## 2023-11-06 - Pre-calculating Node.js crypto hashes in ES modules

**Learning:** Node.js `crypto.createHash` operations are synchronous and CPU-bound, which can block the main event loop even if wrapped in a Promise. When dealing with static environment configuration (like an admin password), these shouldn't be recalculated per-request. Since `server.mjs` is an ES module, we can utilize top-level await to perform these heavy operations once during application startup.

**Action:** Identify static configurations that require expensive hashing. Use top-level await in ES modules to pre-calculate these hashes at server startup and store them in memory for fast retrieval during request handling, fallback to asynchronous hashing only when dealing with dynamic inputs.
