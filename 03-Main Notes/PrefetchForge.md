

!. mono repo - - **Monolith:** An architectural style where the entire                  software system is built and deployed as a single unit.
      
- **Monorepo:** A strategy for _storing_ code. You can have hundreds of independent microservices (not a monolith) all living inside one monorepo.
  
  
  2. |**Feature**|**npm (Node Package Manager)**|**pnpm (Performant NPM)**|
|---|---|---|
|**Philosophy**|The standard, reliable default.|Speed and disk-space optimization.|
|**Storage**|Downloads a fresh copy of a library for every single project.|Saves a library **once** in a global store and "links" to it.|
|**Disk Space**|Uses a lot of space (heavy `node_modules`).|Uses very little space.|
|**Installation**|Slower (installs sequentially).|Much faster (installs in parallel).|

