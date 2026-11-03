
## 2023-10-27 - Pre-calculating static hashes in server.mjs
**Learning:** In Node.js, even if wrapped in a Promise, CPU-bound tasks like `crypto.createHash` can block the event loop. Wrapping it in a promise doesn't magically make it non-blocking if the internal operation is completely synchronous CPU math.
**Action:** When working with static configuration that requires hashing (like environment variables), calculate the hash once at application startup using top-level await rather than on every request.
