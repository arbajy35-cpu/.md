# main_js/boot/criticalBoot.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/boot/criticalBoot.js` |
| Extension | `.js` |
| Bytes | 10407 |
| Lines | 453 |
| SHA-256 | `aa434573ea0ddc8368623474a706a837c13adca4738d66c2361d246eab347127` |
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

- `loadCriticalBoot`
- `is`
- `corePromise`
- `configPromise`
- `supabaseLibPromise`
- `authenticated`
- `earlyLoadPage`

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

`/storage/emulated/0/MINIGRAM1/main_js/boot/criticalBoot.js`

It is NOT AI generated or rewritten.

```javascript
////////////////////////////////////////////////////////////
//  MINIGRAM CRITICAL BOOT
// V6 � BUNDLE ONLY + LOW LATENCY + RECURSION SAFE
//
// CORE
// UI
// CONFIG
// SUPABASE
// AUTH
// PAGELOADER BUNDLE
// FEED
//
// PAGELOADER:
//
// ONE REQUEST ONLY
//
// pageLoader.bundle.js contains:
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
// pageLoader.js
//
// CRITICAL BOOT NEVER LOADS THESE INDIVIDUALLY.
////////////////////////////////////////////////////////////


async function loadCriticalBoot(){


    ////////////////////////////////////////////////////////////
    //  CORE + UI
    //
    // Independent bundles can load together.
    ////////////////////////////////////////////////////////////

    const corePromise =
        Promise.all([

            loadScript(
                "main_js/bundles/core.bundle.js"
            ),

            loadScript(
                "main_js/bundles/ui.bundle.js"
            )

        ]);


    ////////////////////////////////////////////////////////////
    //  CONFIG
    ////////////////////////////////////////////////////////////

    const configPromise =
        loadScript(
            "main_js/pageloader/config.js"
        );


    ////////////////////////////////////////////////////////////
    //  SUPABASE LIBRARY
    ////////////////////////////////////////////////////////////

    const supabaseLibPromise =
        loadScript(
            "https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"
        );


    ////////////////////////////////////////////////////////////
    //  WAIT CRITICAL DEPENDENCIES
    ////////////////////////////////////////////////////////////

    await Promise.all([

        corePromise,

        configPromise,

        supabaseLibPromise

    ]);


    ////////////////////////////////////////////////////////////
    //  CONFIG LOADER + SUPABASE CLIENT
    ////////////////////////////////////////////////////////////

    await Promise.all([

        loadScript(
            "main_js/config_Loader.js"
        ),

        loadScript(
            "supabase.js"
        )

    ]);


    ////////////////////////////////////////////////////////////
    //  AUTH
    ////////////////////////////////////////////////////////////

    const authenticated =
        await checkAuth();


    ////////////////////////////////////////////////////////////
    //  AUTH FAILED
    ////////////////////////////////////////////////////////////

    if(
        !authenticated
    ){

        console.log(
            " AUTH REQUIRED"
        );

        return false;

    }


    ////////////////////////////////////////////////////////////
    //  PAGELOADER BUNDLE
    //
    // IMPORTANT:
    //
    // ONLY ONE REQUEST.
    //
    // NOTHING INSIDE PAGELOADER IS LOADED
    // INDIVIDUALLY FROM CRITICAL BOOT.
    ////////////////////////////////////////////////////////////

    console.log(
        " Loading PageLoader Bundle..."
    );


    ////////////////////////////////////////////////////////////
    //  EARLY QUEUE
    ////////////////////////////////////////////////////////////

    window.__PAGE_LOADER_READY__ =
        false;


    window.__PAGE_LOADER_QUEUE__ =
        window.__PAGE_LOADER_QUEUE__ || [];


    ////////////////////////////////////////////////////////////
    //  EARLY BRIDGE
    ////////////////////////////////////////////////////////////

    let earlyLoadPage =
        null;


    ////////////////////////////////////////////////////////////
    //  CREATE EARLY BRIDGE ONLY IF NEEDED
    ////////////////////////////////////////////////////////////

    if(
        typeof window.loadPage !==
        "function"
    ){

        ////////////////////////////////////////////////////////////
        //  EARLY LOADPAGE
        ////////////////////////////////////////////////////////////

        earlyLoadPage =
        function(
            page,
            force = false
        ){

            ////////////////////////////////////////////////////////
            //  REAL CORE ALREADY READY
            ////////////////////////////////////////////////////////

            if(
                window.__PAGE_LOADER_READY__ &&

                typeof window.__REAL_LOAD_PAGE__ ===
                    "function"
            ){

                return window.__REAL_LOAD_PAGE__(
                    page,
                    force
                );

            }


            ////////////////////////////////////////////////////////
            //  QUEUE REQUEST
            ////////////////////////////////////////////////////////

            console.log(
                " PageLoader waiting:",
                page
            );


            return new Promise(
                resolve => {

                    window.__PAGE_LOADER_QUEUE__.push({

                        page,

                        force,

                        resolve

                    });

                }
            );

        };


        ////////////////////////////////////////////////////////////
        //  MARK EARLY BRIDGE
        ////////////////////////////////////////////////////////////

        Object.defineProperty(
            earlyLoadPage,
            "__PAGE_LOADER_BRIDGE__",
            {
                value: true,
                enumerable: false,
                configurable: false
            }
        );


        ////////////////////////////////////////////////////////////
        //  INSTALL EARLY BRIDGE
        ////////////////////////////////////////////////////////////

        window.loadPage =
            earlyLoadPage;

    }


    ////////////////////////////////////////////////////////////
    //  ONE REQUEST ONLY
    //
    // EVERYTHING BELOW IS ALREADY INSIDE:
    //
    // pageLoader.bundle.js
    //
    // DO NOT ADD:
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
    // cssLoader.js
    // jsLoader.js
    // home.js
    // loaderCore.js
    // pageLoader.js
    //
    // NONE OF THEM ARE LOADED HERE.
    ////////////////////////////////////////////////////////////

    await loadScript(
        "main_js/bundles/pageLoader.bundle.js"
    );


    ////////////////////////////////////////////////////////////
    //  VERIFY CORE
    //
    // loaderCore.js MUST export:
    //
    // window.__PAGE_LOADER_CORE_LOAD_PAGE__
    ////////////////////////////////////////////////////////////

    if(
        typeof window.__PAGE_LOADER_CORE_LOAD_PAGE__ !==
        "function"
    ){

        throw new Error(
            "PageLoader core function is missing"
        );

    }


    ////////////////////////////////////////////////////////////
    //  VERIFY REAL FUNCTION
    //
    // pageLoader.js should create:
    //
    // window.__REAL_LOAD_PAGE__
    //
    // pointing to the REAL core.
    ////////////////////////////////////////////////////////////

    if(
        typeof window.__REAL_LOAD_PAGE__ !==
        "function"
    ){

        throw new Error(
            "PageLoader real function is missing"
        );

    }


    ////////////////////////////////////////////////////////////
    //  RECURSION CHECK
    //
    // REAL CORE MUST NEVER BE:
    //
    // window.loadPage
    //
    // because window.loadPage is the public bridge.
    ////////////////////////////////////////////////////////////

    if(
        window.__REAL_LOAD_PAGE__ ===
        window.loadPage
    ){

        throw new Error(
            "PageLoader bridge recursion detected"
        );

    }


    ////////////////////////////////////////////////////////////
    //  CORE MATCH
    //
    // Both references MUST point to the same
    // actual loaderCore.js function.
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
    //  VERIFY READY
    ////////////////////////////////////////////////////////////

    if(
        !window.__PAGE_LOADER_READY__
    ){

        throw new Error(
            "PageLoader bundle loaded but system is not READY"
        );

    }


    ////////////////////////////////////////////////////////////
    //  PAGELOADER READY
    ////////////////////////////////////////////////////////////

    console.log(
        " PAGELOADER BUNDLE READY"
    );


    ////////////////////////////////////////////////////////////
    //  FEED BUNDLE
    //
    // Feed is independent from PageLoader.
    ////////////////////////////////////////////////////////////

    await loadScript(
        "main_js/bundles/feed.bundle.js"
    );


    ////////////////////////////////////////////////////////////
    //  FEED READY
    ////////////////////////////////////////////////////////////

    console.log(
        " FEED SYSTEM READY"
    );


    ////////////////////////////////////////////////////////////
    //  CRITICAL BOOT COMPLETE
    ////////////////////////////////////////////////////////////

    console.log(
        " CRITICAL BOOT COMPLETE"
    );


    return true;

}
```

---

Generated by MiniGram MD Intelligence V6.
