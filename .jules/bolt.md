## 2024-05-24 - Pre-calculate CPU-bound Hashes and Use Async I/O in Express
**Learning:** In Node.js Express servers, operations like synchronous `fs.readFileSync` and recalculating CPU-intensive operations (like SHA-256 hashes) on every route handler render block the single-threaded event loop, severely degrading concurrent request handling.
**Action:** Always pre-calculate static/configuration data at module load time (startup) and use asynchronous APIs (like `fs.promises`) for I/O operations inside route handlers to ensure the event loop remains unblocked.
