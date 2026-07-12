## 2026-07-12 - Unbounded Cache DoS Vulnerability
**Learning:** When adding caching to server-side rendering logic based on dynamic inputs (like passwords), using a plain `Map` without eviction creates a Denial of Service vulnerability because an attacker can spam unique passwords to cause unbounded memory growth.
**Action:** Always constrain caches with a maximum size limit (like a simple LRU using `Map.size` and `Map.keys().next().value` for eviction) when caching user-provided inputs.
