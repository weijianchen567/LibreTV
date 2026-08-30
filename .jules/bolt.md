## 2026-08-30 - Prevent Event Loop Blocking in Express
**Learning:** Found that `fs.readFileSync` and synchronous CPU-intensive operations like SHA-256 hashing were being used during standard Express page rendering. This is an anti-pattern in Node.js as it blocks the main thread, especially under load. Additionally, pre-calculating static hashes at module load (using top-level await) significantly reduces per-request CPU usage.
**Action:** Always prefer `fs.promises.readFile` for template rendering. Pre-calculate invariant configurations at server startup rather than on a per-request basis.
