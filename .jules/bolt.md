## 2024-05-24 - Async Read and Hash Precomputation
**Learning:** Replaced synchronous `fs.readFileSync` with `fs.promises.readFile` and pre-computed static SHA-256 hashes at server startup to prevent blocking the Node.js event loop on every page render. Avoiding in-memory Maps for file caching was necessary to prevent DoS vulnerabilities and not break development file watching, while still achieving significant performance gains.
**Action:** Always prefer asynchronous file reads and cache CPU-bound static calculations at initialization instead of per-request.
