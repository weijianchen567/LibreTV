## 2026-09-26 - Node.js Server Render Loop Optimization
**Learning:** In a vanilla Node.js/Express app, using synchronous file reads (`fs.readFileSync`) or heavy CPU operations like SHA256 hashing during the request-response cycle directly blocks the main event loop, severely degrading concurrent performance.
**Action:** Always favor asynchronous I/O (`fs.promises`) during page renders and use top-level `await` to pre-compute expensive, static configurations at startup in `.mjs` entry points.
