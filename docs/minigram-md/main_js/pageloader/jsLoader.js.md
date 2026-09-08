# main_js/pageloader/jsLoader.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageloader/jsLoader.js` |
| Extension | `.js` |
| Bytes | 4912 |
| Lines | 180 |
| SHA-256 | `065a32805cae9fa01fad9bfad563066b67d39c58a00fcec93d45dfb07506cf5c` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`main_js`

The local intelligence engine detected
0 direct dependencies
and 0 consumers.

## 5. Dependencies

- None

## 6. Used By

- None

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `applyFonts`
- `file`
- `loadPromise`
- `existing`
- `script`
- `done`
- `retried`
- `timeout`
- `link`
- `f`
- `root`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- No detected errors

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/main_js/pageloader/jsLoader.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
// 🚀 ULTIMATE JS LOADER v3 (STABLE + SAFE + NO FAKE LOAD)
//////////////////////////////////////////////////

window._LOADED_JS = window._LOADED_JS || new Set();
window._LOADING_JS = window._LOADING_JS || new Map();

//////////////////////////////////////////////////
// 🚀 LOAD JS
//////////////////////////////////////////////////
window.loadJS = async function(files){

  files = Array.isArray(files) ? files : [files];
  if (!files || files.length === 0) return;

  for (const file of files){

    // ♻️ Already loaded
    if (window._LOADED_JS.has(file)){
      console.log("♻️ JS cached:", file);
      continue;
    }

    // ⏳ Already loading
    if (window._LOADING_JS.has(file)){
      await window._LOADING_JS.get(file);
      continue;
    }

    const loadPromise = new Promise((resolve)=>{

      const existing = document.querySelector(`script[data-src="${file}"]`);

      if (existing){
        window._LOADED_JS.add(file);
        return resolve();
      }

      const script = document.createElement("script");

      script.src = window.fixPath(file);

      // ✅ FIXED (no conflict)
      script.async = false;

      script.dataset.src = file;

      let done = false;
      let retried = false;

      //////////////////////////////////////////////////
      // ⏱️ TIMEOUT PROTECTION (SAFE)
      //////////////////////////////////////////////////
      const timeout = setTimeout(()=>{
        if (!done){
          console.error("⏱️ JS timeout:", file);

          done = true;
          clearTimeout(timeout);

          window._LOADING_JS.delete(file);

          resolve(); // ❗ don't mark as loaded
        }
      }, 8000);

      //////////////////////////////////////////////////
      // ✅ SUCCESS
      //////////////////////////////////////////////////
      script.onload = () => {
        if (done) return;

        console.log("✅ JS loaded:", file);

        done = true;
        clearTimeout(timeout);

        window._LOADED_JS.add(file);
        window._LOADING_JS.delete(file);

        resolve();
      };

      //////////////////////////////////////////////////
      // ❌ ERROR + RETRY
      //////////////////////////////////////////////////
      script.onerror = () => {

        if (!retried){
          retried = true;

          console.warn("🔁 retry:", file);

          script.remove();

          setTimeout(()=>{
            window._LOADING_JS.delete(file);
            window.loadJS([file]).then(resolve);
          }, 120);

        } else {
          console.error("❌ failed:", file);

          done = true;
          clearTimeout(timeout);

          window._LOADING_JS.delete(file);

          resolve(); // ❗ don't mark as loaded
        }
      };

      document.body.appendChild(script);
    });

    window._LOADING_JS.set(file, loadPromise);

    await loadPromise;
  }
};

//////////////////////////////////////////////////
// 🧹 RESET JS CACHE (DEV TOOL)
//////////////////////////////////////////////////
window.resetJS = function(){

  document.querySelectorAll("script[data-src]").forEach(s => s.remove());

  window._LOADED_JS.clear();
  window._LOADING_JS.clear();

  console.log("🧹 JS cache cleared");
};

//////////////////////////////////////////////////
// ⚡ SMART PREFETCH (NO DUPLICATE)
//////////////////////////////////////////////////
window.prefetchJS = function(files){

  files = Array.isArray(files) ? files : [files];

  files.forEach(file => {

    if (window._LOADED_JS.has(file)) return;

    if (document.querySelector(`link[href="${file}"][rel="prefetch"]`)) return;

    const link = document.createElement("link");

    link.rel = "prefetch";
    link.as = "script";
    link.href = file;

    document.head.appendChild(link);
  });
};

//////////////////////////////////////////////////
// ⚡ CRITICAL JS (PRIORITY LOAD)
//////////////////////////////////////////////////
window.loadCriticalJS = async function(files){
  console.log("⚡ Critical JS loading...");
  await window.loadJS(files);
};

//////////////////////////////////////////////////
// 🎨 FONT APPLY (GLOBAL SAFE)
//////////////////////////////////////////////////
function applyFonts(page){

  const f = window.PAGE_CONFIG[page]?.fonts || {};

  const root = document.documentElement;

  root.style.setProperty("--font-ui", `${f.ui || "Open Sans"}, system-ui, sans-serif`);
  root.style.setProperty("--font-title", `${f.title || "Poppins"}, sans-serif`);
  root.style.setProperty("--font-caption", `${f.caption || "Comfortaa"}, sans-serif`);
}
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
