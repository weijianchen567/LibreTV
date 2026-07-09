## 2024-05-18 - Caching rendered pages and avoiding synchronous fs reads

**Learning:** `server.mjs` was reading HTML files with synchronous `fs.readFileSync` and recalculating SHA-256 hashes repeatedly on every page load request (like `/` or `/player.html`). This is an anti-pattern as it blocks the Node.js event loop on the main thread and performs redundant disk I/O.
**Action:** Replaced `fs.readFileSync` with `fs.promises.readFile` to avoid blocking the event loop. Also implemented a bounded Map-based cache (max 100 entries) in `renderPage` using a composite key (`filePath`, `password`, `config.adminpassword`) and checked `mtimeMs` via `fs.promises.stat` to ensure the cache invalidates properly when the file is updated.
