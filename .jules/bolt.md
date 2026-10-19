## 2024-05-15 - Synchronous operations in page render paths block event loop

**Learning:** Found `fs.readFileSync` inside `renderPage()`, which is called on every request to `/`, `/index.html`, and `/player.html`. This blocks the Node.js event loop synchronously on every single request, meaning only one user can access the frontend at a time until the read completes. Also, checking config properties directly inside a request handler and hashing them (if configured) blocks the event loop synchronously via cryptographic functions on every request.

**Action:** Always refactor `fs.readFileSync` to `fs.promises.readFile` inside request handling paths. Static configuration hashing (e.g., `config.password` and `config.adminpassword`) should be pre-calculated at application startup utilizing ES modules top-level await, rather than per-request.
