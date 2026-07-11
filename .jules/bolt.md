## 2024-05-18 - Caching Rendered Pages
**Learning:** Rendering pages with synchronous file reads and cryptographic hashing on every request causes main thread blocking.
**Action:** Use an in-memory cache with a composite key (filePath, password, adminpassword) and validate with file mtimeMs to ensure freshness while avoiding unbound memory growth since file paths are bounded.
