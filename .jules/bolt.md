## 2026-08-14 - Pre-calculated Hashes & Async File Reads
**Learning:** Found that `server.mjs` used synchronous `fs.readFileSync` blocking the event loop and re-calculated SHA-256 for static configurations on every render. Also learned that implementing unbounded memory map caches for file reads creates a severe DoS vulnerability and disrupts development.
**Action:** Always use `fs.promises.readFile` and leverage top-level `await` for pre-calculating hashes at startup. Never introduce unbounded in-memory caches.
