# main_js/pageLoader.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageLoader.js` |
| Extension | `.js` |
| Bytes | 10188 |
| Lines | 568 |
| SHA-256 | `f972fdf137d206517a94c39922276c5bc4108bcf500e97458ea14cb0d28cf113` |
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

- `CRITICAL_ERRORS_REPORT.md`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `loadPage`
- `missing`
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

`/storage/emulated/0/MINIGRAM1/main_js/pageLoader.js`

It is NOT AI generated or rewritten.

```javascript
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
```

---

Generated by MiniGram MD Intelligence V6.
