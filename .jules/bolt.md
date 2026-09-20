## 2026-09-20 - Express Event Loop Blocking

**Learning:** `fs.readFileSync` combined with repeatedly executing CPU-bound `sha256Hash` during incoming requests (like rendering pages) synchronously blocks the Node.js event loop, destroying throughput under load.

**Action:** Always use asynchronous methods like `fs.promises.readFile` and cache repetitive CPU operations during application initialization (e.g., using top-level await in ES Modules) for performance.