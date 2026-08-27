# Bolt's Performance Journal
## 2026-08-27 - [Pre-calculating configuration hashes]
**Learning:** In Node.js applications with static configurations, pre-calculating hashes like SHA-256 for passwords at startup prevents unnecessary blocking of the event loop during page renders. Additionally, using synchronous file reading (like fs.readFileSync) in a request handler blocks the main thread, leading to poor performance.
**Action:** Always prefer asynchronous file reading (e.g., fs.promises.readFile) in request handlers, and compute CPU-bound values statically at startup where possible.
