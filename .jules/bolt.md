## 2026-07-20 - server.mjs LRU caching and top-level await hashes
**Learning:** Pre-computing SHA256 hashes using top-level await reduces the CPU load in request handlers. When implementing caching combined with file watchers in a Node server, the watcher's lifecycle must be tied to the cache item's eviction logic to prevent resource leaks (such as `EMFILE`).
**Action:** When creating memory bounds and cache validation using `fs.watch`, ensure that on item eviction from the cache, we check if the cache key path still has watchers attached, and if not, close them (`watcher.close()`).
