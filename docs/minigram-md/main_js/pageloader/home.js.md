# main_js/pageloader/home.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageloader/home.js` |
| Extension | `.js` |
| Bytes | 7426 |
| Lines | 236 |
| SHA-256 | `4e01143e08a8a2ff87737d21601feb48315e9c1f5152eb6386ccf7d45aae116a` |
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
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `report.json`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `missing`
- `config`
- `firstKey`
- `htmlString`
- `res`
- `fragment`
- `storiesWrapper`
- `initFunction`
- `scrollFile`
- `crash`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **LOW** — Duplicate Filename: home.js appears in 3 locations

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

`/storage/emulated/0/MINIGRAM1/main_js/pageloader/home.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
// 🏠 HOME PAGE LOADER - FIXED VERSION
//////////////////////////////////////////////////

console.log("🏠 pageloader/home.js loaded");

//////////////////////////////////////////////////
// 🚀 LOAD HOME
//////////////////////////////////////////////////

window.loadHome = async function(container) {
  try {
    console.log("🏠 Loading Home...");

    //////////////////////////////////////////////////
    // 📦 GET PAGE CONFIG
    //////////////////////////////////////////////////
    const config = window.PAGE_CONFIG?.home;

    if (!config) {
      throw new Error("Home config missing");
    }

    if (!container) {
      throw new Error("Container missing");
    }

    //////////////////////////////////////////////////
    // 🛡️ CLEANUP PREVIOUS PAGE
    //////////////////////////////////////////////////
    // Kill old stories observers/timers before doing anything
    if (typeof window.destroyStories === "function") {
      window.destroyStories();
      console.log("🧹 Old Stories cleaned");
    }

    // Reset scroll flag so new scroll engine can init
    window.__SCROLL_INITIALIZED = false;

    //////////////////////////////////////////////////
    // 🎨 LOAD CSS
    //////////////////////////////////////////////////
    if (typeof window.loadCSS === "function") {
      await window.loadCSS?.(config.css || []);
      console.log("✅ Config CSS Loaded");
    } else {
      console.warn("⚠️ loadCSS missing");
    }

    //////////////////////////////////////////////////
    // 📦 PAGE CACHE - STRING BASED
    //////////////////////////////////////////////////
    window.PAGE_CACHE = window.PAGE_CACHE || new Map();

    // LRU: Delete oldest if over limit
    if (window.PAGE_CACHE.size >= 5) {
      const firstKey = window.PAGE_CACHE.keys().next().value;
      window.PAGE_CACHE.delete(firstKey);
      console.log("🗑️ Cache evicted:", firstKey);
    }

    //////////////////////////////////////////////////
    // 📦 GET HTML STRING
    //////////////////////////////////////////////////
    let htmlString;

    if (window.PAGE_CACHE.has("home")) {
      console.log("⚡ HOME CACHE HIT");
      htmlString = window.PAGE_CACHE.get("home");
    } else {
      console.log("🌐 Fetching HTML");

      if (!config.html) {
        throw new Error("config.html missing");
      }

      const res = await fetch(config.html);
      if (!res.ok) {
        throw new Error("HTML fetch failed");
      }

      htmlString = await res.text();
      window.PAGE_CACHE.set("home", htmlString);
      console.log("💾 Home Cached");
    }

    //////////////////////////////////////////////////
    // 🚀 CREATE FRESH FRAGMENT EVERY TIME
    //////////////////////////////////////////////////
    const fragment = document
     .createRange()
     .createContextualFragment(htmlString);

    //////////////////////////////////////////////////
    // 🚀 FAST RENDER
    //////////////////////////////////////////////////
    container.replaceChildren(fragment);
    console.log("✅ HTML Rendered");

    //////////////////////////////////////////////////
    // 💥 RESET STORIES STATE
    //////////////////////////////////////////////////
    window.STORIES_INITIALIZED = false;
    const storiesWrapper = document.getElementById("storiesWrapper");

    if (storiesWrapper) {
      storiesWrapper.replaceChildren();
      storiesWrapper.style.display = "";
      storiesWrapper.style.visibility = "visible";
      storiesWrapper.style.opacity = "1";
    }

    //////////////////////////////////////////////////
    // ⚡ WAIT DOM PAINT
    //////////////////////////////////////////////////
    await new Promise(resolve => {
      requestAnimationFrame(resolve);
    });

    //////////////////////////////////////////////////
    // 📜 LOAD PAGE JS
    //////////////////////////////////////////////////
    if (typeof window.loadJS === "function") {
      await window.loadJS?.(config.js || []);
      console.log("✅ Config JS Loaded");
    } else {
      console.warn("⚠️ loadJS missing");
    }

    //////////////////////////////////////////////////
    // 🧠 RESET PAGE STATE
    //////////////////////////////////////////////////
    window.STATE = window.STATE || {};
    window.STATE.PAGE = 0;
    window.STATE.FEED = [];
    window.STATE.END = false;
    window.STATE.LOADING = false;

    //////////////////////////////////////////////////
    // 🚀 INIT PAGE
    //////////////////////////////////////////////////
    const initFunction = window.FUNCTIONS?.[config.init];
    if (typeof initFunction === "function") {
      await initFunction();
      console.log("✅ Page Init Success");
    } else {
      console.warn("⚠️ Init function missing");
    }

    //////////////////////////////////////////////////
    // 📚 INIT STORIES
    //////////////////////////////////////////////////
    if (typeof window.initStories === "function") {
      try {
        // Double RAF for final paint
        await new Promise(resolve => {
          requestAnimationFrame(() => {
            requestAnimationFrame(resolve);
          });
        });

        window.initStories();
        console.log("✅ Stories Ready");
      } catch (e) {
        console.error("❌ initStories error:", e);
      }
    }

    //////////////////////////////////////////////////
    // 📜 LOAD SCROLL ENGINE
    //////////////////////////////////////////////////
    if (config.scroll?.enabled) {
      const scrollFile = `page_config/scroll/scroll_${config.scroll.config}.js`;

      await window.loadJS?.([scrollFile]);

      if (typeof window.initScroll === "function") {
        // Always re-init on Home load
        window.initScroll();
        window.__SCROLL_INITIALIZED = true;
        console.log("✅ Dynamic Scroll Ready");
      }
    }

    //////////////////////////////////////////////////
    // 🎉 DONE
    //////////////////////////////////////////////////
    console.log("🚀 Home Ready");

  } catch (err) {
    //////////////////////////////////////////////////
    // 💀 FINAL CRASH
    //////////////////////////////////////////////////
    console.error("❌ Home Load Error:", err);

    if (container) {
      const crash = document.createElement("div");
      crash.style.color = "white";
      crash.style.padding = "30px";
      crash.style.textAlign = "center";
      crash.style.fontSize = "18px";
      crash.innerHTML = `
        ❌ HOME CRASH
        <br><br>
        Check console logs
      `;
      container.replaceChildren(crash);
    }
  }
};

//////////////////////////////////////////////////
// 🛡️ GLOBAL ERROR TRACK
//////////////////////////////////////////////////

if (!window.__GLOBAL_ERROR_TRACKER) {
  window.__GLOBAL_ERROR_TRACKER = true;
  window.addEventListener?.(
    "error",
    e => {
      console.log(
        "💀 ERROR IN FILE:",
        e.filename,
        e.message,
        "LINE:",
        e.lineno
      );
    }
  );
}

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log("🔥 HOME LOADER READY");
```

---

Generated by MiniGram MD Intelligence V6.
