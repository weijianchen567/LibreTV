## 2024-05-18 - [Blocked Event Loop in Page Renders]
**Learning:** Found that `server.mjs` was using `fs.readFileSync` and recalculating SHA-256 hashes on every page render request, which blocks the Node.js event loop and significantly degrades concurrent request performance.
**Action:** Always prefer `fs.promises.readFile` for dynamic page serving, and pre-calculate static configuration hashes at startup using top-level await to avoid unnecessary CPU-bound work on the hot path.
