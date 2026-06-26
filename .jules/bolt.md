## 2026-06-26 - [Cache Rendered Content Carefully]
**Learning:** When adding caching to rendering logic, ensure the cache key accurately reflects all variables that influence the rendered output, OR cache the raw template before variables are interpolated. Caching the final rendered output by just the file path will result in serving stale data (e.g. wrong password hash) to subsequent requests.
**Action:** Always cache the raw file content and do string manipulation on a copy of it, OR include all dynamic inputs in the cache key.
