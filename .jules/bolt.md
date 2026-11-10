
## 2024-05-19 - Pre-calculating static hashes in Node.js
**Learning:** In `server.mjs`, CPU-bound operations like SHA-256 hashing for static configurations (e.g., passwords from env vars) block the event loop, even if wrapped in a Promise. When they are static, they can and should be pre-calculated at startup via top-level await (since it's an ES Module) to prevent this blocking on every page render.
**Action:** Identify static configurations that require hashing and pre-calculate them at startup using top-level await in ES modules to avoid event loop blocking during requests.
