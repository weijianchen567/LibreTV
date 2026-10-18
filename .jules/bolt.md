
## 2024-10-18 - Optimize renderPage block and CPU bounds
**Learning:** Found synchronous `fs.readFileSync` and redundant SHA-256 hashing during every page render on the hot path in Express backend. Since the file is already an ES Module (`server.mjs`), I can safely use top-level `await` to pre-calculate hashes during initialization, saving CPU overhead per request.
**Action:** Replace `fs.readFileSync` with `fs.promises.readFile` to avoid event loop blocking, and pre-calculate static configuration hashes at startup with top-level `await`. Only recompute hashes dynamically if the supplied arguments differ from the static config.
