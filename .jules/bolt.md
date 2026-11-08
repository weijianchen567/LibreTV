## 2025-01-20 - Pre-calculate static hashes and avoid sync IO
**Learning:** Found synchronous file reading (`fs.readFileSync`) and repeated CPU-bound hashing (`crypto.createHash`) for static values in the main page render path (`renderPage`). This blocks the event loop on every page load.
**Action:** Use top-level await to pre-calculate hashes for static config values on server start, and always use asynchronous `fs.promises.readFile` to prevent blocking the Node.js event loop during request handling.
