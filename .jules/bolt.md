## 2024-05-24 - Initial Bolt Journal
**Learning:** Initialized Bolt journal.
**Action:** Ready to record performance learnings.

## 2026-09-12 - Blocking I/O in Express request handlers
**Learning:** Discovered that `fs.readFileSync` was being used inside the `renderPage` request handler in `server.mjs`. This blocks the Node.js event loop on every page render, creating a severe bottleneck for concurrent requests.
**Action:** Always verify that file system operations within request lifecycles are asynchronous (e.g., `fs.promises.readFile`) in Node.js applications to maintain non-blocking I/O.
