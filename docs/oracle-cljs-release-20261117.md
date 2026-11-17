# cljs release bundle built by an oracle (2026-11-17)

ORACLE evidence, not a native build. The committed `appview/etzhayyim-wasm-saiban-sb4n0j1c/cljs/public/js/app.js` is the output of a JVM shadow-cljs
release run. No CI, gate, packaging or runtime path depends on it; the Tauri host only copies the
committed bundle. The dev build (`cljs-runtime/`) that was committed before is removed.

- Command: `cd appview/etzhayyim-wasm-saiban-sb4n0j1c/cljs && CLJ_CONFIG=<work>/clj-config ./node_modules/.bin/shadow-cljs -A:oracle release app (same :oracle override as roukisho)`
- Tools: node v26.0.0, npm 11.12.1, openjdk 21.0.1, shadow-cljs 2.28.20, kotoba-lang/kotoba@426ddd2a635b6714ad60a8d7852f4f802e3e54b6 (sparse lib/)
- Input: this repository at 123ef547b9b1f995c4b879040b47fed3d6e4aa60.
- Output: `Build completed`, exit 0; `app.js` 292661 bytes, sha256 64c0aea8a4ea7fa341901ffa9731a51f2a501676c115ce0165352fabb9f048a3.
- Check: the Tauri host built from it renders the page in Chromium under a CSP with no `'unsafe-eval'`
  (no EvalError). index.html loaded js/main.js, which the build never produced (module is app); it now loads js/app.js. No console errors.
- Not shown: behaviour with live data; that a native (Amu) build produces the same code.
