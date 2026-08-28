## 2025-02-18 - Avoid synchronous file reading and duplicated cryptographic hashing during web requests
**Learning:** During page rendering, `fs.readFileSync` blocks the Node.js event loop, preventing concurrent requests from being handled. Additionally, re-calculating SHA-256 hashes of static config values on every request consumes CPU cycles unnecessarily.
**Action:** Replace `fs.readFileSync` with asynchronous `fs.promises.readFile` for template loading in express endpoints. Pre-calculate static configuration hashes at startup using top-level `await` to save CPU cycles per request.
