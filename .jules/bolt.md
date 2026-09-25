## 2026-09-25 - Prevent Event Loop Blocking in Rendering
**Learning:** Synchronous file reading (`fs.readFileSync`) combined with repeated CPU-intensive operations (like pre-hashing static configs on every render using `crypto.createHash`) within a hot route severely blocks the Node.js event loop, preventing the server from handling concurrent requests efficiently.
**Action:** Always pre-calculate static/constant CPU-bound configurations at startup (using top-level await in ES modules) and strictly use asynchronous I/O (`fs.promises.readFile`) in request handlers to maintain high throughput.
