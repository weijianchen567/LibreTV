
## 2023-11-16 - Node.js Sync Operations and Event Loop
**Learning:** Wrapping a CPU-bound operation like `crypto.createHash` in a Promise doesn't prevent it from blocking the Node.js event loop. Furthermore, using `fs.readFileSync` during web requests can severely impact concurrency.
**Action:** Always pre-calculate static values (like hashes of configuration passwords) at startup using top-level await in ES modules, and always use asynchronous I/O (`fs.promises.readFile`) for handling web requests.
