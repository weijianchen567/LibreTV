## 2024-08-12 - Top-level Await & Async File Reading

**Learning:** Node.js native `crypto` methods (`sha256Hash`) are highly CPU-intensive when repeated unnecessarily. Pre-calculating them at startup utilizing top-level `await` inside ES modules `.mjs` is an efficient, safe pattern that works right out of the box. Additionally, `fs.readFileSync` creates significant latency in highly concurrent scenarios since it blocks the single-threaded Node.js event loop during I/O rendering.

**Action:** Whenever possible, use `await fs.promises.readFile` for asynchronous disk reads instead of `fs.readFileSync` inside server request-handling loops. Pre-calculate static cryptographic operations and memoize configurations dynamically at server startup to prevent redundant CPU cycles during user requests.
