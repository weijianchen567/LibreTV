## 2026-06-28 - Avoid Sync I/O in Express request handlers
**Learning:** `server.mjs` was reading HTML files from disk synchronously (`fs.readFileSync`) during the request-response cycle, which blocks the Node.js event loop and degrades server concurrency significantly, particularly when hashing involves CPU-bound tasks like `sha256Hash`.
**Action:** Use `fs.promises.readFile` and an in-memory cache validated via `fs.promises.stat` to prevent repeated synchronous and computationally heavy operations on subsequent page loads. Ensure cache size is bounded to prevent unbounded memory growth.
