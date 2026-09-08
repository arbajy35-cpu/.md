# main_js/bundles/pageLoader.bundle.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/bundles/pageLoader.bundle.js` |
| Extension | `.js` |
| Bytes | 67390 |
| Lines | 2933 |
| SHA-256 | `3a5bd694628f98a3fd73f4dda75018c8070eaa25a3bcfcff123906311c01fc6e` |
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
- `missing`
- `loadPage`
- `cached`
- `cache`
- `normalLimit`
- `lowEndLimit`
- `limit`
- `oldestKey`
- `oldestTime`
- `fixed`
- `res`
- `html`
- `resources`
- `config`
- `destroy`
- `legacyDestroy`
- `el`
- `saved`
- `elapsed`
- `attempt`
- `origins`
- `urls`
- `u`
- `link`
- `old`
- `toast`
- `cssPromise`
- `pluginPromise`
- `homeReady`
- `homePaint`
- `container`
- `post`
- `likeBtn`
- `file`
- `key`
- `loadPromise`
- `path`
- `style`
- `exists`
- `existing`
- `script`
- `done`
- `retried`
- `timeout`
- `f`
- `root`
- `firstKey`
- `htmlString`
- `fragment`
- `storiesWrapper`
- `initFunction`
- `scrollFile`
- `crash`
- `pageId`
- `thisLoad`
- `abortController`
- `signal`
- `isStale`
- `checkAbort`
- `t0`
- `previousPage`
- `skeletonAlreadyVisible`
- `instantHome`
- `htmlPromise`
- `jsPromise`
- `initFn`
- `realCore`
- `earlyQueue`
- `publicLoadPage`
- `request`

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

`/storage/emulated/0/MINIGRAM1/main_js/bundles/pageLoader.bundle.js`

It is NOT AI generated or rewritten.

```javascript


/*
==================================================
🚀 MINIGRAM BUNDLE
FILE: pageLoader.bundle.js
GENERATED: 2026-08-29T07:28:40.286Z
SOURCE FILES: 24
==================================================
*/



/* =================================================
   FILE: main_js/pageLoader_function/state.js
   ================================================= */

// PAGE LOADER STATE
window.CURRENT_PAGE = window.CURRENT_PAGE || null;
window.LAST_PAGE = window.LAST_PAGE || null;
window.PAGE_LOAD_TIME = window.PAGE_LOAD_TIME || 0;
window.LOAD_ID = Number(window.LOAD_ID) || 0;
window.LOADING = false;
window.ACTIVE_PAGE_ID = Number(window.ACTIVE_PAGE_ID) || 0;
window.CURRENT_LOAD_ABORT = null;

window.PAGE_CACHE = window.PAGE_CACHE || new Map();
window.PAGE_STATE = window.PAGE_STATE || new Map();
window.PAGE_HTML_CACHE = window.PAGE_HTML_CACHE || new Map();

window.IS_LOW_END =
    !!window.IS_LOW_END ||
    !!(navigator.deviceMemory && navigator.deviceMemory <= 4);

window._page_resources = window._page_resources || {
    timers: [],
    intervals: [],
    observers: [],
    listeners: [],
    videos: []
};


/* =================================================
   END: main_js/pageLoader_function/state.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/pathUtils.js
   ================================================= */

window.BASE_PATH =
    window.BASE_PATH ||
    location.pathname.replace(/\/[^/]*$/, "/");

window.fixPath = function(path) {
    if (!path) return path;

    if (
        path.startsWith("http") ||
        path.startsWith("/") ||
        path.startsWith("data:")
    ) return path;

    return window.BASE_PATH + path;
};


/* =================================================
   END: main_js/pageLoader_function/pathUtils.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/safeRun.js
   ================================================= */

window.safeRun = function(fn) {
    try {
        return fn?.();
    } catch (e) {
        console.warn("⚠️ SAFE RUN:", e);
        return undefined;
    }
};


/* =================================================
   END: main_js/pageLoader_function/safeRun.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/cacheManager.js
   ================================================= */

// CACHE MANAGER — V12 TTL + HOME PROTECTION + LOW-END LIMIT
window.CACHE_TTL = Number(window.CACHE_TTL) || 60000;
window.MAX_CACHE_SIZE = Number(window.MAX_CACHE_SIZE) || 10;

window.CACHE_PRIORITY = {
    home: 100
};

window.getValidPageCache = function(page, force = false) {
    if (force) return null;

    const cached = window.PAGE_CACHE?.get(page);
    if (!cached || !cached.html) return null;

    if (Date.now() - cached.time >= window.CACHE_TTL) {
        window.PAGE_CACHE.delete(page);
        return null;
    }

    return cached;
};

window.savePageCache = function(page, html) {
    if (!page || !html) return;

    window.PAGE_CACHE.set(page, {
        html,
        time: Date.now()
    });

    window.cleanupCache?.();
};

window.cleanupCache = function() {
    const cache = window.PAGE_CACHE;
    if (!cache) return;

    const normalLimit = window.MAX_CACHE_SIZE;
    const lowEndLimit = Math.min(5, normalLimit);
    const limit = window.IS_LOW_END ? lowEndLimit : normalLimit;

    while (cache.size > limit) {
        let oldestKey = null;
        let oldestTime = Infinity;

        for (const [key, value] of cache) {
            if (key === "home") continue;

            if ((value?.time ?? Infinity) < oldestTime) {
                oldestTime = value.time;
                oldestKey = key;
            }
        }

        if (oldestKey === null) break;
        cache.delete(oldestKey);
    }
};

console.log("🚀 CACHE MANAGER V12 READY");


/* =================================================
   END: main_js/pageLoader_function/cacheManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/htmlFetcher.js
   ================================================= */

window.fetchHTML = async function(url, options = {}) {
    const { signal } = options;

    if (!url) {
        throw new Error("HTML URL is missing");
    }

    const fixed = window.fixPath ? window.fixPath(url) : url;

    if (window.PAGE_HTML_CACHE.has(fixed)) {
        return window.PAGE_HTML_CACHE.get(fixed);
    }

    const res = await fetch(
        fixed,
        signal ? { signal } : {}
    );

    if (!res.ok) {
        throw new Error(`Fetch failed: ${fixed} (${res.status})`);
    }

    const html = await res.text();

    window.PAGE_HTML_CACHE.set(fixed, html);

    return html;
};


/* =================================================
   END: main_js/pageLoader_function/htmlFetcher.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/layoutManager.js
   ================================================= */

window.applyLayout = function(layout) {
    document.getElementById("appbar")?.style.setProperty(
        "display",
        layout?.appbar === false ? "none" : "flex"
    );

    document.getElementById("bottomNav")?.style.setProperty(
        "display",
        layout?.bottomNav === false ? "none" : "flex"
    );
};


/* =================================================
   END: main_js/pageLoader_function/layoutManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/pageLifecycle.js
   ================================================= */

window.cleanupPage = async function(oldPage) {
    const resources = window._page_resources || {};

    (resources.timers || []).forEach(timer => {
        try { clearTimeout(timer); } catch {}
    });

    (resources.intervals || []).forEach(interval => {
        try { clearInterval(interval); } catch {}
    });

    (resources.observers || []).forEach(observer => {
        try { observer.disconnect(); } catch {}
    });

    (resources.listeners || []).forEach(item => {
        try {
            item.el?.removeEventListener(item.type, item.fn);
        } catch {}
    });

    (resources.videos || []).forEach(video => {
        try { video.pause(); } catch {}
    });

    document.querySelectorAll("video").forEach(video => {
        try { video.pause(); } catch {}
    });

    try {
        const config = window.PAGE_CONFIG?.[oldPage];
        const destroy = config?.destroy;

        if (destroy && window.FUNCTIONS?.[destroy]) {
            await window.FUNCTIONS[destroy]();
        } else {
            const legacyDestroy =
                window.FUNCTIONS?.[oldPage + "Destroy"];

            if (typeof legacyDestroy === "function") {
                await legacyDestroy();
            }
        }
    } catch (e) {
        console.warn("⚠️ Page destroy:", e);
    }

    window._page_resources = {
        timers: [],
        intervals: [],
        observers: [],
        listeners: [],
        videos: []
    };
};


/* =================================================
   END: main_js/pageLoader_function/pageLifecycle.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/scrollManager.js
   ================================================= */

console.log("🚀 Scroll Manager V12 Ready");

window._scrollY = window._scrollY || 0;

if (!window._scrollListenerAdded) {
    window.addEventListener("scroll", () => {
        window._scrollY = window.scrollY;
    }, { passive: true });

    window._scrollListenerAdded = true;
}

window.PAGE_STATE = window.PAGE_STATE || new Map();

window.saveScroll = function(page) {
    if (!page) return;

    if (page === "search") {
        const el = document.querySelector(".searchPage");

        window.PAGE_STATE.set(page, {
            scroll: el?.scrollTop || 0
        });
    } else {
        window.PAGE_STATE.set(page, {
            scroll: window._scrollY
        });
    }
};

window.restoreScroll = function(page) {
    const saved = window.PAGE_STATE.get(page);
    if (!saved) return;

    requestAnimationFrame(() => {
        requestAnimationFrame(() => {
            if (page === "search") {
                const el = document.querySelector(".searchPage");

                if (
                    el &&
                    Math.abs(el.scrollTop - saved.scroll) > 2
                ) {
                    el.scrollTop = saved.scroll;
                }
            } else if (
                Math.abs(window._scrollY - saved.scroll) > 2
            ) {
                window.scrollTo(0, saved.scroll);
            }
        });
    });
};


/* =================================================
   END: main_js/pageLoader_function/scrollManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/performanceManager.js
   ================================================= */

window.__MINIGRAM_T0 =
    Number(window.__MINIGRAM_T0) || performance.now();

window.__MINIGRAM_METRICS =
    window.__MINIGRAM_METRICS || {
        bootStart: window.__MINIGRAM_T0,
        firstShell: null,
        homeStart: null,
        homeReady: null,
        homePaint: null
    };

window.markMetric = function(name) {
    const elapsed =
        performance.now() - window.__MINIGRAM_T0;

    window.__MINIGRAM_METRICS[name] = elapsed;

    console.log(
        `⏱️ ${name}: ${elapsed.toFixed(2)} ms`
    );

    return elapsed;
};


/* =================================================
   END: main_js/pageLoader_function/performanceManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/retryManager.js
   ================================================= */

window.MAX_RETRY = Number(window.MAX_RETRY) || 1;

window.loadWithRetry = async function(fn, signal) {
    for (
        let attempt = 0;
        attempt <= window.MAX_RETRY;
        attempt++
    ) {
        if (signal?.aborted) {
            throw new DOMException("Aborted", "AbortError");
        }

        try {
            return await fn();
        } catch (err) {
            if (err?.name === "AbortError") {
                throw err;
            }

            console.warn(
                `⚠️ LOAD RETRY ${attempt + 1}/${window.MAX_RETRY + 1}`,
                err
            );

            if (attempt >= window.MAX_RETRY) {
                throw err;
            }
        }
    }
};


/* =================================================
   END: main_js/pageLoader_function/retryManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/skeletonManager.js
   ================================================= */

window.getSkeleton = function() {
    return `
        <div
            class="instant-skeleton"
            data-page-skeleton="true"
            aria-hidden="true"
        >
            <div class="skel-stories">
                ${Array.from(
                    { length: 5 },
                    () => `<div class="skel-story"></div>`
                ).join("")}
            </div>

            ${Array.from(
                { length: 3 },
                () => `
                    <div class="skel-post">
                        <div class="skel-user">
                            <div class="skel-avatar"></div>
                            <div class="skel-name"></div>
                        </div>
                        <div class="skel-media"></div>
                    </div>
                `
            ).join("")}
        </div>
    `;
};

window.hasInstantSkeleton = function(container) {
    return !!(
        container &&
        (
            container.querySelector("#instantSkeleton") ||
            container.querySelector(
                "[data-page-skeleton='true']"
            )
        )
    );
};

window.hasInstantHomeShell = function(container) {
    return !!(
        container &&
        container.querySelector("#homeShell")
    );
};

window.removeSkeleton = function(container) {
    if (!container) return;

    container.querySelector("#instantSkeleton")?.remove();

    container
        .querySelectorAll("[data-page-skeleton='true']")
        .forEach(el => {
            if (el.id !== "instantSkeleton") {
                el.remove();
            }
        });

    window.__INSTANT_SKELETON_ACTIVE__ = false;
};


/* =================================================
   END: main_js/pageLoader_function/skeletonManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/preconnectManager.js
   ================================================= */

window.preparePreconnect = function() {
    setTimeout(() => {
        try {
            const origins = new Set();

            Object.values(window.PAGE_CONFIG || {}).forEach(config => {
                const urls = [
                    ...(config?.css || []),
                    ...(config?.js || []),
                    config?.html
                ];

                urls.forEach(url => {
                    if (!url) return;

                    try {
                        const u = new URL(url, location.href);

                        if (u.origin !== location.origin) {
                            origins.add(u.origin);
                        }
                    } catch {}
                });
            });

            origins.forEach(origin => {
                if (
                    document.querySelector(
                        `link[rel="preconnect"][href="${origin}"]`
                    )
                ) return;

                const link = document.createElement("link");

                link.rel = "preconnect";
                link.href = origin;
                link.crossOrigin = "anonymous";

                document.head.appendChild(link);
            });
        } catch {}
    }, 0);
};


/* =================================================
   END: main_js/pageLoader_function/preconnectManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/uiManager.js
   ================================================= */

window.applyPageUI = function(config, page) {
    try {
        window.applyLayout?.(config?.layout);
    } catch {}

    queueMicrotask(() => {
        try {
            window.initIcons?.();
        } catch {}

        try {
            window.initNavigation?.();
        } catch {}
    });
};


/* =================================================
   END: main_js/pageLoader_function/uiManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/errorManager.js
   ================================================= */

window.showLoadError = function(page) {
    const old =
        document.querySelector("[data-page-load-error]");

    old?.remove();

    const toast = document.createElement("div");

    toast.dataset.pageLoadError = "true";

    toast.style.cssText = `
        position:fixed;
        top:60px;
        left:50%;
        transform:translateX(-50%);
        background:#ff3040;
        color:#fff;
        padding:12px 20px;
        border-radius:8px;
        z-index:99999;
        font-size:14px;
    `;

    toast.innerHTML = `
        Failed to load ${page}
        <button
            type="button"
            style="
                margin-left:8px;
                padding:4px 12px;
                background:#fff;
                color:#ff3040;
                border:0;
                border-radius:4px;
                font-weight:600
            "
        >Retry</button>
    `;

    toast.querySelector("button")?.addEventListener(
        "click",
        () => {
            toast.remove();
            window.loadPage(page, true);
        }
    );

    document.body.appendChild(toast);

    setTimeout(() => toast.remove(), 4000);
};


/* =================================================
   END: main_js/pageLoader_function/errorManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/loaderUtils.js
   ================================================= */

window.nextFrame = () =>
    new Promise(resolve => requestAnimationFrame(resolve));

window.nextTwoFrames = async function() {
    await window.nextFrame();
    await window.nextFrame();
};

window.idle = () =>
    new Promise(resolve => {
        if (typeof window.requestIdleCallback === "function") {
            window.requestIdleCallback(resolve);
        } else {
            setTimeout(resolve, 50);
        }
    });

window.getMainContainer = function() {
    if (
        window.__MINIGRAM_MAIN_CONTAINER &&
        document.contains(window.__MINIGRAM_MAIN_CONTAINER)
    ) {
        return window.__MINIGRAM_MAIN_CONTAINER;
    }

    window.__MINIGRAM_MAIN_CONTAINER =
        document.getElementById("mainContent");

    return window.__MINIGRAM_MAIN_CONTAINER;
};


/* =================================================
   END: main_js/pageLoader_function/loaderUtils.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/resourceManager.js
   ================================================= */

window.preparePageResources = function(config, signal) {
    const cssPromise =
        config?.css?.length &&
        typeof window.loadCSS === "function"
            ? window.loadCSS(
                config.css.map(window.fixPath || (x => x)),
                { signal }
            )
            : Promise.resolve();

    const pluginPromise =
        typeof window.loadPlugins === "function"
            ? Promise.resolve(window.loadPlugins(config))
            : Promise.resolve();

    return {
        cssPromise,
        pluginPromise
    };
};

window.loadPageJS = function(config, signal) {
    return (
        config?.js?.length &&
        typeof window.loadJS === "function"
    )
        ? window.loadJS(
            config.js.map(window.fixPath || (x => x)),
            { signal }
        )
        : Promise.resolve();
};


/* =================================================
   END: main_js/pageLoader_function/resourceManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/homeLoader.js
   ================================================= */

window.loadHomePage = async function({
    container,
    signal,
    pluginPromise
}) {
    await pluginPromise;

    if (signal?.aborted) {
        throw new DOMException("Aborted", "AbortError");
    }

    if (typeof window.loadHome !== "function") {
        throw new Error("loadHome() is not available");
    }

    await window.loadWithRetry(async () => {
        if (signal?.aborted) {
            throw new DOMException("Aborted", "AbortError");
        }

        await window.loadHome(container);

        if (signal?.aborted) {
            throw new DOMException("Aborted", "AbortError");
        }
    }, signal);

    await window.nextTwoFrames();

    if (signal?.aborted) {
        throw new DOMException("Aborted", "AbortError");
    }

    window.removeSkeleton(container);

    const homeReady = window.markMetric("homeReady");

    await window.nextFrame();

    if (signal?.aborted) {
        throw new DOMException("Aborted", "AbortError");
    }

    const homePaint = window.markMetric("homePaint");

    window.savePageCache(
        "home",
        container.innerHTML
    );

    window.__INSTANT_SKELETON_ACTIVE__ = false;

    return {
        homeReady,
        homePaint
    };
};


/* =================================================
   END: main_js/pageLoader_function/homeLoader.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/delegationManager.js
   ================================================= */

window.setupPageDelegation = function() {
    const container = window.getMainContainer?.();

    if (!container) return;

    if (container.dataset.delegated === "true") return;

    container.dataset.delegated = "true";

    container.addEventListener("click", event => {
        const post = event.target.closest(".post");

        if (post) {
            window.handlePostClick?.(post, event);
            return;
        }

        const likeBtn =
            event.target.closest("[data-action='like']");

        if (likeBtn) {
            window.handleLike?.(likeBtn);
        }
    });
};


/* =================================================
   END: main_js/pageLoader_function/delegationManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/prefetchManager.js
   ================================================= */

window.prefetchPage = function(page) {
    const cached = window.getValidPageCache?.(page, false);

    if (cached) return;

    const config = window.PAGE_CONFIG?.[page];

    if (
        !config?.html ||
        typeof window.fetchHTML !== "function"
    ) {
        return;
    }

    window.fetchHTML(config.html)
        .then(html => {
            if (!html) return;
            window.savePageCache?.(page, html);
        })
        .catch(() => {});
};


/* =================================================
   END: main_js/pageLoader_function/prefetchManager.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/cssLoader.js
   ================================================= */

//////////////////////////////////////////////////
// 🚀 ELITE CSS LOADER v3 (SMART CACHE + NO LEAK + SPA OPTIMIZED)
//////////////////////////////////////////////////

window._ACTIVE_CSS = window._ACTIVE_CSS || new Map();
window._LOADING_CSS = window._LOADING_CSS || new Map();

//////////////////////////////////////////////////
// 🚀 LOAD CSS
//////////////////////////////////////////////////
window.loadCSS = async function(files, isGlobal = false){

  files = Array.isArray(files) ? files : [files];
  if (!files.length) return;

  for (const file of files) {

    const key = file.split("?")[0];

    // ♻️ Already loaded
    if (window._ACTIVE_CSS.has(key)) {
      console.log("♻️ CSS cached:", key);
      continue;
    }

    // ⏳ Already loading
    if (window._LOADING_CSS.has(key)) {
      await window._LOADING_CSS.get(key);
      continue;
    }

    const loadPromise = new Promise((resolve) => {

      const path = window.fixPath(file);

      fetch(path)
        .then(res => {
          if (!res.ok) throw new Error("CSS fetch failed");
          return res.text();
        })
        .then(css => {

          const style = document.createElement("style");

          style.dataset.type = isGlobal ? "global" : "page";
          style.dataset.key = key;

          style.textContent = css;

          document.head.appendChild(style);

          window._ACTIVE_CSS.set(key, style);

          console.log("✅ CSS injected:", key);

          resolve();
        })
        .catch(err => {
          console.error("❌ CSS load failed:", key);
          resolve(); // safe fail
        });

    });

    window._LOADING_CSS.set(key, loadPromise);

    await loadPromise;

    window._LOADING_CSS.delete(key);
  }
};

//////////////////////////////////////////////////
// 🧹 SMART CSS CLEANUP (NO FLICKER + NO RELOAD)
//////////////////////////////////////////////////
window.cleanupPageCSS = function(keepKeys = []){

  keepKeys = Array.isArray(keepKeys) ? keepKeys : [keepKeys];

  window._ACTIVE_CSS.forEach((style, key) => {

    if (style.dataset.type === "page" && !keepKeys.includes(key)) {
      style.remove();
      window._ACTIVE_CSS.delete(key);
    }

  });

  console.log("🧹 Smart CSS cleaned");
};

//////////////////////////////////////////////////
// ♻️ HARD RESET (FULL SAFE MODE)
//////////////////////////////////////////////////
window.resetPageCSS = function(){

  window._ACTIVE_CSS.forEach((style, key) => {

    if (!style || !style.parentNode) return;

    if (style.dataset.type === "page") {
      style.remove();
      window._ACTIVE_CSS.delete(key);
    }

  });

  console.log("♻️ Full CSS reset done");
};

//////////////////////////////////////////////////
// 🔥 FORCE RELOAD (DEV TOOL)
//////////////////////////////////////////////////
window.reloadCSS = async function(file){

  const key = file.split("?")[0];

  const old = window._ACTIVE_CSS.get(key);

  if (old) {
    old.remove();
    window._ACTIVE_CSS.delete(key);
  }

  await window.loadCSS(file);
};

//////////////////////////////////////////////////
// ⚡ SMART PREFETCH (NO DUPLICATE REQUEST)
//////////////////////////////////////////////////
window.prefetchCSS = function(files){

  files = Array.isArray(files) ? files : [files];

  files.forEach(file => {

    const key = file.split("?")[0];

    // already active → skip
    if (window._ACTIVE_CSS.has(key)) return;

    // 🔥 FIX: prevent duplicate with query params
    const exists = document.querySelector(`link[href^="${key}"][rel="prefetch"]`);
    if (exists) return;

    const link = document.createElement("link");
    link.rel = "prefetch";
    link.as = "style";
    link.href = file;

    document.head.appendChild(link);
  });
};

//////////////////////////////////////////////////
// 🌍 GLOBAL CSS (RUN ONLY ONCE)
//////////////////////////////////////////////////
window.loadGlobalCSSOnce = async function(files){

  if (window.__GLOBAL_CSS_DONE__) return;

  window.__GLOBAL_CSS_DONE__ = true;

  await loadCSS(files, true);

  console.log("🌍 Global CSS loaded once");
};
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));


/* =================================================
   END: main_js/pageloader/cssLoader.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/jsLoader.js
   ================================================= */

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


/* =================================================
   END: main_js/pageloader/jsLoader.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/home.js
   ================================================= */

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

/* =================================================
   END: main_js/pageloader/home.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader_function/loaderCore.js
   ================================================= */

////////////////////////////////////////////////////////////
// 🚀 MINIGRAM PAGE LOADER CORE
// V16 — TRUE BUNDLE NATIVE CORE
//
// IMPORTANT:
//
// This file contains the REAL PageLoader engine.
//
// loaderCore.js:
//
// ✅ Contains REAL loadPage()
// ✅ Exports REAL core function
// ❌ Does NOT create public window.loadPage
// ❌ Does NOT dynamically load PageLoader modules
// ❌ Does NOT use the early bridge
//
// Public API is created ONLY by:
//
// main_js/pageLoader.js
//
// REAL EXPORT:
//
// window.__PAGE_LOADER_CORE_LOAD_PAGE__
//
// MUST point directly to:
//
// loadPage
////////////////////////////////////////////////////////////


////////////////////////////////////////////////////////////
// 🚀 REAL PAGE LOADER CORE
////////////////////////////////////////////////////////////

async function loadPage(
    page,
    force = false
){

    ////////////////////////////////////////////////////////////
    // FORCE NORMALIZATION
    ////////////////////////////////////////////////////////////

    if(
        typeof force !==
        "boolean"
    ){

        force =
            !!force;

    }


    ////////////////////////////////////////////////////////////
    // MAIN CONTAINER
    ////////////////////////////////////////////////////////////

    const container =
        window.getMainContainer?.();


    if(
        !container
    ){

        console.error(
            "❌ #mainContent not found"
        );

        return false;

    }


    ////////////////////////////////////////////////////////////
    // SAME PAGE PROTECTION
    ////////////////////////////////////////////////////////////

    if(
        window.LOADING &&
        window.CURRENT_PAGE === page &&
        !force
    ){

        return true;

    }


    ////////////////////////////////////////////////////////////
    // ABORT PREVIOUS LOAD
    ////////////////////////////////////////////////////////////

    window.CURRENT_LOAD_ABORT?.abort();


    ////////////////////////////////////////////////////////////
    // LOAD IDS
    ////////////////////////////////////////////////////////////

    const pageId =
        ++window.ACTIVE_PAGE_ID;


    const thisLoad =
        ++window.LOAD_ID;


    ////////////////////////////////////////////////////////////
    // ABORT CONTROLLER
    ////////////////////////////////////////////////////////////

    const abortController =
        new AbortController();


    window.CURRENT_LOAD_ABORT =
        abortController;


    const signal =
        abortController.signal;


    ////////////////////////////////////////////////////////////
    // STALE CHECK
    ////////////////////////////////////////////////////////////

    const isStale =
        () =>

            thisLoad !==
                window.LOAD_ID ||

            pageId !==
                window.ACTIVE_PAGE_ID ||

            signal.aborted;


    ////////////////////////////////////////////////////////////
    // ABORT CHECK
    ////////////////////////////////////////////////////////////

    const checkAbort =
        () => {

            if(
                isStale()
            ){

                throw new DOMException(
                    "Aborted",
                    "AbortError"
                );

            }

        };


    ////////////////////////////////////////////////////////////
    // LOADING STATE
    ////////////////////////////////////////////////////////////

    window.LOADING =
        true;


    const t0 =
        performance.now();


    const previousPage =
        window.CURRENT_PAGE;


    window.LAST_PAGE =
        previousPage;


    console.log(
        "🐞 LOAD PAGE:",
        page,
        "| FROM:",
        previousPage ||
            "FIRST",
        "| FORCE:",
        force
    );


    ////////////////////////////////////////////////////////////
    // MAIN LOAD
    ////////////////////////////////////////////////////////////

    try{


        ////////////////////////////////////////////////////////////
        // ⚙️ CONFIG
        ////////////////////////////////////////////////////////////

        await window.ensurePageConfig?.(
            page
        );


        checkAbort();


        const config =
            window.PAGE_CONFIG?.[
                page
            ];


        if(
            !config
        ){

            throw new Error(
                `Invalid config: ${page}`
            );

        }


        ////////////////////////////////////////////////////////////
        // ⚡ CACHE
        ////////////////////////////////////////////////////////////

        const cached =
            window.getValidPageCache?.(
                page,
                force
            );


        if(
            cached
        ){

            container.innerHTML =
                cached.html;


            container.style.opacity =
                "1";


            window.CURRENT_PAGE =
                page;


            window.__INSTANT_SKELETON_ACTIVE__ =
                false;


            window.applyPageUI?.(
                config,
                page
            );


            //////////////////////////////////////////////////
            // 📜 SCROLL
            //////////////////////////////////////////////////

            if(
                page ===
                "search"
            ){

                window.restoreScroll?.(
                    page
                );

            }else{

                window.scrollTo(
                    0,
                    0
                );

            }


            //////////////////////////////////////////////////
            // ⚡ ADAPTIVE
            //////////////////////////////////////////////////

            window.idle?.().then(
                () => {

                    if(
                        !isStale()
                    ){

                        window.applyAdaptive?.(
                            page
                        );

                    }

                }
            );


            console.log(
                `⚡ CACHE HIT: ${page} | ${Math.round(
                    performance.now() -
                    t0
                )}ms`
            );


            return true;

        }


        ////////////////////////////////////////////////////////////
        // 🧹 CLEAN PREVIOUS PAGE
        ////////////////////////////////////////////////////////////

        if(
            previousPage &&
            previousPage !== page
        ){

            await window.cleanupPage?.(
                previousPage
            );


            checkAbort();

        }


        ////////////////////////////////////////////////////////////
        // 💾 SAVE PREVIOUS SCROLL
        ////////////////////////////////////////////////////////////

        if(
            previousPage
        ){

            window.saveScroll?.(
                previousPage
            );

        }


        ////////////////////////////////////////////////////////////
        // 📍 CURRENT PAGE
        ////////////////////////////////////////////////////////////

        window.CURRENT_PAGE =
            page;


        ////////////////////////////////////////////////////////////
        // 💀 SKELETON
        ////////////////////////////////////////////////////////////

        const skeletonAlreadyVisible =
            window.hasInstantSkeleton?.(
                container
            );


        const instantHome =
            page ===
                "home" &&

            (
                window.hasInstantHomeShell?.(
                    container
                ) ||

                skeletonAlreadyVisible
            );


        if(
            !instantHome
        ){

            container.innerHTML =
                window.getSkeleton?.() ||
                "";

        }


        container.style.opacity =
            "1";


        ////////////////////////////////////////////////////////////
        // 🎨 LAYOUT
        ////////////////////////////////////////////////////////////

        try{

            window.applyLayout?.(
                config.layout
            );

        }catch(
            layoutError
        ){

            console.warn(
                "⚠️ Layout apply failed:",
                layoutError
            );

        }


        ////////////////////////////////////////////////////////////
        // 🏠 HOME METRICS
        ////////////////////////////////////////////////////////////

        if(
            page ===
            "home"
        ){

            window.__MINIGRAM_METRICS =
                window.__MINIGRAM_METRICS ||
                {};


            window.__MINIGRAM_METRICS.homeStart =
                performance.now() -
                (
                    window.__MINIGRAM_T0 ||
                    performance.now()
                );


            console.log(
                `🏠 HOME START: ${window.__MINIGRAM_METRICS.homeStart.toFixed(2)} ms`
            );

        }


        ////////////////////////////////////////////////////////////
        // 📦 PAGE RESOURCES
        ////////////////////////////////////////////////////////////

        const {
            cssPromise,
            pluginPromise
        } =
            window.preparePageResources(
                config,
                signal
            );


        ////////////////////////////////////////////////////////////
        // 📄 HTML
        ////////////////////////////////////////////////////////////

        let htmlPromise =
            null;


        if(
            page !==
            "home"
        ){

            htmlPromise =
                window.loadWithRetry(
                    () =>
                        window.fetchHTML(
                            config.html,
                            {
                                signal
                            }
                        ),
                    signal
                );

        }


        ////////////////////////////////////////////////////////////
        // 📜 PAGE JS
        ////////////////////////////////////////////////////////////

        const jsPromise =
            page !==
                "home"

                ? window.loadPageJS(
                    config,
                    signal
                )

                : Promise.resolve();


        ////////////////////////////////////////////////////////////
        // 🏠 HOME
        ////////////////////////////////////////////////////////////

        if(
            page ===
            "home"
        ){

            await window.loadHomePage({

                container,

                signal,

                pluginPromise

            });

        }


        ////////////////////////////////////////////////////////////
        // 📄 NORMAL PAGE
        ////////////////////////////////////////////////////////////

        else{

            const html =
                await htmlPromise;


            checkAbort();


            if(
                typeof html ===
                "string"
            ){

                container.innerHTML =
                    html;

            }


            window.savePageCache?.(
                page,
                html
            );

        }


        ////////////////////////////////////////////////////////////
        // 📦 RESOURCES READY
        ////////////////////////////////////////////////////////////

        await Promise.all([

            cssPromise,

            jsPromise

        ]);


        checkAbort();


        ////////////////////////////////////////////////////////////
        // 🎨 PAGE UI
        ////////////////////////////////////////////////////////////

        window.applyPageUI?.(
            config,
            page
        );


        ////////////////////////////////////////////////////////////
        // 🔌 PLUGINS + INIT
        ////////////////////////////////////////////////////////////

        if(
            page !==
            "home"
        ){

            await pluginPromise;


            checkAbort();


            await window.nextFrame?.();


            checkAbort();


            const initFn =
                window.FUNCTIONS?.[
                    config.init
                ];


            await initFn?.(
                pageId
            );

        }


        ////////////////////////////////////////////////////////////
        // 📜 SCROLL
        ////////////////////////////////////////////////////////////

        if(
            page ===
            "search"
        ){

            window.restoreScroll?.(
                "search"
            );

        }else{

            window.scrollTo(
                0,
                0
            );

        }


        ////////////////////////////////////////////////////////////
        // ⚡ ADAPTIVE
        ////////////////////////////////////////////////////////////

        window.idle?.().then(
            () => {

                if(
                    !isStale()
                ){

                    window.applyAdaptive?.(
                        page
                    );

                }

            }
        );


        ////////////////////////////////////////////////////////////
        // 🚀 READY
        ////////////////////////////////////////////////////////////

        console.log(
            `🚀 Loaded: ${page} | ${Math.round(
                performance.now() -
                t0
            )}ms`
        );


        return true;


    }catch(
        err
    ){


        ////////////////////////////////////////////////////////////
        // 🛑 ABORT
        ////////////////////////////////////////////////////////////

        if(
            err?.name ===
            "AbortError"
        ){

            return false;

        }


        ////////////////////////////////////////////////////////////
        // ❌ LOAD ERROR
        ////////////////////////////////////////////////////////////

        console.error(
            "❌ LOAD FAIL:",
            page,
            err
        );


        ////////////////////////////////////////////////////////////
        // SHOW ERROR ONLY FOR ACTIVE LOAD
        ////////////////////////////////////////////////////////////

        if(
            thisLoad ===
                window.LOAD_ID &&

            !signal.aborted
        ){

            window.showLoadError?.(
                page
            );

        }


        return false;


    }finally{


        ////////////////////////////////////////////////////////////
        // 🧹 CLEAN LOADING STATE
        ////////////////////////////////////////////////////////////

        if(
            thisLoad ===
            window.LOAD_ID
        ){

            window.LOADING =
                false;


            if(
                window.CURRENT_LOAD_ABORT ===
                abortController
            ){

                window.CURRENT_LOAD_ABORT =
                    null;

            }

        }

    }

}


////////////////////////////////////////////////////////////
// 🔗 PAGELOADER CORE EXPORT
//
// IMPORTANT:
//
// This is the REAL internal loadPage.
//
// It is NOT the public window.loadPage API.
//
// DO NOT:
//
// window.loadPage = loadPage
//
// The public API is created ONLY by:
//
// main_js/pageLoader.js
//
// This prevents:
//
// loaderCore
//      ↓
// window.loadPage
//      ↓
// bridge
//      ↓
// __REAL_LOAD_PAGE__
//      ↓
// loaderCore
//      ↓
// recursion
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_CORE_LOAD_PAGE__ =
    loadPage;


////////////////////////////////////////////////////////////
// 🔥 CORE READY
////////////////////////////////////////////////////////////

console.log(
    "🔥 PageLoader Core: READY"
);


////////////////////////////////////////////////////////////
// 🔗 REAL CORE EXPORT READY
////////////////////////////////////////////////////////////

console.log(
    "🔗 Real Core Export: READY"
);


////////////////////////////////////////////////////////////
// 📦 BUNDLE NATIVE
////////////////////////////////////////////////////////////

console.log(
    "📦 Bundle Native: ON"
);


////////////////////////////////////////////////////////////
// ⚡ DYNAMIC MODULE LOADING
////////////////////////////////////////////////////////////

console.log(
    "⚡ Dynamic Module Loading: OFF"
);

/* =================================================
   END: main_js/pageLoader_function/loaderCore.js
   ================================================= */



/* =================================================
   FILE: main_js/pageLoader.js
   ================================================= */

////////////////////////////////////////////////////////////
// 🚀 MINIGRAM PAGELOADER
// V15 — TRUE BUNDLE ENTRY
//
// IMPORTANT:
//
// This file is bundled LAST.
//
// This file MUST NOT dynamically load PageLoader modules.
//
// ALL PageLoader dependencies are already bundled:
//
// state.js
// pathUtils.js
// safeRun.js
// cacheManager.js
// htmlFetcher.js
// layoutManager.js
// pageLifecycle.js
// scrollManager.js
// performanceManager.js
// retryManager.js
// skeletonManager.js
// preconnectManager.js
// uiManager.js
// errorManager.js
// loaderUtils.js
// resourceManager.js
// homeLoader.js
// delegationManager.js
// prefetchManager.js
// loaderCore.js
//
// Bundle order:
//
// dependencies
//      ↓
// loaderCore.js
//      ↓
// pageLoader.js
//      ↓
// public window.loadPage
//
// IMPORTANT:
//
// loaderCore.js owns the REAL loadPage function.
//
// pageLoader.js owns ONLY the public wrapper/API.
//
////////////////////////////////////////////////////////////


console.log(
    "🚀 PAGE LOADER V15 BOOT"
);


////////////////////////////////////////////////////////////
// 🛡️ READY STATE
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_READY__ =
    false;


////////////////////////////////////////////////////////////
// 📦 BUNDLE MARKER
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_BUNDLE__ =
    true;


////////////////////////////////////////////////////////////
// 🔗 GET REAL CORE
//
// loaderCore.js MUST have already executed.
//
// It exposes:
//
// window.__PAGE_LOADER_CORE_LOAD_PAGE__
//
// This reference MUST point directly to:
//
// async function loadPage(...)
//
////////////////////////////////////////////////////////////

const realCore =
    window.__PAGE_LOADER_CORE_LOAD_PAGE__;


////////////////////////////////////////////////////////////
// ❌ CORE MISSING
////////////////////////////////////////////////////////////

if(
    typeof realCore !==
    "function"
){

    throw new Error(
        "PageLoader core did not expose loadPage()"
    );

}


////////////////////////////////////////////////////////////
// 🔒 SAVE REAL CORE
//
// IMPORTANT:
//
// __REAL_LOAD_PAGE__ MUST ALWAYS point to
// the REAL loaderCore function.
//
// NEVER assign:
//
// window.loadPage
//
// to this variable.
//
////////////////////////////////////////////////////////////

window.__REAL_LOAD_PAGE__ =
    realCore;


////////////////////////////////////////////////////////////
// 🛡️ REAL CORE VALIDATION
////////////////////////////////////////////////////////////

if(
    typeof window.__REAL_LOAD_PAGE__ !==
    "function"
){

    throw new Error(
        "PageLoader real core function missing"
    );

}


////////////////////////////////////////////////////////////
// 🛡️ CORE REFERENCE VALIDATION
//
// These two references MUST be identical:
//
// __PAGE_LOADER_CORE_LOAD_PAGE__
// __REAL_LOAD_PAGE__
//
////////////////////////////////////////////////////////////

if(
    window.__REAL_LOAD_PAGE__ !==
    window.__PAGE_LOADER_CORE_LOAD_PAGE__
){

    throw new Error(
        "PageLoader core reference mismatch"
    );

}


////////////////////////////////////////////////////////////
// 🔗 PRESERVE EARLY QUEUE
//
// criticalBoot.js may have created this queue
// before the PageLoader bundle finished loading.
//
// NEVER replace it before reading it.
//
////////////////////////////////////////////////////////////

const earlyQueue =
    Array.isArray(
        window.__PAGE_LOADER_QUEUE__
    )
        ? window.__PAGE_LOADER_QUEUE__
        : [];


////////////////////////////////////////////////////////////
// 🚦 MARK READY
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_READY__ =
    true;


////////////////////////////////////////////////////////////
// 🌐 PUBLIC LOADPAGE
//
// ONLY public wrapper.
//
// loaderCore remains the real engine.
//
////////////////////////////////////////////////////////////

const publicLoadPage =
function(
    page,
    force = false
){

    return window.__REAL_LOAD_PAGE__(
        page,
        force
    );

};


////////////////////////////////////////////////////////////
// 🛡️ MARK PUBLIC WRAPPER
////////////////////////////////////////////////////////////

Object.defineProperty(
    publicLoadPage,
    "__PAGE_LOADER_PUBLIC_WRAPPER__",
    {
        value: true,
        enumerable: false,
        configurable: false,
        writable: false
    }
);


////////////////////////////////////////////////////////////
// 🌐 INSTALL PUBLIC API
////////////////////////////////////////////////////////////

window.loadPage =
    publicLoadPage;


////////////////////////////////////////////////////////////
// 🛡️ SINGLE PUBLIC RECURSION CHECK
//
// window.loadPage
//       ↓
// publicLoadPage
//       ↓
// __REAL_LOAD_PAGE__
//       ↓
// loaderCore
//
// They MUST NOT be the same function.
//
////////////////////////////////////////////////////////////

if(
    window.loadPage ===
    window.__REAL_LOAD_PAGE__
){

    window.__PAGE_LOADER_READY__ =
        false;

    throw new Error(
        "PageLoader public wrapper recursion detected"
    );

}


////////////////////////////////////////////////////////////
// 🛡️ PUBLIC WRAPPER MARK CHECK
////////////////////////////////////////////////////////////

if(
    window.loadPage.__PAGE_LOADER_PUBLIC_WRAPPER__ !==
    true
){

    window.__PAGE_LOADER_READY__ =
        false;

    throw new Error(
        "PageLoader public wrapper installation failed"
    );

}


////////////////////////////////////////////////////////////
// 🔁 FLUSH EARLY QUEUE
//
// IMPORTANT:
//
// Never call:
//
// window.loadPage()
//
// here.
//
// Always call:
//
// window.__REAL_LOAD_PAGE__()
//
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_QUEUE__ =
    [];


for(
    const request of earlyQueue
){

    if(
        !request ||
        typeof request.resolve !==
        "function"
    ){

        continue;

    }


    Promise.resolve()

        .then(
            () =>
                window.__REAL_LOAD_PAGE__(
                    request.page,
                    request.force
                )
        )

        .then(
            result => {

                request.resolve(
                    result
                );

            }
        )

        .catch(
            error => {

                console.error(
                    "❌ Queued loadPage failed:",
                    error
                );


                request.resolve(
                    false
                );

            }
        );

}


////////////////////////////////////////////////////////////
// 🔗 NAVIGATION API
////////////////////////////////////////////////////////////

window.goToPage =
function(
    page,
    force = false
){

    return window.loadPage(
        page,
        force
    );

};


////////////////////////////////////////////////////////////
// 🔄 RELOAD PAGE
////////////////////////////////////////////////////////////

window.reloadPage =
function(){

    if(
        !window.CURRENT_PAGE
    ){

        return Promise.resolve(
            false
        );

    }


    return window.loadPage(
        window.CURRENT_PAGE,
        true
    );

};


////////////////////////////////////////////////////////////
// 📍 CURRENT PAGE
////////////////////////////////////////////////////////////

window.getCurrentPage =
function(){

    return window.CURRENT_PAGE;

};


////////////////////////////////////////////////////////////
// ⚙️ OPTIONAL SYSTEM INIT
//
// Already bundled.
// No dynamic loading.
//
////////////////////////////////////////////////////////////

try{

    window.setupPageDelegation?.();

}catch(error){

    console.warn(
        "⚠️ Page delegation init failed:",
        error
    );

}


try{

    window.preparePreconnect?.();

}catch(error){

    console.warn(
        "⚠️ Preconnect init failed:",
        error
    );

}


////////////////////////////////////////////////////////////
// 🔥 FINAL CORE CHECK
////////////////////////////////////////////////////////////

if(
    typeof window.__PAGE_LOADER_CORE_LOAD_PAGE__ !==
    "function"
){

    window.__PAGE_LOADER_READY__ =
        false;

    throw new Error(
        "PageLoader final core verification failed"
    );

}


////////////////////////////////////////////////////////////
// 🔥 FINAL REAL CORE CHECK
////////////////////////////////////////////////////////////

if(
    typeof window.__REAL_LOAD_PAGE__ !==
    "function"
){

    window.__PAGE_LOADER_READY__ =
        false;

    throw new Error(
        "PageLoader final real core verification failed"
    );

}


////////////////////////////////////////////////////////////
// 🔗 FINAL CORE MATCH CHECK
////////////////////////////////////////////////////////////

if(
    window.__REAL_LOAD_PAGE__ !==
    window.__PAGE_LOADER_CORE_LOAD_PAGE__
){

    window.__PAGE_LOADER_READY__ =
        false;

    throw new Error(
        "PageLoader final core reference mismatch"
    );

}


////////////////////////////////////////////////////////////
// 🚦 FINAL READY
////////////////////////////////////////////////////////////
//
// NOTE:
//
// No second recursion check here.
//
// The public wrapper recursion check above
// is the ONLY check of:
//
// window.loadPage === window.__REAL_LOAD_PAGE__
//
// This prevents duplicate recursion-check logic.
//
////////////////////////////////////////////////////////////

window.__PAGE_LOADER_READY__ =
    true;


////////////////////////////////////////////////////////////
// 🎉 READY LOGS
////////////////////////////////////////////////////////////

console.log(
    "🚀 PAGE LOADER V15 READY"
);

console.log(
    "🛡️ Abort Race Protection: ON"
);

console.log(
    "📦 Bundle System: ON"
);

console.log(
    "⚡ Dynamic Module Loading: OFF"
);

console.log(
    "🔥 PageLoader Core: READY"
);

console.log(
    "📦 Dependencies: BUNDLED"
);

console.log(
    "🚫 Individual Module Requests: OFF"
);

console.log(
    "🔗 Public API: READY"
);

/* =================================================
   END: main_js/pageLoader.js
   ================================================= */


```

---

Generated by MiniGram MD Intelligence V6.
