## 2026-06-30 - [Caching rendered pages in server.mjs]
**Learning:** The server read files synchronously and re-hashed passwords on every request.
**Action:** Introduced an in-memory map to cache the rendered page, mapping a composite key (file, passwords) to the content and its `mtimeMs` to correctly invalidate the cache if files change while saving unnecessary I/O and SHA hashing.
