## 2024-05-10 - Blocked Event Loop
**Learning:** Found that `server.mjs` was using `fs.readFileSync` and hashing static passwords on every request, blocking the Node.js event loop and significantly reducing throughput.
**Action:** Always use async file I/O (`fs.promises.readFile`) and pre-calculate CPU-bound operations (like static hashes) via top-level await in Node.js HTTP servers.
