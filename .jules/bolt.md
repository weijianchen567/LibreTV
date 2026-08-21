## 2024-05-18 - Avoid Blocking the Event Loop

**Learning:** `server.mjs` was reading HTML files synchronously using `fs.readFileSync` and hashing passwords dynamically on every request. This caused blocking operations in the Express server, severely reducing its ability to handle concurrent requests smoothly.
**Action:** Always prefer asynchronous file reads (`fs.promises.readFile`) on server critical paths like request handlers and pre-calculate CPU-bound operations (like SHA-256 for static strings) during application startup.
