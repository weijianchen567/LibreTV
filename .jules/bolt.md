## 2024-05-15 - Synchronous File Reads and Repeated Hashing
**Learning:** Using `fs.readFileSync` blocks the Node.js event loop, preventing concurrent request handling. Additionally, repeatedly recalculating hashes for static configuration values (like `config.adminpassword`) on every request wastes CPU cycles.
**Action:** Replace `fs.readFileSync` with `fs.promises.readFile` for asynchronous file reading. Use top-level `await` to pre-calculate hashes for static configurations at startup to avoid repeated work during request handling.
