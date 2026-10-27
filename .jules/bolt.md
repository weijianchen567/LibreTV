## 2024-10-27 - [Avoid Event Loop Blocking on File Read & Hashing]
**Learning:** Synchronous file reads (`fs.readFileSync`) and CPU-bound crypto operations (like SHA-256 hashing) in request handlers can block the Node.js event loop, degrading performance under concurrent load. Pre-calculating static hashes at startup and using asynchronous file reads (`fs.promises.readFile`) prevents this bottleneck.
**Action:** Use `fs.promises.readFile` for dynamic page rendering and pre-calculate static configuration hashes at startup using top-level await in ES Modules.
