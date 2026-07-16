## 2025-02-18 - Express ES Module Hashing & Caching

**Learning:** When adding caching to an ES module-based Express server (`server.mjs`), top-level `await` is a powerful tool to pre-calculate CPU-bound operations (like SHA-256 hashing configurations at startup). `__dirname` and `log` functions must be explicitly confirmed, as ES modules do not provide `__dirname` by default (though this project constructs it explicitly). Furthermore, transforming `fs.readFileSync` to `fs.promises.readFile` avoids blocking the main event loop during cache misses.

**Action:** Before optimizing Node.js backend files, always check if they are ES modules (`.mjs` or `"type": "module"`) to leverage top-level await for pre-computing heavy tasks at startup. Always verify the presence of `__dirname` or similar polyfills before using them in file system watchers.
