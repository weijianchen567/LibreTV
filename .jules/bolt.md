## 2023-10-25 - Blocking I/O in Express Route Handlers
**Learning:** The Express route handlers in `server.mjs` were using `fs.readFileSync` inside an `async` function (`renderPage`) to read HTML templates for every request. This is a classic Node.js anti-pattern that blocks the main event loop, significantly reducing concurrent request handling capacity.
**Action:** When working on Node.js web servers, always check if file operations within request paths are synchronous. Replace them with their asynchronous equivalents (e.g., `fs.promises.readFile`) to maintain non-blocking behavior.
