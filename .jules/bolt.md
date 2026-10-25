## 2024-05-24 - Pre-calculating Hashes at Startup and Using Async File Reads
**Learning:** In `server.mjs`, CPU-bound operations like SHA-256 hashing for static configurations (passwords) block the Node.js event loop when performed synchronously per-request. Furthermore, `fs.readFileSync` blocks the event loop on page renders.
**Action:** Use top-level await to pre-calculate hashes at startup for static values. Fall back to async hashing for dynamic values. Also, use `fs.promises.readFile` instead of synchronous file reads.
