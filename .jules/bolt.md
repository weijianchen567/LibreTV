## 2024-05-18 - [Optimized server.mjs event loop bottleneck]
**Learning:** Found a significant bottleneck in `server.mjs` where `fs.readFileSync` was used for every page render request, which blocks the Node.js event loop. Additionally, SHA256 hashes of static config values (like password) were re-calculated on every render rather than memoized at startup.
**Action:** Always favor `fs.promises.readFile` for asynchronous file reading during request handling and use top-level `await` to pre-calculate CPU-bound operations (like hashing static variables) when booting ES Modules in Node.js.
