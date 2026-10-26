## 2024-05-24 - Pre-calculating static hashes to avoid event loop blocking

**Learning:** In Node.js, CPU-intensive synchronous operations like `crypto.createHash` block the main event loop, causing severe latency on concurrent requests. Even though they were wrapped in a `Promise` in `sha256Hash()`, the underlying operation (`crypto.createHash('sha256').update(input)`) remained synchronous CPU-bound logic executing on the main thread rather than offloading to the thread pool (like `crypto.pbkdf2` does).

**Action:** For values that are static for the lifetime of the process (like `config.password`), compute them once at startup using top-level `await` instead of dynamically recalculating them for every single request in functions like `renderPage()`. Also, ensure asynchronous I/O (`fs.promises.readFile`) is used over synchronous operations (`fs.readFileSync`) in request handlers.
