## 2024-05-24 - [Avoid synchronous I/O and repeating CPU-bound operations on requests]
**Learning:** Using `fs.readFileSync` on every request and repeating synchronous CPU-bound operations (like crypto hashes wrapped in Promises) blocks the event loop and significantly degrades concurrent request performance. Node's `crypto.createHash` inside a Promise is still synchronous.
**Action:** Use `fs.promises.readFile` for I/O operations inside request handlers, and pre-calculate static CPU-bound data at startup using top-level await.
