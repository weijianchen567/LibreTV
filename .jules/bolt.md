## 2023-10-24 - Pre-calculating CPU-bound operations at startup
**Learning:** In Node.js applications, CPU-bound operations like SHA-256 hashing can block the event loop if executed during request handling. Pre-calculating static hashes at startup using top-level `await` prevents this overhead on every request.
**Action:** Identify and move static CPU-bound operations out of the request-response cycle and execute them at startup to improve server throughput.
