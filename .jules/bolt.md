## 2024-05-23 - Initial Optimization
**Learning:** Node.js file system methods can be synchronous (`fs.readFileSync`) which blocks the event loop on every request, degrading performance under load. Also, repeatedly hashing static configs on each request burns CPU unnecessarily.
**Action:** Use `fs.promises.readFile` for asynchronous file reading in request handlers. Pre-compute hashes for static configuration values like passwords using top-level await during server startup.
