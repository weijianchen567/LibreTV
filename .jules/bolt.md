
## 2026-09-11 - Synchronous File I/O and Redundant Hashes in Page Render
**Learning:** Found that `server.mjs` was using `fs.readFileSync` for every single page render request, which severely blocks the Node.js event loop under concurrent load. Additionally, static password configurations were being SHA-256 hashed dynamically on every request, wasting CPU cycles on a bound task.
**Action:** Always verify that critical request paths use async I/O (`fs.promises.readFile`) in Node.js apps. Use top-level `await` in ES Modules to pre-calculate static cryptographic operations at startup rather than during request handling.
