
## 2024-05-18 - Avoid synchronous file reading on every request
**Learning:** `server.mjs` was reading HTML files synchronously on every request and calculating `sha256` hashing on every request, blocking the single-threaded Node.js event loop and preventing scalability.
**Action:** Always pre-compute static values via top-level await in config modules, and use asynchronous `fs.promises.readFile` for serving file resources on requests.
