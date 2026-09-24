## 2024-05-18 - Node.js Sync File Read Bottleneck
**Learning:** The Express server was previously blocking the event loop on *every* request by using `fs.readFileSync` for page renders and performing CPU-bound SHA-256 password hashing.
**Action:** Always favor `fs.promises.readFile` for dynamic page loading in Node.js to keep the event loop free. Static, configuration-based hashes should always be pre-computed at startup rather than calculated lazily per-request.
