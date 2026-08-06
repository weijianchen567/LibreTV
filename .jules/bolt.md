
## 2024-05-24 - Event Loop Blocking in Page Render
**Learning:** Using synchronous `fs.readFileSync` inside a request handler (like `renderPage`) blocks the Node.js event loop, significantly degrading concurrency and performance when serving multiple users. Additionally, recalculating the SHA-256 hash for static configurations on every request wastes CPU cycles.
**Action:** Replace synchronous file I/O with asynchronous equivalents (`fs.promises.readFile`) in request handlers. Pre-calculate static configurations at startup using top-level await to avoid redundant CPU-bound operations during runtime.
