
FORGE
The Design Intelligence Layer for AI-Assisted Frontend Development
Complete Product Specification  •  v1.0

Version Control
for every component you build	AI Intelligence
that learns your design taste	MCP Interface
for every AI agent you use

 
1. Executive Summary
THE PROBLEM WE ARE SOLVING
"The internet is now flooded with AI-generated slop. Every AI tool generates components that look slightly different, feel inconsistent, and don't match your existing codebase. Forge is the answer — a persistent design intelligence that understands how YOU build UI, and enforces that taste across every project, every AI tool, and every collaborator, forever."

Product Vision
Forge is a version-controlled component library platform with an AI intelligence layer. It is GitHub for frontend components, but with a Design DNA engine that understands your personal visual language and enforces coherence across every project you touch. It makes AI-assisted frontend development tasteful, consistent, and reusable by default.

The Sharp Edge — One Sentence Pitch
THE HOOK
"Connect Forge's MCP to Claude Code and it will never generate a component that doesn't match your existing design system — automatically, across every project you've ever built."

Target Users
Feature	Description	Priority
Freelancers	Build 5-20 client sites/year, rebuild same components constantly	Primary V1
Indie Devs	Personal projects, side products, portfolios — tired of starting from scratch	Primary V1
Small Teams	2-10 dev teams without budget for Chromatic + Storybook + private npm	V2 Target
Agencies	10+ sites/year, same stack, same components, no shared system	V3 Target

 
2. Product Identity
Name: FORGE
Forge was chosen deliberately. Forging is the act of crafting something with precision under pressure — shaping raw material into something durable and exact. It implies craft, permanence, and quality. It is the antithesis of AI slop. When you Forge a component, it is made to last.

Tagline	Craft components that last. Ship taste at scale.
Domain suggestion	forge.dev / useforge.dev / forgeui.dev
Voice	Precise. Confident. Anti-slop. For developers who care about craft.
Anti-positioning	Not another component library. Not a design system. Your system.

 
3. Repository & Workspace Model
Core Model: One Repo Per Component
Every component is an independent versioned repository. This is the foundational design decision. It enables precise MCP searches, targeted imports, independent versioning, and clean forking without pulling in unrelated components.

Workspace Structure
Users organize components into Workspaces. A Workspace is a logical grouping — not a monorepo. Each Workspace is essentially a tagged collection of component repos with a shared Design DNA context.

Entity	Description
User Account	Top-level identity. Owns workspaces and component repos.
Workspace	Logical project grouping (e.g. 'ClientA Dashboard', 'Personal Portfolio'). Contains component refs + shared DNA.
Component Repo	One repo per component. Has its own git-like version history, branches, tags.
Component Version	Semantic version (1.0.0). Each version is an immutable snapshot of code + metadata + DNA score.
Fork	Copy of another user's component repo. Maintains upstream link. Auto-adapted to forker's DNA.
Collection / Kit	Curated set of components published as a named kit (e.g. 'Brutalist UI Kit').

Folder Structure Per Component Repo
my-button/
  ├── component.tsx          # Main component source
  ├── component.stories.tsx  # Auto-generated Storybook story
  ├── component.test.tsx     # Auto-generated tests
  ├── forge.json             # Component metadata + DNA scores
  ├── CHANGELOG.md           # Auto-generated version history
  └── replay/
        ├── prompts.json     # All AI prompts used
        ├── screenshots/     # Input screenshots
        └── snapshots/       # Version snapshots

 
4. Import & Usage Model
Three Ways to Use Components
Feature	Description	Priority
CLI (shadcn-style)	forge add Button — copies source directly into your project. No runtime dependency. You own the code. Auto-resolves all peer dependencies.	V1 Core
npm Package	npm install @username/forge-components. Auto-published npm scope per user. Versioned. Importable from any project.	V1 Core
MCP Tool	AI agents query and inject components directly. Claude Code, Cursor, Windsurf all supported via standard MCP protocol.	V1 Core

Universal URL Import — The Game Changer
UNIVERSAL IMPORT
Users paste any component URL from any platform (shadcn/ui, ReactBits, MagicUI, Aceternity, etc.). Forge fetches the component, resolves ALL dependencies automatically, adapts it to the user's Design DNA, and commits it into their repo as a versioned component. No separate installs. No manual dependency management. One import command for the entire internet.

Supported import sources (V1):
•	Direct URL to any component page (shadcn/ui, ReactBits, MagicUI, Aceternity UI, HyperUI, etc.)
•	GitHub raw file URLs
•	CodeSandbox / StackBlitz embed URLs
•	npm package name (forge import react-hot-toast)

Dependency Resolution Engine
When a component is imported from an external URL, Forge's Dependency Resolver:
•	Parses the component source and identifies all imports
•	Cross-references against the user's existing installed packages
•	Installs only missing dependencies
•	Rewrites import paths to match the user's project structure
•	Flags any version conflicts and suggests resolutions
•	Runs a coherence pass to adapt the component's styling to the user's Design DNA

 
5. Design DNA Engine
WHAT IS DESIGN DNA
Design DNA is a machine-readable profile of your personal visual language. It is built from your code, updated with every component you create, and used by every AI tool you connect to Forge. It is the reason Forge-generated components always look like they came from you.

DNA Profile Contents
Feature	Description	Priority
Spacing Scale	Detected padding/margin patterns. Your preferred spacing rhythm (4px grid, 8px grid, etc.)	Auto-detected
Color System	Primary, secondary, semantic colors. Dark mode patterns. CSS variable naming conventions.	Auto-detected
Typography Scale	Font families, size scales, weight usage, line-height patterns.	Auto-detected
Animation Personality	Preferred easing functions, duration ranges, motion complexity level.	Auto-detected
Component Patterns	Preferred composition patterns: compound components vs props, slot patterns, etc.	Auto-detected
Naming Conventions	camelCase vs kebab-case, prop naming patterns, file naming style.	Auto-detected
Framework Conventions	Next.js App Router vs Pages, 'use client' placement, server component patterns.	Auto-detected
Complexity Level	How verbose vs minimal your components tend to be. Accessibility depth.	Auto-detected

How DNA Gets Built
•	Connect GitHub repos — Forge analyzes all .tsx/.jsx files across your repos
•	Upload codebase — zip upload, Forge runs analysis pipeline
•	Manual setup — color tokens, spacing scale, font stack via guided UI wizard
•	Progressive learning — every component you publish refines the DNA automatically

DNA in Action
On Component Creation	AI uses your DNA as system context before generating any code
On Fork	Forked component is automatically adapted to your DNA before import
On URL Import	Imported component styling is rewritten to match your DNA
On MCP Query	DNA is included in every agent context payload
On Coherence Check	New components are scored against your DNA before publish

 
6. AI Feature Modules
6.1 Screenshot to Component
The V1 flagship AI feature. Paste any screenshot of a UI element. Forge generates production-ready React + Tailwind code that matches your Design DNA. Iteration loop included — you can prompt-refine the output in-platform before committing to your repo.

Input	Screenshot (PNG/JPG/WebP), PDF page, or direct URL screenshot
Output	Production React + Tailwind component, TypeScript typed, with variants
DNA Application	Spacing, colors, typography all adapted to your DNA automatically
Iteration	In-platform prompt loop: 'Make it more minimal', 'Add loading state'
Commit	One-click commit to your Forge repo with auto-generated version tag
AI Model	User's own API key (Anthropic Claude recommended for vision quality)

6.2 Video to Animation Code
Record or paste a video of any UI animation. Forge analyzes the motion, identifies keyframes, timing curves, and interaction triggers, then generates Framer Motion or CSS animation code. Particularly powerful for replicating animations from design inspiration sites.

Input	MP4/GIF/WebM video file, or Lottie JSON
Output	Framer Motion component or CSS @keyframes + transition code
Motion Adaptation	Easing curves adapted to your DNA animation personality
prefers-reduced-motion	Auto-generated reduced motion variant included always

6.3 Coherence Engine & Taste Filter
Before any component is published to the social feed, the Coherence Engine scores it. This is Forge's quality gate and the core mechanism against AI slop.

Feature	Description	Priority
DNA Coherence Score	0-100 score: how well the component matches the author's own DNA	V1 AI
Accessibility Score	WCAG 2.1 AA compliance check. Missing ARIA, contrast ratios, keyboard nav.	V1 AI
Completeness Score	Does it have loading state? Error state? Empty state? Dark mode?	V1 AI
Slop Detection	Flags patterns common in low-quality AI generation: magic numbers, inline styles, hardcoded colors.	V1 AI
Human Touch Score	Ratio of AI-generated vs manually-edited lines. Higher manual edit = higher trust score.	V2

6.4 Agentic Component Lifecycle
The most ambitious AI module. Components are not static files — they are living entities with an agent monitoring them.

•	Variant Consolidation Agent — notices you use a Button in 12 different ways across projects and proposes a unified variant system
•	Accessibility Monitor — detects when WCAG standards update and flags non-compliant components
•	Framework Migration Agent — detects deprecated API usage (e.g. React 19 changes) and opens automated migration PRs
•	Trend Adoption Agent — surfaces trending patterns from social feed that match your DNA, asks if you want to adopt
•	Cross-Project Sync Agent — when you update a component, notifies all projects using it and proposes sync

6.5 Component Replay
Every component has a full creation history stored in its replay/ directory. Anyone who forks the component can watch how it was built — prompts, screenshots, version evolution. This is knowledge sharing, not just code sharing.

Recorded: AI Prompts	Every prompt sent during component creation or iteration
Recorded: Screenshots	All visual reference inputs used
Recorded: Version Snapshots	Immutable snapshot at each version tag
NOT Recorded	Keystroke-level edits (too invasive, too much storage)
Replay UI	Timeline scrubber in the component detail page. Step through creation history.

 
7. MCP Integration
THE STRATEGIC IMPORTANCE OF MCP
The Forge MCP is what separates this product from every other component tool. It transforms any AI coding agent — Claude Code, Cursor, Windsurf, GitHub Copilot — into a collaborator that knows your entire frontend history.

MCP Tool Suite
Feature	Description	Priority
forge.search	Semantic search across your component library. 'Find me something that handles image galleries with lazy loading'	V1 Core
forge.get	Fetch a specific component by name and version. Returns full source + metadata.	V1 Core
forge.getDNA	Returns your full Design DNA profile as structured JSON for agent context injection.	V1 Core
forge.push	Agent pushes a newly generated component back into your Forge repo with auto-versioning.	V1 Core
forge.checkCoherence	Agent checks if a component it just generated is coherent with your DNA before using it.	V1 Core
forge.listWorkspace	Returns all components in a workspace with names, descriptions, and usage metadata.	V1 Core
forge.fork	Agent forks a public component from the social feed directly into your library.	V2
forge.diff	Compares two versions of a component. Useful for agent-driven migration.	V2

MCP Auth Setup
Auth is a first-class concern. The MCP server uses standard OAuth 2.0 token flow:
•	User generates a Forge API token from their dashboard (scoped: read-only, read-write, or admin)
•	Token is added to Claude Code config: forge.mcp.token = <token>
•	MCP server validates token on every request
•	Workspace-scoped tokens available for team use
•	Token rotation and revocation from dashboard

MCP Context Payload
Every MCP response includes a standardized context block that any AI agent can use:
{ "component": { "name": "Button", "version": "2.1.0", "source": "...", },
  "dna_context": { "spacing_scale": "8px", "primary_color": "#6366F1",
    "animation_easing": "cubic-bezier(0.4, 0, 0.2, 1)", "naming": "camelCase" },
  "existing_components": ["Card", "Modal", "Navbar", "Input"],
  "coherence_score": 94,
  "instruction": "Always use these tokens. Never introduce new spacing values." }

 
8. Social & Discovery Layer
The Explore Feed
Public by default. Every published component is discoverable. The feed is the antidote to AI slop — surfacing only high-quality, coherence-scored, human-crafted components.

Feed Filters
•	Framework: React / Next.js
•	Coherence score threshold (e.g. only show components scoring 85+)
•	Human Touch: filter by human-crafted only, AI-assisted, or all
•	DNA Match: show components most compatible with YOUR DNA
•	Trending / Most Forked / Newest / Most Used
•	Collection / Kit browsing

Social Actions
Feature	Description	Priority
Fork	Copy a component into your library. Auto-adapted to your DNA. Upstream link maintained.	V1 Core
Star	Bookmark components. Stars feed the trending algorithm.	V1 Core
Comment	Threaded comments on components. Design critique, suggestions, questions.	V1 Core
Share Kit	Group your components into a named kit and publish it as a collection.	V1 Core
Inspired By	Tag your component with what inspired it. Builds the lineage graph.	V2
Provenance Graph	Visual graph showing fork lineage across the community.	V2
Weekly Digest	Email/notification of top components matching your DNA each week.	V2

Creator Profiles
Every user gets a public creator profile — auto-generated from their published components. This is a portfolio page that updates itself. For Forge's target users (freelancers, indie devs), this is a meaningful secondary benefit: building in public without extra effort.

Component Provenance & Trust
Provenance Badge	Shows fork lineage: forked from X, adapted by Y, used in Z projects
Human Crafted	Green badge: >80% manually edited lines
AI Assisted	Blue badge: AI generated, human reviewed and iterated
AI Generated	Yellow badge: minimal human edits post-generation
Community Score	Weighted score: coherence + accessibility + human touch + fork count

 
9. Cross-Project Sync
THE PROBLEM THAT NOBODY TALKS ABOUT
You fix a bug in your Button in Project 1. Projects 2 through 6 still have the bug. Forever. Forge solves this. When you update a component, every project using it gets notified. One review, one approve, and the fix ships everywhere.

How It Works
•	User installs Forge CLI in each project: npx forge init
•	Forge CLI registers the project against the user's account
•	A forge.lock file tracks which component + version each project is using
•	When a component is updated in Forge, all registered projects receive a sync notification
•	User reviews the diff in Forge dashboard and approves or skips per project
•	Approved syncs are applied via CLI: forge sync (applies all pending updates)

Sync Modes
Auto-sync (patch versions)	Bug fixes (1.0.x) auto-applied with no review required
Review required (minor)	Feature additions (1.x.0) require explicit approval
Breaking change alert (major)	API changes (x.0.0) shown as breaking, never auto-applied
Skip forever	Pin a project to a specific version, never receive sync notifications

 
10. Design Contracts (Team / V2 Feature)
Design Contracts are enforced rules at the component library level. Any component that violates a contract is flagged before it can be merged into the shared library. Think CI/CD, but for design consistency.

Example Contracts
•	All interactive components MUST have a loading state
•	All components MUST support dark mode via CSS variables
•	All motion MUST respect prefers-reduced-motion
•	All components MUST pass WCAG 2.1 AA contrast minimum
•	No hardcoded color values — only CSS variables from the design token set

Contract Enforcement
At Publish	Contract checks run before any component can be published to shared library
At Fork	Forked component is checked against your contracts before being added
At URL Import	Imported components run contract checks, violations shown with fix suggestions
Agent Enforcement	MCP includes active contracts so AI agents generate compliant code by default

 
11. Recommended Tech Stack
Frontend (The Product UI)
Framework	Next.js 15 (App Router)
Styling	Tailwind CSS v4
Component Base	Radix UI primitives (unstyled) + custom Forge design system
State Management	Zustand for client state, React Query for server state
Code Editor	Monaco Editor (for in-platform component editing)
Component Preview	sandpack (CodeSandbox's in-browser bundler) for live preview
Animations	Framer Motion

Backend
Runtime	Node.js with Bun (performance + compatibility)
Framework	Hono (fast, edge-compatible, TypeScript-native)
Database	PostgreSQL via Neon (serverless, branching, scales to zero)
ORM	Drizzle ORM (TypeScript-native, SQL-first)
Auth	Clerk or Auth.js (social login + API token management)
Storage	Cloudflare R2 (zero bandwidth fees — component files, screenshots, replays)
Search	pgvector extension on PostgreSQL for semantic MCP search
Queue	BullMQ + Redis (Upstash) for async AI jobs and sync notifications
Cache	Upstash Redis for component metadata caching

AI Layer
Primary Model	User's own API key — Claude claude-sonnet-4 (vision + code quality)
Secondary Model	User's own API key — GPT-4o (fallback, video analysis)
Embeddings	text-embedding-3-small (OpenAI) for semantic search vectors
DNA Analysis	Custom pipeline: AST parsing (TypeScript compiler API) + LLM summarization
Screenshot Analysis	Claude's vision API (best-in-class for UI understanding)

Infrastructure
Hosting	Vercel (frontend + API routes) or Railway (full backend control)
CDN	Cloudflare (component file delivery, MCP endpoint edge caching)
MCP Server	Cloudflare Workers (edge-deployed, low latency for agent queries)
npm Publishing	Verdaccio (self-hosted npm registry) or direct npmjs.com publishing
Monitoring	Sentry (errors) + Posthog (analytics) + Axiom (logs)

 
12. Core API Design
REST API — Component Operations
Method	Endpoint	Description
GET	/api/components	List all components for authenticated user
POST	/api/components	Create new component repo
GET	/api/components/:id	Get component metadata + latest version
GET	/api/components/:id/versions	List all versions of a component
POST	/api/components/:id/versions	Publish new version
POST	/api/components/import	Import component from external URL
GET	/api/components/:id/replay	Get replay history
POST	/api/components/:id/fork	Fork a public component
GET	/api/dna	Get user's Design DNA profile
POST	/api/ai/screenshot	Submit screenshot for component generation
POST	/api/ai/video	Submit video for animation generation
POST	/api/ai/coherence	Run coherence check on submitted code
GET	/api/explore	Public component feed with filters
GET	/api/mcp/search	MCP semantic search endpoint

 
13. Phased Build Roadmap
Phase 1 — V1 Core (Portfolio MVP)
Goal: Ship something real that demonstrates the full system. Enough to impress engineers and put in a resume.
Feature	Description	Priority
Auth + User accounts	Clerk-based auth, user profiles, API token generation	V1 Core
Component Repo System	Create, version, and browse component repos	V1 Core
CLI Tool (forge)	forge add, forge push, forge init, forge sync commands	V1 Core
npm Auto-publish	Each user gets @username/forge scope auto-published on version bump	V1 Core
URL Import + Dep Resolver	Paste any component URL, Forge fetches + resolves deps + commits	V1 Core
Screenshot to Component	Vision AI generates React+Tailwind from screenshot with DNA context	V1 AI
Design DNA (GitHub import)	Analyze connected GitHub repos to build initial DNA profile	V1 Core
MCP Server (read)	forge.search, forge.get, forge.getDNA, forge.listWorkspace	V1 Core
Basic social feed	Explore page, star, fork, public profiles	V1 Core
Component Replay	Store prompts + screenshots + version snapshots	V1 Core
Coherence Engine (basic)	DNA coherence score + accessibility check before publish	V1 AI

Phase 2 — V2 Growth
Feature	Description	Priority
Video to Animation	Upload video/GIF, get Framer Motion code	V2
Agentic Lifecycle	Variant consolidation, framework migration, accessibility agents	V2
Cross-Project Sync	forge.lock, sync notifications, one-click apply	V2
MCP read-write	forge.push from agent, forge.diff, forge.fork	V2
Provenance Graph	Visual lineage graph for forked components	V2
Design Contracts (team)	Enforceable rules for shared component libraries	V2
Collections / Kits	Curated component sets, publishable as named kits	V2
VSCode Extension	Browse and insert components without leaving the editor	V2

Phase 3 — V3 Scale
Feature	Description	Priority
Org / Team accounts	Shared workspaces, role-based access, team DNA	V3
Monetization	Free tier + Pro (private repos, unlimited AI credits) + Team	V3
Agency features	Client-namespaced workspaces, white-label kit publishing	V3
Figma plugin	Import Figma components directly into Forge	V3
Component marketplace	Buy and sell premium kits and collections	V3

 
14. Competitive Landscape
Why Forge Wins Where Others Didn't
THE BIT.DEV LESSON
Bit.dev attempted component version control and never gained mainstream adoption. The reason: it required too much behavior change without enough immediate payoff. Forge's answer is the MCP — the payoff is immediate and visible in the first AI session. Developers don't change workflows for better organization. They change for superpowers.

Feature	Forge	shadcn/ui	Bit.dev	Storybook	v0.dev
Personal version control	✓	✗	✓	✗	✗
Universal URL import	✓	✗	✗	✗	✗
Design DNA engine	✓	✗	✗	✗	✗
MCP for AI agents	✓	✗	✗	✗	✗
Screenshot to component	✓	✗	✗	✗	✓
Cross-project sync	✓	✗	Partial	✗	✗
Social fork layer	✓	✗	✓	✗	✗
Coherence / taste filter	✓	✗	✗	✗	✗
Component Replay	✓	✗	✗	✗	✗
Fully free V1	✓	✓	Limited	✓	Limited

 
15. Open Questions & Decisions Pending
Feature	Description	Priority
Final product name	FORGE is the recommendation. Confirm or explore alternatives before domain registration.	Decide now
npm registry approach	Self-hosted Verdaccio vs publishing directly to npmjs.com under user scope. Verdaccio = more control, npmjs = less infra.	Decide at V1 build
Video analysis model	No great open model for video-to-animation. GPT-4o or Gemini 1.5 Pro are candidates. Needs evaluation.	V2 decision
Replay storage cost	Per-component replay storage could grow large. Need per-user storage quota and compression strategy.	Decide at V1 build
DNA cold start	Users with no GitHub history have no DNA. Need a guided manual setup wizard that produces usable DNA from 5 questions.	V1 required
Fork adaptation quality	Auto-adapting a forked component to DNA is hard. Need fallback: 'Adaptation suggested — review before commit'.	V1 required
MCP latency SLA	AI agents need fast MCP responses. Target: <200ms for forge.get, <500ms for forge.search. Needs caching strategy.	V1 required

 
16. Summary — What We Are Building

THE FINAL WORD
Forge is not a component library. It is not a design system. It is the infrastructure layer that makes your taste portable — across every project, every AI agent, every collaborator, and every inspiration you encounter on the internet. It is what happens when version control, design intelligence, AI tooling, and community are built together from the ground up for the reality of how developers actually build frontend in 2025.

The product is defined. The vision is clear. The sharp edge is the MCP. The moonshot is Design DNA. The community moat is the social layer.

Next step: System architecture design.

— END OF PRODUCT SPECIFICATION —
