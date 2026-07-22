## 2026-07-22 - Pre-calculated hashes and Async File Reads
**Learning:** In a single-threaded Node.js server, replacing blocking synchronous functions (`fs.readFileSync`) with their async counterparts, and computing CPU-bound tasks for static inputs (like `config.password` hashing) at startup using top-level await significantly unblocks the event loop.
**Action:** Next time, scan the critical request path for any synchronous I/O or repeatedly computed static operations that can be optimized into async or initialization-time operations.
