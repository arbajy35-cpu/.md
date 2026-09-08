# main_js/pageLoader_function/loaderCore.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageLoader_function/loaderCore.js` |
| Extension | `.js` |
| Bytes | 16547 |
| Lines | 839 |
| SHA-256 | `6acd9ceb915da2b63aaf591f92b5eab8f520f8f6b9ced95335289a68f9f91704` |
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

- `loadPage`
- `container`
- `pageId`
- `thisLoad`
- `abortController`
- `signal`
- `isStale`
- `checkAbort`
- `t0`
- `previousPage`
- `config`
- `cached`
- `skeletonAlreadyVisible`
- `instantHome`
- `htmlPromise`
- `jsPromise`
- `html`
- `initFn`

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

`/storage/emulated/0/MINIGRAM1/main_js/pageLoader_function/loaderCore.js`

It is NOT AI generated or rewritten.

```javascript
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
```

---

Generated by MiniGram MD Intelligence V6.
