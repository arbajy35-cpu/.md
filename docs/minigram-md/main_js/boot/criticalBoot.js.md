# main_js/boot/criticalBoot.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/criticalBoot.js` |
| Extension | `.js` |
| Size | 10407 bytes |
| Lines | 453 |
| SHA-256 | `aa434573ea0ddc8368623474a706a837c13adca4738d66c2361d246eab347127` |

## Project Understanding

AI analysis unavailable.

## Architecture Context

Architecture generated from local file relations.

## Dependencies

- None

## Used By

- None

## Relation Flow

```text
main_js/boot/criticalBoot.js
  ↓
  └─ No local dependencies
```

## AI Project Patterns

- None

## AI Warnings

- None

---

# Original Source Code

The following content is copied directly from:

`/storage/emulated/0/MINIGRAM1/main_js/boot/criticalBoot.js`

No AI rewriting was performed on the source code.

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

Generated automatically.
