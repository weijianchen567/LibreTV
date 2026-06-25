## 2024-06-25 - Prevent Event Loop Blocking in Page Rendering
**Learning:** The application was using synchronous `fs.readFileSync` and redundant cryptographic `sha256Hash` calls inside the `renderPage` route handler, causing the Node.js event loop to block on every page load.
**Action:** Replaced `fs.readFileSync` with `fs.promises.readFile` and pre-computed static password hashes at startup using top-level `await`.
