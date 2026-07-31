## 2023-10-27 - Blocking Event Loop in Request Handlers
**Learning:** Synchronous file reads (`fs.readFileSync`) and repeated CPU-bound operations (like SHA-256 hashing) inside request handlers block the Express event loop, causing severe performance degradation and increased latency under load.
**Action:** Pre-calculate static configurations (e.g., password hashes) at startup using top-level await, and always use asynchronous I/O (`fs.promises.readFile`) for per-request file operations to keep the event loop non-blocking.
