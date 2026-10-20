
## 2026-10-20 - Prevent Event Loop Blocking in Rendering Pages
**Learning:** Found a critical performance bottleneck in `server.mjs`. `fs.readFileSync` was used to read HTML files synchronously during request handling, which blocks the Node.js event loop and significantly degrades performance under load. Also, static password hashes were recalculated on every page render rather than being pre-computed at startup.
**Action:** Replaced `fs.readFileSync` with `await fs.promises.readFile` to asynchronously load templates without blocking. Pre-calculated static config hashes (`config.password` and `config.adminpassword`) at server startup using top-level `await` to prevent repeated CPU-intensive operations per request.
