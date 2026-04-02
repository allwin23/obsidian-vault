**ATOMICHUB**

**System Design Document**

_Architecture  •  Data Models  •  APIs  •  Infrastructure  •  Sequence Flows_

|   |   |   |
|---|---|---|
|**Modular Monolith**<br><br>Single deploy, domain-separated|**PostgreSQL+Redis+Qdrant**<br><br>Three-layer data stack|**Vercel + Render**<br><br>Frontend + Backend split|

  

# 1. System Overview

|   |
|---|
|**ARCHITECTURE PHILOSOPHY**<br><br>_AtomicHub is a modular monolith — one deployable unit whose code is strictly separated into domain modules. Each domain owns its own routes, services, repositories, and types. No shared state between domains except through well-defined internal service interfaces. This gives the speed of a monolith today and a clear migration path to microservices if scale demands it._|

### High-Level System Topology

|   |
|---|
|┌─────────────────────────────────────────────────────────────────────┐<br><br>│                        CLIENTS                                      │<br><br>│  Next.js Web App    CLI (atomichub)    MCP Server    VS Code Ext    │<br><br>└──────────┬──────────────────┬──────────────┬──────────────┬─────────┘<br><br>           │                  │              │              │<br><br>           ▼                  ▼              ▼              ▼<br><br>┌──────────────────────────────────────────────────────────────────────┐<br><br>│                    API GATEWAY  (Hono on Render)                     │<br><br>│   Auth Middleware → Rate Limiter → Router → Domain Modules           │<br><br>└────┬───────┬──────────┬──────────┬──────────┬──────────┬────────────┘<br><br>     │       │          │          │          │          │<br><br>     ▼       ▼          ▼          ▼          ▼          ▼<br><br>  [Auth]  [VCS]      [DNA]      [AI]       [Social]  [Sync]<br><br>  Module  Module     Module     Module     Module    Module<br><br>     │       │          │          │          │          │<br><br>     └───────┴──────────┴────┬─────┴──────────┴──────────┘<br><br>                             │<br><br>          ┌──────────────────┼──────────────────┐<br><br>          ▼                  ▼                  ▼<br><br>    ┌──────────┐      ┌────────────┐    ┌──────────────┐<br><br>    │PostgreSQL│      │   Redis    │    │   Qdrant     │<br><br>    │  (Neon)  │      │ (Upstash)  │    │(Vector Store)│<br><br>    └──────────┘      └────────────┘    └──────────────┘<br><br>          │<br><br>    ┌─────┴──────┐<br><br>    │     R2     │<br><br>    │ (Cloudflare│<br><br>    │  Storage)  │<br><br>    └────────────┘|

### Deployment Split

|**Service**|**Platform**|**Runtime**|**Reason**|
|---|---|---|---|
|**Next.js Frontend**|Vercel|Edge + Node.js|Native Next.js, global CDN, zero config|
|**Hono API (Monolith)**|Render|Node.js container|Long-running jobs, WebSockets, full control|
|**MCP Server**|Cloudflare Workers|V8 isolates|Edge-deployed, <50ms global latency for agents|
|**BullMQ Workers**|Render (separate service)|Node.js container|Isolated from API, auto-scaling|
|**Verdaccio npm**|Render (separate service)|Node.js container|npm registry for component publishing|
|**Qdrant**|Qdrant Cloud|Managed|Vector search for MCP semantic queries|

  

# 2. Domain Module Breakdown

The monolith is divided into 7 domain modules. Each module is a self-contained folder with its own routes, service layer, repository layer, and types. Modules communicate only through their exported service interfaces — never through shared DB queries.

### Module Directory Structure

|   |
|---|
|src/<br><br>  ├── modules/<br><br>  │   ├── auth/          # Identity, sessions, API tokens, OAuth<br><br>  │   ├── vcs/           # Component repos, commits, branches, PRs, tags<br><br>  │   ├── dna/           # Design DNA, workspace DNA, topology analysis<br><br>  │   ├── ai/            # All AI generation jobs: screenshot, video, a11y, etc<br><br>  │   ├── import/        # Universal URL import, dep resolver, npm publish<br><br>  │   ├── social/        # Feed, stars, forks, comments, kits, profiles<br><br>  │   └── sync/          # Cross-project sync, atomichub.lock, notifications<br><br>  ├── mcp/               # MCP server (deployed separately to CF Workers)<br><br>  ├── shared/<br><br>  │   ├── db/            # Drizzle schema, migrations, db client<br><br>  │   ├── redis/         # Redis client, cache helpers, queue definitions<br><br>  │   ├── storage/       # R2 client wrappers<br><br>  │   ├── queue/         # BullMQ job definitions and processors<br><br>  │   ├── middleware/    # Auth, rate-limit, error handler<br><br>  │   └── types/         # Shared TypeScript types<br><br>  └── index.ts           # Hono app, mounts all module routers|

### Module Responsibility Matrix

|**Module**|**Owns**|**Calls**|**Emits (Queue Jobs)**|
|---|---|---|---|
|**auth**|Users, sessions, API tokens, OAuth accounts|—|—|
|**vcs**|Component repos, commits, branches, PRs, tags, blame|auth, dna|npm.publish, snapshot.create|
|**dna**|Global DNA, workspace DNA, topology scores|auth, vcs|dna.analyze, topology.compute|
|**ai**|AI job dispatch, prompt construction, result storage|auth, vcs, dna|ai.screenshot, ai.video, ai.a11y, ai.coherence|
|**import**|URL fetch, dep resolver, adaptation pipeline|auth, vcs, dna, ai|import.fetch, import.adapt|
|**social**|Feed, stars, forks, comments, kits, profiles|auth, vcs, dna|social.fork, kit.publish|
|**sync**|atomichub.lock, sync notifications, apply|auth, vcs|sync.notify, sync.apply|

  

# 3. Database Schema — PostgreSQL (Neon)

### 3.1 Auth Domain

|   |
|---|
|-- users<br><br>CREATE TABLE users (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  username    TEXT UNIQUE NOT NULL,<br><br>  email       TEXT UNIQUE NOT NULL,<br><br>  avatar_url  TEXT,<br><br>  plan        TEXT DEFAULT 'free',        -- free \| pro \| team<br><br>  created_at  TIMESTAMPTZ DEFAULT now(),<br><br>  updated_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- api_tokens  (scoped tokens for CLI + MCP)<br><br>CREATE TABLE api_tokens (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  name        TEXT NOT NULL,              -- e.g. 'Claude Code MCP'<br><br>  token_hash  TEXT UNIQUE NOT NULL,       -- bcrypt hash, never store plain<br><br>  scope       TEXT[] NOT NULL,            -- ['read','write','admin']<br><br>  workspace_id UUID,                      -- null = all workspaces<br><br>  last_used   TIMESTAMPTZ,<br><br>  expires_at  TIMESTAMPTZ,<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- usage_quotas  (per-user AI usage tracking)<br><br>CREATE TABLE usage_quotas (<br><br>  user_id         UUID PRIMARY KEY REFERENCES users(id) ON DELETE CASCADE,<br><br>  screenshot_used INT DEFAULT 0,<br><br>  video_used      INT DEFAULT 0,<br><br>  a11y_used       INT DEFAULT 0,<br><br>  coherence_used  INT DEFAULT 0,<br><br>  reset_at        TIMESTAMPTZ NOT NULL,   -- monthly reset<br><br>  -- limits enforced by plan tier in app layer<br><br>  updated_at      TIMESTAMPTZ DEFAULT now()<br><br>);|

### 3.2 VCS Domain

|   |
|---|
|-- workspaces<br><br>CREATE TABLE workspaces (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  name        TEXT NOT NULL,<br><br>  description TEXT,<br><br>  is_default  BOOLEAN DEFAULT false,<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- component_repos  (one row = one component repo)<br><br>CREATE TABLE component_repos (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id         UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  workspace_id    UUID REFERENCES workspaces(id),<br><br>  name            TEXT NOT NULL,          -- e.g. 'Button'<br><br>  slug            TEXT NOT NULL,          -- url-safe: 'button'<br><br>  description     TEXT,<br><br>  framework       TEXT NOT NULL,          -- react \| nextjs \| webcomponent<br><br>  is_public       BOOLEAN DEFAULT true,<br><br>  default_branch  TEXT DEFAULT 'main',<br><br>  fork_of_id      UUID REFERENCES component_repos(id),<br><br>  upstream_commit TEXT,                   -- upstream commit SHA at fork time<br><br>  star_count      INT DEFAULT 0,<br><br>  fork_count      INT DEFAULT 0,<br><br>  created_at      TIMESTAMPTZ DEFAULT now(),<br><br>  updated_at      TIMESTAMPTZ DEFAULT now(),<br><br>  UNIQUE(user_id, slug)<br><br>);<br><br>-- branches<br><br>CREATE TABLE branches (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  repo_id         UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  name            TEXT NOT NULL,<br><br>  head_commit_sha TEXT,<br><br>  is_protected    BOOLEAN DEFAULT false,<br><br>  created_at      TIMESTAMPTZ DEFAULT now(),<br><br>  UNIQUE(repo_id, name)<br><br>);<br><br>-- commits<br><br>CREATE TABLE commits (<br><br>  sha             TEXT PRIMARY KEY,       -- SHA256 of content<br><br>  repo_id         UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  branch_id       UUID REFERENCES branches(id),<br><br>  parent_sha      TEXT REFERENCES commits(sha),<br><br>  author_id       UUID REFERENCES users(id),<br><br>  message         TEXT NOT NULL,          -- conventional commit format<br><br>  source_url      TEXT,                   -- R2 key for component source<br><br>  metadata_url    TEXT,                   -- R2 key for atomichub.json<br><br>  ai_assisted     BOOLEAN DEFAULT false,<br><br>  ai_model        TEXT,<br><br>  ai_prompt_ref   TEXT,                   -- R2 key for prompts.json<br><br>  coherence_score INT,<br><br>  a11y_score      INT,<br><br>  human_ratio     NUMERIC(4,2),           -- 0.00–1.00<br><br>  created_at      TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- version_tags  (semver releases)<br><br>CREATE TABLE version_tags (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  repo_id         UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  tag             TEXT NOT NULL,          -- '1.2.0'<br><br>  commit_sha      TEXT REFERENCES commits(sha),<br><br>  channel         TEXT DEFAULT 'stable',  -- stable \| beta \| canary<br><br>  release_notes   TEXT,<br><br>  npm_published   BOOLEAN DEFAULT false,<br><br>  created_at      TIMESTAMPTZ DEFAULT now(),<br><br>  UNIQUE(repo_id, tag)<br><br>);<br><br>-- pull_requests<br><br>CREATE TABLE pull_requests (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  repo_id         UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  author_id       UUID REFERENCES users(id),<br><br>  title           TEXT NOT NULL,<br><br>  description     TEXT,<br><br>  source_branch   TEXT NOT NULL,<br><br>  target_branch   TEXT NOT NULL,<br><br>  status          TEXT DEFAULT 'open',    -- open \| merged \| closed<br><br>  merge_strategy  TEXT,                   -- merge \| squash \| rebase<br><br>  checks_passed   BOOLEAN,<br><br>  coherence_delta INT,                    -- score change if merged<br><br>  created_at      TIMESTAMPTZ DEFAULT now(),<br><br>  updated_at      TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- pr_comments<br><br>CREATE TABLE pr_comments (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  pr_id       UUID REFERENCES pull_requests(id) ON DELETE CASCADE,<br><br>  author_id   UUID REFERENCES users(id),<br><br>  body        TEXT NOT NULL,<br><br>  line_number INT,<br><br>  file_path   TEXT,<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);|

### 3.3 DNA Domain

|   |
|---|
|-- global_dna  (one per user)<br><br>CREATE TABLE global_dna (<br><br>  user_id         UUID PRIMARY KEY REFERENCES users(id) ON DELETE CASCADE,<br><br>  spacing_scale   JSONB,      -- { base: 4, scale: [4,8,12,16,24,32,48,64] }<br><br>  color_system    JSONB,      -- { primary, secondary, semantic, dark_mode }<br><br>  typography      JSONB,      -- { heading_font, body_font, scale, weights }<br><br>  border_system   JSONB,      -- { radius_scale, border_widths, shadow_levels }<br><br>  animation       JSONB,      -- { easing, duration_range, library }<br><br>  component_patterns JSONB,   -- { composition_style, slot_usage, complexity }<br><br>  naming          JSONB,      -- { props: camelCase, files: kebab-case }<br><br>  framework_conventions JSONB,<br><br>  cold_start_complete BOOLEAN DEFAULT false,<br><br>  source          TEXT,       -- 'github' \| 'upload' \| 'wizard' \| 'progressive'<br><br>  confidence      INT,        -- 0-100, how confident the DNA is<br><br>  updated_at      TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- workspace_dna  (per-project override, merged with global at query time)<br><br>CREATE TABLE workspace_dna (<br><br>  workspace_id    UUID PRIMARY KEY REFERENCES workspaces(id) ON DELETE CASCADE,<br><br>  overrides       JSONB NOT NULL,  -- only fields that differ from global DNA<br><br>  dark_mode       TEXT,            -- 'required' \| 'optional' \| 'none'<br><br>  contracts       TEXT[],          -- active contract IDs<br><br>  updated_at      TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- topology_reports  (AI-generated analysis of component library)<br><br>CREATE TABLE topology_reports (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id         UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  workspace_id    UUID REFERENCES workspaces(id),<br><br>  consistency_score INT,<br><br>  token_coverage    INT,<br><br>  a11y_baseline     INT,<br><br>  dark_mode_coverage INT,<br><br>  suggestions     JSONB,   -- array of { type, severity, message, affected_repos }<br><br>  created_at      TIMESTAMPTZ DEFAULT now()<br><br>);|

### 3.4 AI Domain

|   |
|---|
|-- ai_jobs  (all async AI generation tasks)<br><br>CREATE TABLE ai_jobs (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  type        TEXT NOT NULL,  -- screenshot\|video\|a11y\|coherence\|responsive\|darkmode\|figma\|compose<br><br>  status      TEXT DEFAULT 'queued',  -- queued\|processing\|done\|failed<br><br>  input_ref   TEXT,           -- R2 key for input (screenshot/video file)<br><br>  output_ref  TEXT,           -- R2 key for generated component source<br><br>  model_used  TEXT,           -- claude-sonnet-4\|gemini-1.5-pro\|etc<br><br>  prompt_ref  TEXT,           -- R2 key for full prompt sent<br><br>  error       TEXT,<br><br>  repo_id     UUID REFERENCES component_repos(id),<br><br>  commit_sha  TEXT,           -- set after user approves and commits<br><br>  duration_ms INT,<br><br>  created_at  TIMESTAMPTZ DEFAULT now(),<br><br>  updated_at  TIMESTAMPTZ DEFAULT now()<br><br>);|

### 3.5 Social Domain

|   |
|---|
|-- stars<br><br>CREATE TABLE stars (<br><br>  user_id   UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  repo_id   UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  created_at TIMESTAMPTZ DEFAULT now(),<br><br>  PRIMARY KEY (user_id, repo_id)<br><br>);<br><br>-- comments  (on component repos in the social feed)<br><br>CREATE TABLE comments (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  repo_id     UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  parent_id   UUID REFERENCES comments(id),   -- for threaded replies<br><br>  body        TEXT NOT NULL,<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- kits  (curated component collections)<br><br>CREATE TABLE kits (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  name        TEXT NOT NULL,<br><br>  description TEXT,<br><br>  is_public   BOOLEAN DEFAULT true,<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- kit_components<br><br>CREATE TABLE kit_components (<br><br>  kit_id    UUID REFERENCES kits(id) ON DELETE CASCADE,<br><br>  repo_id   UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  order_idx INT DEFAULT 0,<br><br>  PRIMARY KEY (kit_id, repo_id)<br><br>);|

### 3.6 Sync Domain

|   |
|---|
|-- project_registrations  (registered projects using atomichub init)<br><br>CREATE TABLE project_registrations (<br><br>  id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  user_id     UUID REFERENCES users(id) ON DELETE CASCADE,<br><br>  project_name TEXT NOT NULL,<br><br>  lock_ref    TEXT,           -- R2 key for atomichub.lock file<br><br>  created_at  TIMESTAMPTZ DEFAULT now()<br><br>);<br><br>-- sync_subscriptions  (which project uses which component version)<br><br>CREATE TABLE sync_subscriptions (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  project_id      UUID REFERENCES project_registrations(id) ON DELETE CASCADE,<br><br>  repo_id         UUID REFERENCES component_repos(id) ON DELETE CASCADE,<br><br>  pinned_version  TEXT,        -- null = follow latest stable<br><br>  current_tag     TEXT NOT NULL,<br><br>  channel         TEXT DEFAULT 'stable',<br><br>  UNIQUE(project_id, repo_id)<br><br>);<br><br>-- sync_notifications<br><br>CREATE TABLE sync_notifications (<br><br>  id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),<br><br>  project_id      UUID REFERENCES project_registrations(id) ON DELETE CASCADE,<br><br>  repo_id         UUID REFERENCES component_repos(id),<br><br>  from_tag        TEXT NOT NULL,<br><br>  to_tag          TEXT NOT NULL,<br><br>  change_type     TEXT NOT NULL,  -- patch \| minor \| major<br><br>  status          TEXT DEFAULT 'pending',  -- pending \| approved \| skipped<br><br>  created_at      TIMESTAMPTZ DEFAULT now()<br><br>);|

### 3.7 Key Indexes

|   |
|---|
|-- VCS performance<br><br>CREATE INDEX idx_commits_repo_branch ON commits(repo_id, branch_id);<br><br>CREATE INDEX idx_commits_created ON commits(created_at DESC);<br><br>CREATE INDEX idx_repos_user ON component_repos(user_id);<br><br>CREATE INDEX idx_repos_public ON component_repos(is_public) WHERE is_public = true;<br><br>-- Social feed performance<br><br>CREATE INDEX idx_repos_stars ON component_repos(star_count DESC);<br><br>CREATE INDEX idx_repos_updated ON component_repos(updated_at DESC);<br><br>CREATE INDEX idx_stars_repo ON stars(repo_id);<br><br>-- Sync performance<br><br>CREATE INDEX idx_sync_subs_project ON sync_subscriptions(project_id);<br><br>CREATE INDEX idx_sync_notif_status ON sync_notifications(status) WHERE status = 'pending';<br><br>-- AI jobs<br><br>CREATE INDEX idx_ai_jobs_user_status ON ai_jobs(user_id, status);|

  

# 4. Redis Caching Strategy (Upstash)

|   |
|---|
|**REDIS ROLE**<br><br>_Redis serves three distinct purposes in AtomicHub: (1) response caching for hot read paths, (2) session/token validation cache to avoid DB hits on every request, and (3) BullMQ job queue broker for all async AI and background jobs. All Redis keys have explicit TTLs — nothing cached forever._|

### 4.1 Cache Key Schema & TTLs

|**Cache Key Pattern**|**Value**|**TTL**|
|---|---|---|
|**dna:global:{user_id}**|Serialized global DNA JSON|1 hour — invalidate on DNA update|
|**dna:workspace:{workspace_id}**|Serialized workspace DNA JSON|1 hour — invalidate on DNA update|
|**dna:effective:{user_id}:{workspace_id}**|Merged effective DNA (global + workspace)|30 min — invalidate on either update|
|**repo:meta:{repo_id}**|Component repo metadata + latest version|5 min — invalidate on commit/publish|
|**repo:props:{repo_id}:{version}**|Prop schema JSON for Prop Playground|24 hours — immutable per version|
|**feed:public:{page}:{filters_hash}**|Paginated public feed results|2 min — balance freshness vs DB load|
|**token:{token_hash}**|User ID + scope (token validation fast path)|15 min — invalidate on token revoke|
|**mcp:search:{query_hash}:{user_id}**|MCP semantic search results|10 min — balance freshness vs Qdrant cost|
|**mcp:get:{repo_id}:{version}**|Full MCP component payload|10 min — invalidate on new version|
|**sync:pending:{user_id}**|Count of pending sync notifications|5 min — for dashboard badge|
|**quota:{user_id}:{month}**|Current AI usage counts per type|Until end of month, reset on new month|
|**topology:{user_id}**|Latest topology report summary|1 hour — invalidate on topology.compute job|

### 4.2 Cache Invalidation Strategy

•        Write-through invalidation: every service method that mutates a record also deletes relevant cache keys

•        Use Redis SCAN + DEL pattern for wildcard invalidation (e.g. all dna:* keys for a user on DNA update)

•        Version-keyed cache for immutable data (prop schemas, commit snapshots) — never needs invalidation

•        Feed cache uses short TTL (2 min) instead of active invalidation — acceptable staleness for social feed

### 4.3 Queue Architecture (BullMQ)

|**Queue Name**|**Jobs**|**Workers / Concurrency**|
|---|---|---|
|**ai:generation**|screenshot, video, a11y-fix, darkmode, responsive, figma, compose|2 workers, concurrency 3 each|
|**ai:coherence**|coherence check runs (fast, lightweight)|1 worker, concurrency 10|
|**vcs:publish**|npm publish to Verdaccio on new version tag|1 worker, concurrency 5|
|**dna:analysis**|github repo analysis, codebase upload analysis|1 worker, concurrency 2|
|**dna:topology**|topology report generation (heavy, weekly)|1 worker, concurrency 1|
|**sync:notify**|fan-out sync notifications to registered projects|1 worker, concurrency 20|
|**import:fetch**|URL import fetch + dep resolution|2 workers, concurrency 5|
|**social:index**|index new public component into Qdrant|1 worker, concurrency 10|

### 4.4 MCP Latency SLA — How We Hit <200ms

|**Step**|**Target**|**Mechanism**|
|---|---|---|
|**Token validation**|<5ms|Redis cache: token:{hash} → user_id + scope|
|**forge.get (cached)**|<20ms|Redis: mcp:get:{repo_id}:{version} → full payload|
|**forge.get (miss)**|<80ms|Neon PostgreSQL read + R2 source fetch + Redis set|
|**forge.search (cached)**|<30ms|Redis: mcp:search:{hash} → result set|
|**forge.search (miss)**|<180ms|Qdrant vector search + PostgreSQL metadata join + Redis set|
|**forge.getDNA (cached)**|<10ms|Redis: dna:effective:{uid}:{wid} → DNA JSON|
|**forge.getDNA (miss)**|<60ms|PostgreSQL read + merge computation + Redis set|

  

# 5. Vector Store — Qdrant

|   |
|---|
|**PURPOSE**<br><br>_Qdrant powers semantic search for the MCP tool and the Explore feed. When a developer asks Claude Code to 'find me a gallery component with lazy loading', Qdrant returns the most semantically similar components from their library — using embeddings, not keyword matching. This is what makes forge.search feel intelligent rather than just a text search._|

### 5.1 Collections

|**Collection**|**Embedding Source**|**Payload Fields**|
|---|---|---|
|**components_public**|name + description + tags + prop names|repo_id, user_id, framework, scores, star_count|
|**components_private_{user_id}**|name + description + tags + code summary|repo_id, workspace_id, version, updated_at|
|**dna_profiles**|DNA JSON serialized to text|user_id, confidence, source|

### 5.2 Embedding Pipeline

•        Model: text-embedding-3-small (OpenAI) — 1536 dimensions, cheap, fast

•        Generated at: component publish, fork, URL import, DNA update

•        Queued via social:index BullMQ job — never blocks the publish API response

•        Embedding input = concat(name, description, prop_names, code_summary_200_chars)

•        Code summary generated by Claude haiku (cheap) before embedding — not the full source

### 5.3 Search Flow

|   |
|---|
|MCP forge.search('gallery with lazy loading')<br><br>  │<br><br>  ├─ 1. Check Redis: mcp:search:{hash}:{user_id}  →  cache hit? return immediately<br><br>  │<br><br>  ├─ 2. Generate query embedding via text-embedding-3-small<br><br>  │<br><br>  ├─ 3. Qdrant search:<br><br>  │      collection: components_private_{user_id}  (search own library first)<br><br>  │      top_k: 5, score_threshold: 0.75<br><br>  │      filter: { framework: ['react','nextjs','webcomponent'] }<br><br>  │<br><br>  ├─ 4. If < 3 results: also search components_public<br><br>  │      filter: { user_id: NOT current_user }  (exclude already-owned)<br><br>  │<br><br>  ├─ 5. Hydrate results: fetch repo metadata from PostgreSQL<br><br>  │<br><br>  ├─ 6. Fetch component source from R2 for top result<br><br>  │<br><br>  ├─ 7. Cache in Redis: mcp:search:{hash}:{user_id}  TTL 10min<br><br>  │<br><br>  └─ 8. Return MCP payload with DNA context injected|

  

# 6. Object Storage — Cloudflare R2

|   |
|---|
|**WHY R2**<br><br>_R2 has zero egress fees. Component source files, screenshots, videos, and replay data are fetched constantly — by CLI, by MCP, by the Prop Playground, by the visual diff engine. With S3, egress would be a meaningful cost at scale. With R2, it is zero._|

### R2 Bucket Structure

|   |
|---|
|atomichub-components/          # Component source files<br><br>  {user_id}/{repo_id}/{sha}/<br><br>    component.tsx              # Main source<br><br>    component.ce.ts            # Web Component wrapper<br><br>    atomichub.json             # Metadata<br><br>    CHANGELOG.md<br><br>atomichub-ai/                  # AI job inputs and outputs<br><br>  jobs/{job_id}/<br><br>    input.{png\|mp4\|json}       # Screenshot / video / figma input<br><br>    output.tsx                 # Generated component<br><br>    prompt.json                # Full prompt sent to model<br><br>atomichub-replay/              # Component creation history<br><br>  {repo_id}/<br><br>    prompts.json               # All prompts in chronological order<br><br>    screenshots/{sha}.png      # Reference screenshots<br><br>    snapshots/{version}.tsx    # Version snapshots<br><br>atomichub-dna/                 # DNA analysis artifacts<br><br>  {user_id}/<br><br>    analysis.json              # Full DNA analysis result<br><br>    topology_{date}.json       # Topology report|

### R2 Access Patterns

|**Consumer**|**Access Pattern**|**Auth**|
|---|---|---|
|**API (Render)**|Direct R2 SDK reads/writes|Service account credentials|
|**MCP (CF Workers)**|Presigned URL fetch for component source|Presigned URL generated by API, short TTL|
|**CLI**|Presigned upload URLs for push, presigned download for add|API token → server generates presigned URL|
|**Prop Playground**|Source fetched by API, served to sandpack|Public read for public repos, API for private|
|**Visual Diff**|Two source files fetched for comparison|Same as Prop Playground|

  

# 7. AI Pipeline Architecture

### 7.1 Screenshot → Component Flow

|   |
|---|
|POST /api/ai/screenshot<br><br>  │<br><br>  ├─ 1. Validate: user quota check (Redis: quota:{uid}:screenshot)<br><br>  │<br><br>  ├─ 2. Upload screenshot to R2: atomichub-ai/jobs/{job_id}/input.png<br><br>  │<br><br>  ├─ 3. Insert ai_jobs row: status='queued'<br><br>  │<br><br>  ├─ 4. Enqueue BullMQ job: ai:generation  { job_id, type:'screenshot' }<br><br>  │<br><br>  └─ 5. Return 202 Accepted: { job_id }  ← client polls /api/ai/jobs/{job_id}<br><br>BullMQ Worker: ai:generation (screenshot)<br><br>  │<br><br>  ├─ 1. Fetch effective DNA from Redis (or PostgreSQL)<br><br>  │<br><br>  ├─ 2. Fetch workspace contracts from PostgreSQL<br><br>  │<br><br>  ├─ 3. Build system prompt:<br><br>  │      - DNA context (spacing, colors, typography, naming, animation)<br><br>  │      - Active contracts (must-haves)<br><br>  │      - Existing component list (from Qdrant user library)<br><br>  │      - Framework target (React + Tailwind)<br><br>  │<br><br>  ├─ 4. Call Claude claude-sonnet-4 vision API (user's Anthropic key)<br><br>  │      Input: screenshot + system prompt<br><br>  │      Output: component.tsx source<br><br>  │<br><br>  ├─ 5. Run coherence check (Claude haiku): score + violations<br><br>  │<br><br>  ├─ 6. Store output to R2: atomichub-ai/jobs/{job_id}/output.tsx<br><br>  │<br><br>  ├─ 7. Store prompt to R2: atomichub-ai/jobs/{job_id}/prompt.json<br><br>  │<br><br>  ├─ 8. Update ai_jobs: status='done', output_ref, coherence_score<br><br>  │<br><br>  ├─ 9. Increment usage quota: Redis INCR quota:{uid}:screenshot<br><br>  │<br><br>  └─ 10. Notify client via WebSocket or polling response|

### 7.2 Video → Animation Flow (Gemini)

|   |
|---|
|POST /api/ai/video<br><br>  │<br><br>  ├─ Validate quota, upload to R2, enqueue ai:generation job<br><br>  └─ Same 202 pattern as screenshot<br><br>BullMQ Worker: ai:generation (video)<br><br>  │<br><br>  ├─ 1. Fetch video from R2<br><br>  │<br><br>  ├─ 2. Build prompt: extract motion timeline, easing, element transforms<br><br>  │      Include DNA animation personality: easing preference, duration range<br><br>  │<br><br>  ├─ 3. Call Gemini 1.5 Pro (user's Google AI key)<br><br>  │      Input: video file + motion extraction prompt<br><br>  │      Output: Framer Motion component OR CSS @keyframes<br><br>  │<br><br>  ├─ 4. Post-process: inject prefers-reduced-motion wrapper<br><br>  │<br><br>  ├─ 5. Adapt easing values to DNA animation personality<br><br>  │<br><br>  └─ 6. Store + notify (same pattern as screenshot)|

### 7.3 DNA Cold Start — 5 Question Wizard

|   |
|---|
|POST /api/dna/cold-start  { answers: QuizAnswer[] }<br><br>Q1: 'How would you describe your spacing style?'<br><br>    → A) Tight and dense  B) Comfortable (8px grid)  C) Airy and spacious<br><br>    Maps to: spacing_scale base unit (4px / 8px / 12px)<br><br>Q2: 'Pick the border radius style that fits you:'<br><br>    → A) Sharp (0px)  B) Subtle (4-6px)  C) Rounded (8-12px)  D) Pill (9999px)<br><br>    Maps to: border_system.radius_scale preset<br><br>Q3: 'How do you prefer animations?'<br><br>    → A) None — I prefer static  B) Subtle and functional  C) Expressive and playful<br><br>    Maps to: animation.personality preset<br><br>Q4: 'Upload your brand colors or pick a palette:'<br><br>    → Color picker UI or hex input for primary + secondary<br><br>    Maps to: color_system.primary, color_system.secondary<br><br>Q5: 'Pick your typography stack:'<br><br>    → Shows 6 font pair previews (Inter/Sora, Geist/Cal Sans, etc.)<br><br>    Maps to: typography.heading_font, typography.body_font<br><br>→ Server synthesizes full DNA JSON from answer mapping + reasonable defaults<br><br>→ Sets global_dna.cold_start_complete = true, confidence = 40<br><br>→ DNA refines automatically as user publishes components (confidence rises)|

### 7.4 Fork DNA Adaptation

|   |
|---|
|POST /api/social/fork  { repo_id, target_workspace_id }<br><br>  │<br><br>  ├─ 1. Copy repo metadata → new component_repo row<br><br>  │<br><br>  ├─ 2. Fetch source from R2 (original component)<br><br>  │<br><br>  ├─ 3. Fetch effective DNA of FORKER (not original author)<br><br>  │<br><br>  ├─ 4. Enqueue ai:generation job: type='fork_adapt'<br><br>  │<br><br>  └─ 5. Return 202 with repo stub (accessible immediately, adapted version pending)<br><br>BullMQ Worker: fork_adapt<br><br>  │<br><br>  ├─ 1. Diff original DNA vs forker DNA: find deltas<br><br>  │      e.g. primary color changed, border radius changed, font changed<br><br>  │<br><br>  ├─ 2. Build targeted adaptation prompt:<br><br>  │      'Adapt this component. Change primary from #6366F1 to #8B5CF6.<br><br>  │       Change border-radius from 4px to 8px. Keep structure identical.'<br><br>  │<br><br>  ├─ 3. Call Claude haiku (cheap — targeted, not generative)<br><br>  │<br><br>  ├─ 4. Run coherence check against forker's DNA<br><br>  │<br><br>  ├─ 5. If coherence < 70: flag as 'Needs Review' — don't auto-commit<br><br>  │      If coherence >= 70: auto-commit to forker's repo<br><br>  │<br><br>  └─ 6. Notify forker: 'Fork ready — review adaptation before publishing'|

  

# 8. MCP Server Architecture

|   |
|---|
|**DEPLOYMENT**<br><br>_The MCP server is deployed as a Cloudflare Worker — separate from the main Render API. This gives edge-global latency (<50ms anywhere), infinite horizontal scaling at zero config, and complete isolation from API load. The Worker is stateless — all data comes from Redis (cache) or the Render API (cache miss fallback)._|

### 8.1 MCP Request Flow

|   |
|---|
|Claude Code → MCP Server (CF Worker)<br><br>  │<br><br>  ├─ 1. Parse MCP tool call: { tool: 'atomichub.search', params: { query } }<br><br>  │<br><br>  ├─ 2. Validate API token:<br><br>  │      Check Redis: token:{hash} → { user_id, scope, workspace_id }<br><br>  │      Cache miss: POST Render API /internal/tokens/validate (adds to cache)<br><br>  │<br><br>  ├─ 3. Check scope: read tools require 'read', push requires 'write'<br><br>  │<br><br>  ├─ 4. Route to tool handler<br><br>  │<br><br>  └─ 5. Return MCP-formatted response with DNA context injected<br><br>Tool handler: atomichub.search<br><br>  ├─ Check Redis cache (mcp:search:{hash}:{user_id})<br><br>  ├─ Miss: POST Render API /internal/mcp/search { query, user_id, workspace_id }<br><br>  │        API runs Qdrant search + PostgreSQL hydration<br><br>  ├─ Cache result in Redis (10 min TTL)<br><br>  └─ Inject DNA context from Redis dna:effective:{uid}:{wid}|

### 8.2 MCP Internal API (Render → Worker bridge)

|**Endpoint**|**Called By**|**Returns**|
|---|---|---|
|**POST /internal/tokens/validate**|CF Worker on token cache miss|user_id, scope, workspace_id|
|**POST /internal/mcp/search**|CF Worker on search cache miss|Ranked component list with metadata|
|**GET /internal/mcp/component/{id}**|CF Worker on get cache miss|Full source + props + metadata|
|**GET /internal/mcp/dna/{uid}/{wid}**|CF Worker on DNA cache miss|Effective DNA JSON|
|**POST /internal/mcp/push**|CF Worker on write tool call|Created commit SHA|
|**GET /internal/mcp/contracts/{wid}**|CF Worker on contracts cache miss|Active contract list|

  

# 9. VCS Engine Design

|   |
|---|
|**DESIGN DECISION**<br><br>_AtomicHub does not use libgit2 or shell out to git. It implements a purpose-built VCS on top of PostgreSQL + R2. This gives full control over the data model, allows UI-first features like visual diffing and AI blame annotation, and avoids the complexity of managing bare git repos at scale. The mental model is git-identical from the user's perspective._|

### 9.1 Commit Hashing

|   |
|---|
|function computeSHA(content: string, parentSHA: string \| null, metadata: object): string {<br><br>  // SHA256 of: content + parentSHA + author_id + timestamp + metadata<br><br>  const input = JSON.stringify({ content, parentSHA, metadata });<br><br>  return crypto.createHash('sha256').update(input).digest('hex');<br><br>}<br><br>// Each commit is content-addressed — identical content = identical SHA<br><br>// Parent chain forms the commit DAG (same as git's object model)|

### 9.2 Visual Diff Engine

|   |
|---|
|GET /api/components/{id}/diff?from={sha_or_tag}&to={sha_or_tag}<br><br>  │<br><br>  ├─ 1. Fetch source A and source B from R2<br><br>  │<br><br>  ├─ 2. Code diff: unified diff algorithm (same as git diff -U3)<br><br>  │<br><br>  ├─ 3. Prop diff: parse TypeScript interfaces from both versions,<br><br>  │      compute added/removed/renamed/type-changed props<br><br>  │<br><br>  ├─ 4. Visual diff: both sources sent to Prop Playground renderer,<br><br>  │      screenshots captured via headless browser (Playwright on Render),<br><br>  │      pixel comparison via pixelmatch → diff percentage + overlay image<br><br>  │<br><br>  ├─ 5. Score diff: coherence_score A vs B, a11y_score A vs B<br><br>  │<br><br>  └─ 6. Return: { code_diff, prop_diff, visual_diff_url, score_delta }|

### 9.3 Blame Construction

|   |
|---|
|GET /api/components/{id}/blame?branch=main<br><br>  │<br><br>  ├─ 1. Fetch current source from R2<br><br>  │<br><br>  ├─ 2. Walk commit history from HEAD → initial commit<br><br>  │<br><br>  ├─ 3. For each commit: diff against parent, attribute changed lines<br><br>  │<br><br>  ├─ 4. Build blame map: line_number → { commit_sha, author, timestamp,<br><br>  │                                       ai_assisted, ai_model }<br><br>  │<br><br>  └─ 5. Return blame map + annotated source|

  

# 10. Verdaccio npm Registry

|   |
|---|
|**ROLE**<br><br>_Every AtomicHub user gets a scoped npm package: @username/atomichub-components. When a component is tagged with a semver release, a BullMQ job publishes the updated package to the Verdaccio instance running on Render. CLI users can install via npm install @username/atomichub-components or use the shadcn-style atomichub add command (which copies source — no runtime dependency)._|

### Publish Flow

|   |
|---|
|POST /api/components/{id}/versions  { tag: '1.2.0', channel: 'stable' }<br><br>  │<br><br>  ├─ 1. Insert version_tags row<br><br>  │<br><br>  ├─ 2. Enqueue vcs:publish job: { repo_id, tag, user_id }<br><br>  │<br><br>  └─ 3. Return 201 Created<br><br>BullMQ Worker: vcs:publish<br><br>  │<br><br>  ├─ 1. Fetch component source from R2<br><br>  │<br><br>  ├─ 2. Generate package.json:<br><br>  │      { name: '@{username}/atomichub-components',<br><br>  │        version: '{tag}',<br><br>  │        exports: { './{ComponentName}': './{ComponentName}.tsx' } }<br><br>  │<br><br>  ├─ 3. Build tarball (tar + gzip)<br><br>  │<br><br>  ├─ 4. PUT to Verdaccio registry API<br><br>  │<br><br>  ├─ 5. Update version_tags.npm_published = true<br><br>  │<br><br>  └─ 6. Invalidate Redis: repo:meta:{repo_id}|

### Verdaccio Config

|   |
|---|
|# config.yaml (Render service)<br><br>storage: /verdaccio/storage<br><br>auth:<br><br>  htpasswd:<br><br>    file: /verdaccio/htpasswd<br><br>    max_users: -1<br><br>uplinks:<br><br>  npmjs:<br><br>    url: https://registry.npmjs.org/<br><br>packages:<br><br>  '@*/atomichub-components':<br><br>    access: '$all'          # public read<br><br>    publish: '$authenticated'  # only AtomicHub service account writes<br><br>    proxy: npmjs<br><br>  '**':<br><br>    access: '$all'<br><br>    proxy: npmjs           # proxy all other packages to npmjs|

  

# 11. Auth & Usage Quota System

### 11.1 Authentication Layers

|**Consumer**|**Auth Method**|**How It Works**|
|---|---|---|
|**Web app users**|Clerk OAuth/Email|Clerk session token → Clerk SDK validates → user_id extracted|
|**CLI users**|API Token|atomichub login → browser OAuth → token generated + stored in ~/.atomichub/config|
|**MCP clients**|API Token|Token in env var ATOMICHUB_TOKEN → CF Worker validates → scoped access|
|**Internal services**|Service key|Render-to-Render internal network + shared secret header|

### 11.2 API Token Flow

|   |
|---|
|1. User visits Dashboard → Settings → API Tokens<br><br>2. Names token ('Claude Code MCP'), selects scope, optionally scopes to workspace<br><br>3. Server: generates random 32-byte token, stores bcrypt(token) in api_tokens table<br><br>4. Returns plain token ONCE — user copies it, never shown again<br><br>5. On every MCP/CLI request:<br><br>   a. Extract token from Authorization: Bearer {token}<br><br>   b. Check Redis: token:{sha256(token)} → cached user_id + scope<br><br>   c. Cache miss: bcrypt compare against api_tokens table, cache result 15min<br><br>   d. Check scope: read/write/admin as required by route<br><br>   e. Update api_tokens.last_used (async, non-blocking)|

### 11.3 Per-User AI Quota System

|   |
|---|
|// Quota limits per plan tier (enforced in app layer, not DB)<br><br>const QUOTA_LIMITS = {<br><br>  free: {<br><br>    screenshot: 10,   // per month<br><br>    video: 3,<br><br>    a11y: 20,<br><br>    coherence: 100,   // runs on every publish, so higher limit<br><br>    responsive: 10,<br><br>    darkmode: 10,<br><br>    figma: 5,<br><br>  },<br><br>  pro: {            // all limits 10x free (future monetization)<br><br>    screenshot: 100,<br><br>    // ...<br><br>  }<br><br>};<br><br>// Quota check before every AI job:<br><br>async function checkQuota(userId: string, type: AIJobType): Promise<void> {<br><br>  const key = `quota:${userId}:${currentMonth()}`;<br><br>  const used = await redis.hget(key, type) ?? 0;<br><br>  const limit = QUOTA_LIMITS[userPlan][type];<br><br>  if (Number(used) >= limit) throw new QuotaExceededError(type, limit);<br><br>}<br><br>// After job completes:<br><br>await redis.hincrby(`quota:${userId}:${currentMonth()}`, type, 1);<br><br>// Redis key auto-expires at month end (TTL set on first write)|

  

# 12. Key Sequence Flows

### 12.1 CLI: atomichub add Button

|   |
|---|
|Developer terminal → CLI<br><br>  │<br><br>  ├─ 1. Read ~/.atomichub/config for API token + active workspace<br><br>  │<br><br>  ├─ 2. GET /api/components?name=Button&workspace={id}<br><br>  │      Response: { repo_id, latest_tag, source_url (presigned R2) }<br><br>  │<br><br>  ├─ 3. Fetch source from R2 presigned URL<br><br>  │<br><br>  ├─ 4. Read project package.json, resolve missing deps<br><br>  │<br><br>  ├─ 5. npm install {missing_deps} in current project<br><br>  │<br><br>  ├─ 6. Write component.tsx to ./components/Button/<br><br>  │<br><br>  ├─ 7. Append to atomichub.lock:<br><br>  │      { Button: { repo_id, tag: '1.2.0', workspace_id } }<br><br>  │<br><br>  └─ 8. POST /api/sync/register-usage { project_id, repo_id, tag }|

### 12.2 MCP: Claude Code Builds a Feature

|   |
|---|
|Developer: 'Build me a user profile card using my component library'<br><br>  │<br><br>  ├─ Claude Code calls atomichub.getDNA({ workspace_id })<br><br>  │      → CF Worker → Redis hit → DNA JSON returned<br><br>  │      Claude now knows: violet accent, 8px grid, Inter font, no hardcoded colors<br><br>  │<br><br>  ├─ Claude Code calls atomichub.listWorkspace({ workspace_id })<br><br>  │      → Returns: ['Avatar', 'Card', 'Badge', 'Button', 'Text']<br><br>  │<br><br>  ├─ Claude Code calls atomichub.search({ query: 'profile card layout' })<br><br>  │      → Qdrant semantic search → 'Card' component returned as top match<br><br>  │<br><br>  ├─ Claude Code calls atomichub.get({ name: 'Card', version: 'latest' })<br><br>  │      → Full Card source returned<br><br>  │<br><br>  ├─ Claude generates ProfileCard using existing Card + Avatar + Badge<br><br>  │      (Composition — no new components generated unnecessarily)<br><br>  │<br><br>  ├─ Claude Code calls atomichub.checkCoherence({ source: generatedCode })<br><br>  │      → Score: 91 — 'Uses correct spacing, colors match DNA, accessible'<br><br>  │<br><br>  ├─ Claude Code calls atomichub.push({ name: 'ProfileCard', source, message: 'feat: profile card' })<br><br>  │      → CF Worker → POST /internal/mcp/push → commit created in PostgreSQL<br><br>  │      → source stored in R2 → Qdrant index queued<br><br>  │<br><br>  └─ Developer has a new ProfileCard in their AtomicHub library automatically|

### 12.3 Cross-Project Sync Flow

|   |
|---|
|Developer updates Button v1.1.0 → v1.2.0 (minor: adds loading state)<br><br>  │<br><br>  ├─ 1. New version_tag inserted<br><br>  │<br><br>  ├─ 2. vcs:publish BullMQ job fires → npm published to Verdaccio<br><br>  │<br><br>  ├─ 3. sync:notify job fires:<br><br>  │      Query sync_subscriptions WHERE repo_id = Button.id AND channel = 'stable'<br><br>  │      Found: Project-A (v1.1.0), Project-B (v1.1.0), Project-C (pinned=v1.0.0)<br><br>  │<br><br>  ├─ 4. Insert sync_notifications for Project-A and Project-B (not C — pinned)<br><br>  │      change_type = 'minor' (1.x.0) → requires review<br><br>  │<br><br>  ├─ 5. Developer sees badge in dashboard: '2 pending syncs'<br><br>  │<br><br>  ├─ 6. Developer opens sync dashboard:<br><br>  │      Shows visual diff: Button v1.1.0 rendered vs v1.2.0 rendered<br><br>  │      Shows code diff, prop diff (new 'loading' prop added)<br><br>  │<br><br>  ├─ 7. Developer approves for Project-A, skips Project-B<br><br>  │<br><br>  └─ 8. atomichub sync (in Project-A terminal):<br><br>         Fetches approved updates, writes new Button source, updates atomichub.lock|

  

# 13. Prop Playground Architecture

|   |
|---|
|**TECH CHOICE**<br><br>_Sandpack (CodeSandbox's in-browser bundler) runs entirely in the browser — no server-side rendering needed. The component source is fetched from R2, injected into a sandpack template, and rendered live. The controls panel is driven by the component.props.json schema auto-generated by the TypeScript compiler API at publish time._|

### Prop Schema Generation Pipeline

|   |
|---|
|// Runs as part of vcs:publish BullMQ job<br><br>import { Project, ts } from 'ts-morph';<br><br>function extractPropSchema(source: string): PropSchema[] {<br><br>  const project = new Project({ useInMemoryFileSystem: true });<br><br>  const file = project.createSourceFile('component.tsx', source);<br><br>  // Find the Props interface or type<br><br>  const propsInterface = file.getInterface('Props') ?? file.getTypeAlias('Props');<br><br>  return propsInterface.getProperties().map(prop => ({<br><br>    name: prop.getName(),<br><br>    type: inferControlType(prop.getType()),  // string→text, boolean→toggle, union→select<br><br>    values: extractUnionValues(prop.getType()),<br><br>    default: extractJSDocDefault(prop),<br><br>    required: !prop.hasQuestionToken(),<br><br>  }));<br><br>}|

### Sandpack Integration

|   |
|---|
|// Frontend: ComponentPlayground.tsx<br><br>import { Sandpack } from '@codesandbox/sandpack-react';<br><br>// Files injected into sandpack at load time:<br><br>const files = {<br><br>  '/component.tsx': componentSource,           // from R2<br><br>  '/App.tsx': generateAppWrapper(propValues),  // generated from prop controls state<br><br>  '/index.tsx': SANDPACK_ENTRY,<br><br>};<br><br>// When any control changes:<br><br>// 1. Update propValues state<br><br>// 2. Regenerate /App.tsx with new prop values<br><br>// 3. Sandpack hot-reloads — preview updates in <100ms|

  

# 14. Universal URL Import Pipeline

|   |
|---|
|POST /api/import  { url: 'https://reactbits.dev/components/animated-content' }<br><br>  │<br><br>  ├─ 1. Validate URL, check quota<br><br>  │<br><br>  ├─ 2. Enqueue import:fetch job → return 202<br><br>  │<br><br>BullMQ Worker: import:fetch<br><br>  │<br><br>  ├─ 1. HTTP fetch URL → parse HTML<br><br>  │<br><br>  ├─ 2. Source extraction strategy (tried in order):<br><br>  │      a. Look for <code> blocks with .tsx/.jsx content<br><br>  │      b. Look for CodeSandbox/StackBlitz embed URLs → fetch their file API<br><br>  │      c. Look for GitHub raw URLs → direct fetch<br><br>  │      d. Headless Playwright fetch (last resort for JS-rendered pages)<br><br>  │<br><br>  ├─ 3. Parse extracted source → identify all imports<br><br>  │<br><br>  ├─ 4. Dependency resolution:<br><br>  │      For each import: check if it's in npm registry<br><br>  │      Build manifest: { peerDeps: [], devDeps: [], internal: [] }<br><br>  │<br><br>  ├─ 5. Enqueue ai:generation job: type='fork_adapt' against user's DNA<br><br>  │<br><br>  ├─ 6. Store adapted source to R2<br><br>  │<br><br>  ├─ 7. Create commit in user's component repo<br><br>  │<br><br>  └─ 8. Return: { repo_id, dep_manifest, coherence_score, adaptation_notes }|

  

# 15. Infrastructure & Environment Configuration

### 15.1 Service Inventory

|**Service**|**Platform**|**Plan**|**Config Notes**|
|---|---|---|---|
|**Next.js App**|Vercel|Hobby → Pro|NEXT_PUBLIC_API_URL, NEXT_PUBLIC_CLERK_KEY|
|**Hono API**|Render|Starter ($7/mo)|Main monolith. 512MB RAM sufficient for V1.|
|**BullMQ Workers**|Render|Starter ($7/mo)|Separate service. Shares Redis with API.|
|**Verdaccio**|Render|Starter ($7/mo)|Persistent disk for storage. 1GB sufficient V1.|
|**Playwright**|Render (API)|Included|Headless browser for visual diff screenshots.|
|**PostgreSQL**|Neon|Free tier → Pro|Serverless, branching for staging. pgvector enabled.|
|**Redis**|Upstash|Free → Pay-per-use|Serverless Redis. BullMQ + caching.|
|**Qdrant**|Qdrant Cloud|Free → Starter|Vector search. 1GB free tier sufficient for V1.|
|**R2**|Cloudflare|Free tier (10GB)|Object storage. Zero egress.|
|**MCP Server**|CF Workers|Free (100k/day)|Edge MCP endpoint.|

### 15.2 Environment Variables

|   |
|---|
|# Render API service<br><br>DATABASE_URL=postgresql://...         # Neon connection string<br><br>REDIS_URL=redis://...                 # Upstash Redis URL<br><br>REDIS_TOKEN=...                       # Upstash REST token<br><br>QDRANT_URL=https://...qdrant.io       # Qdrant Cloud endpoint<br><br>QDRANT_API_KEY=...                    # Qdrant API key<br><br>R2_ACCOUNT_ID=...                     # Cloudflare account<br><br>R2_ACCESS_KEY_ID=...                  # R2 credentials<br><br>R2_SECRET_ACCESS_KEY=...<br><br>R2_BUCKET_COMPONENTS=atomichub-components<br><br>R2_BUCKET_AI=atomichub-ai<br><br>R2_BUCKET_REPLAY=atomichub-replay<br><br>CLERK_SECRET_KEY=...                  # Clerk backend key<br><br>VERDACCIO_URL=http://verdaccio:4873   # Internal Render network<br><br>VERDACCIO_TOKEN=...                   # Service account token<br><br>MCP_INTERNAL_SECRET=...              # CF Worker → API auth<br><br>OPENAI_API_KEY=...                   # For text-embedding-3-small ONLY<br><br>                                      # (user models come from their own keys)<br><br># Cloudflare Worker (MCP server)<br><br>API_BASE_URL=https://api.atomichub.dev<br><br>REDIS_URL=...                         # Same Upstash instance<br><br>MCP_INTERNAL_SECRET=...              # Shared with Render API|

  

# 16. Security Considerations

|   |
|---|
|**CRITICAL ITEMS**<br><br>_These are non-negotiable security requirements that must be implemented before any public launch. Skipping any of these creates real attack surface._|

|**Concern**|**Risk**|**Mitigation**|
|---|---|---|
|**User API keys in DB**|High|Never store plain. AES-256-GCM encrypt at rest. Decrypt only in worker at job time. Key stored in env var, never in DB.|
|**URL import SSRF**|Critical|Validate URL against allowlist of domains. Block internal IPs (169.254.x.x, 10.x.x.x, 172.x.x.x). Max redirect depth: 3.|
|**Sandpack code execution**|Medium|Sandpack runs in browser iframe with sandbox attribute. No server-side code execution. CSP headers enforced.|
|**Verdaccio package poisoning**|High|Only AtomicHub service account can publish. Namespace scoped to @*/atomichub-components. Packages validated before publish.|
|**R2 presigned URL abuse**|Medium|Short TTL (15 min) on all presigned URLs. URLs scoped to specific object key. Rate limit presigned URL generation.|
|**SQL injection**|Low — mitigated|Drizzle ORM parameterizes all queries. No raw SQL string interpolation permitted.|
|**Token hash timing attack**|Medium|Use bcrypt (not SHA256) for token comparison. bcrypt's constant-time compare prevents timing attacks.|
|**Playwright SSRF via visual diff**|Critical|Playwright runs in isolated container. Network restricted to R2 URLs only. Timeout: 10s max.|

  

# 17. Recommended Build Order

|   |
|---|
|**PRINCIPLE**<br><br>_Build the dumbest thing that demonstrates the core value first. Each milestone should be independently deployable and demonstrable. Never build infrastructure before the feature it serves._|

|**Sprint**|**Milestone**|**Delivers**|**Validates**|
|---|---|---|---|
|**1**|Auth + DB foundations|Clerk auth, PostgreSQL schema (all tables), basic API scaffold, Vercel + Render deployed|Stack works end to end|
|**2**|Component Repo CRUD|Create repo, view repo, basic commit (no branching yet), R2 storage|Core VCS concept|
|**3**|Full git features|Branches, PRs, tags, revert, blame, visual diff (code only)|VCS completeness|
|**4**|CLI tool|atomichub init, login, add, push, commit, log|Developer DX|
|**5**|DNA cold start + analysis|5-question wizard, GitHub import analysis, DNA stored|DNA engine baseline|
|**6**|Screenshot → Component|AI job pipeline, BullMQ, quota, iteration loop, auto-commit|V1 AI flagship|
|**7**|Prop Playground|sandpack integration, prop schema generation, Monaco editor|V1 UX differentiator|
|**8**|Visual diffing (full)|Screenshot diff via Playwright, prop diff, side-by-side render|Key feature complete|
|**9**|MCP server|CF Workers MCP, all 10 tools, token auth, Redis caching|Sharp edge live|
|**10**|Universal URL import|Fetch pipeline, dep resolver, DNA adaptation, Playwright fallback|Import system live|
|**11**|npm + Verdaccio|Verdaccio deploy, publish on tag, user scoped packages|Distribution live|
|**12**|Cross-project sync|atomichub.lock, sync notifications, dashboard, apply command|Sync feature live|
|**13**|Social layer|Public feed, stars, forks, comments, creator profiles|Community live|
|**14**|Remaining AI suite|A11y fixer, dark mode gen, responsive gen, composition suggester|AI suite complete|
|**15**|Coherence + contracts|Full coherence engine, design contracts, enforcement gates|Quality system live|
|**16**|Polish + launch|Topology analysis, onboarding flow, documentation, demo video|V1 ship-ready|

  

# 18. System Design Summary

|   |
|---|
|**ARCHITECTURE LOCKED**<br><br>_Modular monolith on Render (Hono). Next.js on Vercel. MCP on Cloudflare Workers. PostgreSQL (Neon) + Redis (Upstash) + Qdrant Cloud + Cloudflare R2. Verdaccio on Render for npm. BullMQ for all async AI and background jobs. Every decision is optimized for zero-to-V1 speed while maintaining a clean migration path to microservices at scale._|

### Data Flow in One Sentence Per Domain

•        Auth: Clerk handles identity. API tokens stored hashed. Validated via Redis fast path.

•        VCS: Custom content-addressed commit graph in PostgreSQL. Sources in R2. Visual diff via Playwright + pixelmatch.

•        DNA: Two-level (global + workspace). Stored in PostgreSQL. Cached in Redis. Used by every AI job as system context.

•        AI: All jobs async via BullMQ. User brings own API keys. Results in R2. Quota tracked in Redis.

•        MCP: Cloudflare Workers edge server. Redis cache for <200ms. Falls back to Render API for cache misses.

•        Import: URL fetch → source extract → dep resolve → DNA adapt → commit. Playwright as last-resort fetcher.

•        Social: PostgreSQL for graph. Qdrant for semantic search. Redis for feed cache.

•        Sync: atomichub.lock tracks usage. Notifications fan-out via BullMQ. Visual diff before every apply.

_— END OF SYSTEM DESIGN DOCUMENT —_