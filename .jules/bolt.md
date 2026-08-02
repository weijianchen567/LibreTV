## 2024-02-09 - Node.js Event Loop Blocking

**Learning:** Using `fs.readFileSync` and dynamic `crypto.createHash` in request handlers (like `renderPage`) blocks the Node.js main thread, severely degrading throughput under load.
**Action:** Always prefer asynchronous I/O (`fs.promises.readFile`) and pre-calculate static values (like hashes for configuration passwords) at module load time to free up the event loop during request processing.
