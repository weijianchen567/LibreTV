## 2024-05-24 - Server Performance Bottleneck
**Learning:** Found that `server.mjs` was using synchronous file reads (`fs.readFileSync`) for every request to `index.html` and `player.html`. This blocks the Node.js event loop and significantly hurts concurrency for static file delivery.
**Action:** Always check Express route handlers for synchronous I/O. Use in-memory Map caching combined with `fs.promises.stat` (for `mtimeMs` validation) to make frequent file rendering async and high-performance.
