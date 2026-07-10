
## 2024-07-10 - Synchronous Rendering Bottleneck
**Learning:** `server.mjs` was using `fs.readFileSync` and synchronous expensive operations (`sha256Hash` resolution despite being wrapped in Promise) during the rendering of every static page request (`/`, `/player.html`). This caused a significant main-thread block, bottlenecking high-concurrency performance.
**Action:** Replace `readFileSync` with `fs.promises.readFile` and use an in-memory `Map` to cache the fully rendered output string, checking `fs.promises.stat(filePath).mtimeMs` for zero-downtime cache invalidation to prevent serving stale files. Ensure cache key accounts for dynamic environmental factors (e.g., passwords).
