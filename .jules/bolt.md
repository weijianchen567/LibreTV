## 2026-11-02 - Pre-computing SHA-256 Hashes
**Learning:** Wrapping synchronous CPU-bound operations like crypto.createHash in a Promise does not prevent them from blocking the event loop.
**Action:** Pre-calculate static configurations using top-level await at startup instead of inside route handlers.
