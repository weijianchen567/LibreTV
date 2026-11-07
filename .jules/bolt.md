## 2024-11-07 - Synchronous File I/O and Hashing Event Loop Blocking
**Learning:** Using `fs.readFileSync` for static assets and running dynamic hashing calculations using `crypto.createHash` in the main request path blocks the Node.js event loop, crippling throughput under concurrent requests.
**Action:** Always use asynchronous file system methods (e.g., `fs.promises.readFile`). Pre-calculate static cryptographic hashes at application startup via top-level `await` to prevent repeated synchronous CPU-bound operations in the request handler.
