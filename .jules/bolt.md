## 2024-03-24 - Pre-calculating hashes and avoiding Sync File reads
**Learning:** Found an opportunity to pre-calculate crypto hashes at start up, avoiding redundant recalculations every time `renderPage` is hit. Also, `fs.readFileSync` should be replaced with `fs.promises.readFile` in `renderPage` to avoid blocking the event loop on page loads.
**Action:** Use top-level await in `server.mjs` to pre-calculate `passwordHash` and `adminPasswordHash` and use them in `renderPage`, along with switching to `fs.promises.readFile`.
