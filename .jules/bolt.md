## 2024-11-20 - Synchronous file reads and faux-async crypto operations blocking Node event loop
**Learning:** Wrapping synchronous CPU-bound operations (like Node.js `crypto.createHash`) in a Promise does not make them asynchronous and will still block the event loop. In addition, using `fs.readFileSync` on hot paths like request handlers blocks the entire server while reading from disk.
**Action:** Pre-calculate static hashes at startup (using top-level await if needed) rather than per-request. Always use true async file reads (`fs.promises.readFile`) in request handlers.
