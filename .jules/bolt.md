## 2026-07-05 - Synchronous I/O in Async Handlers
**Learning:** The codebase has a pattern of using synchronous I/O operations (like `fs.readFileSync`) inside async Express route handlers (e.g., `renderPage`). This blocks the Node.js event loop on every request, creating a severe bottleneck under load.
**Action:** Always scan for and replace synchronous `fs` methods with `fs.promises` equivalents when dealing with route handlers. Apply in-memory caching with `mtimeMs` validation for frequently accessed files to bypass disk I/O entirely.
