## 2024-03-24 - Event Loop Blocking in Page Render
**Learning:** Found that `fs.readFileSync` and synchronous hashing via `crypto.createHash` (even when wrapped in a Promise) were being used on every request to render pages. This blocks the Node.js event loop, crippling concurrency under load.
**Action:** Always pre-calculate static configuration hashes at startup using top-level await and replace synchronous file operations with `fs.promises.readFile` for dynamic request handling to ensure the event loop remains unblocked.
