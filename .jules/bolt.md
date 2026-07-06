## 2026-07-06 - [Avoid Blocking Main Thread With Synchronous File Reads]
**Learning:** [The `renderPage` function in `server.mjs` was using `fs.readFileSync` synchronously. This could block the Node.js event loop unnecessarily on every request to the main page and player page, affecting overall throughput.]
**Action:** [Used an in-memory `Map` as a cache and switched to asynchronous `fs.promises.stat` and `fs.promises.readFile` with proper cache invalidation based on the file modification time (`mtimeMs`) to resolve this bottleneck.]
