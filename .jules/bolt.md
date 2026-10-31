## $(date +%Y-%m-%d) - [Async I/O and Hash Pre-calculation]
**Learning:** Combining synchronous file I/O (`fs.readFileSync`) and synchronous-like CPU-bound crypto operations during request handling is an anti-pattern that blocks the Node.js event loop. Wrapping `crypto.createHash` in a Promise does not make it truly asynchronous or prevent blocking.
**Action:** Use top-level await to pre-calculate static CPU-bound configurations at startup. Always use async I/O (`fs.promises.readFile`) for file operations during request handling.
