## 2024-06-25 - Prevent event loop blocking in page rendering
**Learning:** Found synchronous `fs.readFileSync` and repeated SHA-256 hashing of static configurations in the `renderPage` function, which blocks the Node event loop and wastes CPU cycles.
**Action:** Use `fs.promises.readFile` for asynchronous file reading and pre-calculate static configuration hashes at startup using top-level `await` to improve performance.
