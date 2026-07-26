## 2026-07-26 - Prevent Blocking Event Loop on Render Page

**Learning:** Sync file I/O (`fs.readFileSync`) and CPU-intensive operations (e.g. `crypto.createHash`) inside heavily called functions (like page rendering) block Node's single-threaded event loop, directly hurting concurrency and overall performance.

**Action:** Replace sync I/O with async counterparts (e.g. `fs.promises.readFile`) and use top-level await to pre-calculate CPU-intensive static tasks at initialization when feasible.
