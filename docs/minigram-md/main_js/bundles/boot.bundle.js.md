# main_js/bundles/boot.bundle.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/bundles/boot.bundle.js` |
| Extension | `.js` |
| Size | 43724 bytes |
| Lines | 2000 |
| SHA-256 | `daee2bac0c8ab5c2bae5cb8f3ea8b6e4fa929891a6b75940b12e3ac29d9eea72` |

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
main_js/bundles/boot.bundle.js
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

`/storage/emulated/0/MINIGRAM1/main_js/bundles/boot.bundle.js`

No AI rewriting was performed on the source code.

```javascript


/*
==================================================
🚀 MINIGRAM BUNDLE
FILE: boot.bundle.js
GENERATED: 2026-08-29T07:28:40.498Z
SOURCE FILES: 14
==================================================
*/



/* =================================================
   FILE: main_js/boot/performance.js
   ================================================= */

//////////////////////////////////////////////////
// ⏱️ MINIGRAM BOOT PERFORMANCE
//////////////////////////////////////////////////

window.__MINIGRAM_T0 =
    performance.now();

window.__MINIGRAM_TIMINGS =
    window.__MINIGRAM_TIMINGS || {};

/* =================================================
   END: main_js/boot/performance.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/idle.js
   ================================================= */

//////////////////////////////////////////////////
// 💤 MINIGRAM IDLE FALLBACK
//////////////////////////////////////////////////

window.requestIdleCallback =
    window.requestIdleCallback ||
    function(cb){

        return setTimeout(
            () => cb({
                timeRemaining: () => 0
            }),
            1
        );

    };

/* =================================================
   END: main_js/boot/idle.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/scriptCache.js
   ================================================= */

//////////////////////////////////////////////////
// 📦 MINIGRAM SCRIPT CACHE
//////////////////////////////////////////////////

window.__LOADED_SCRIPTS =
    window.__LOADED_SCRIPTS ||
    new Map();

window.__LOADING_SCRIPTS =
    window.__LOADING_SCRIPTS ||
    new Map();

/* =================================================
   END: main_js/boot/scriptCache.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/scriptLoader.js
   ================================================= */

//////////////////////////////////////////////////
// 📜 MINIGRAM SCRIPT LOADER
// RACE-SAFE VERSION
//////////////////////////////////////////////////

function loadScript(
    src,
    force = false
){

    if(!src){

        return Promise.reject(
            new Error(
                "Missing script source"
            )
        );

    }


    //////////////////////////////////////////////////
    // FORCE RELOAD
    //////////////////////////////////////////////////

    if(force){

        const old =
            document.querySelector(
                `script[data-src="${src}"]`
            );

        old?.remove();

        window.__LOADED_SCRIPTS
            .delete(src);

        window.__LOADING_SCRIPTS
            .delete(src);

    }


    //////////////////////////////////////////////////
    // ALREADY LOADED
    //////////////////////////////////////////////////

    if(
        window.__LOADED_SCRIPTS
            .has(src)
    ){

        return Promise.resolve();

    }


    //////////////////////////////////////////////////
    // CURRENTLY LOADING
    //////////////////////////////////////////////////

    if(
        window.__LOADING_SCRIPTS
            .has(src)
    ){

        return window.__LOADING_SCRIPTS
            .get(src);

    }


    //////////////////////////////////////////////////
    // CREATE PROMISE
    //////////////////////////////////////////////////

    const promise =
        new Promise(
            (resolve,reject)=>{

                //////////////////////////////////////////////////
                // EXISTING SCRIPT
                //////////////////////////////////////////////////

                const existing =
                    document.querySelector(
                        `script[data-src="${src}"]`
                    );


                if(existing){

                    //////////////////////////////////////////////////
                    // ALREADY COMPLETED
                    //////////////////////////////////////////////////

                    if(
                        existing.dataset.loaded ===
                        "true"
                    ){

                        window.__LOADED_SCRIPTS
                            .set(src,true);

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        resolve();

                        return;

                    }


                    //////////////////////////////////////////////////
                    // EXISTING SCRIPT SUCCESS
                    //////////////////////////////////////////////////

                    const done = () => {

                        existing.dataset.loaded =
                            "true";

                        window.__LOADED_SCRIPTS
                            .set(src,true);

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        resolve();

                    };


                    //////////////////////////////////////////////////
                    // EXISTING SCRIPT ERROR
                    //////////////////////////////////////////////////

                    const fail = () => {

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        reject(
                            new Error(
                                "Failed to load: " +
                                src
                            )
                        );

                    };


                    existing.addEventListener(
                        "load",
                        done,
                        {once:true}
                    );


                    existing.addEventListener(
                        "error",
                        fail,
                        {once:true}
                    );


                    return;

                }


                //////////////////////////////////////////////////
                // CREATE NEW SCRIPT
                //////////////////////////////////////////////////

                const s =
                    document.createElement(
                        "script"
                    );


                s.src =
                    src.includes("?")
                        ? src + "&v=1"
                        : src + "?v=1";


                s.dataset.src =
                    src;


                //////////////////////////////////////////////////
                // ASYNC
                //////////////////////////////////////////////////

                s.async = true;


                //////////////////////////////////////////////////
                // SUCCESS
                //////////////////////////////////////////////////

                s.onload = () => {

                    s.dataset.loaded =
                        "true";

                    window.__LOADED_SCRIPTS
                        .set(src,true);

                    window.__LOADING_SCRIPTS
                        .delete(src);

                    resolve();

                };


                //////////////////////////////////////////////////
                // ERROR
                //////////////////////////////////////////////////

                s.onerror = () => {

                    window.__LOADING_SCRIPTS
                        .delete(src);

                    reject(
                        new Error(
                            "Failed to load: " +
                            src
                        )
                    );

                };


                //////////////////////////////////////////////////
                // APPEND
                //////////////////////////////////////////////////

                (
                    document.head ||
                    document.body ||
                    document.documentElement
                ).appendChild(s);

            }
        );


    //////////////////////////////////////////////////
    // STORE PROMISE
    //////////////////////////////////////////////////

    window.__LOADING_SCRIPTS
        .set(
            src,
            promise
        );


    //////////////////////////////////////////////////
    // CLEANUP
    //////////////////////////////////////////////////

    promise.finally(()=>{

        if(
            window.__LOADING_SCRIPTS
                .get(src) === promise
        ){

            window.__LOADING_SCRIPTS
                .delete(src);

        }

    }).catch(()=>{});


    return promise;

}


//////////////////////////////////////////////////
// 🚀 PUBLIC BOOT LOADER
//////////////////////////////////////////////////

window.loadBootScript =
    loadScript;

/* =================================================
   END: main_js/boot/scriptLoader.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/device.js
   ================================================= */

//////////////////////////////////////////////////
// 📱 MINIGRAM DEVICE DETECTION
//////////////////////////////////////////////////

window.IS_LOW_END =

    (
        navigator.deviceMemory &&
        navigator.deviceMemory <= 4
    ) ||

    (
        navigator.hardwareConcurrency &&
        navigator.hardwareConcurrency <= 4
    );

/* =================================================
   END: main_js/boot/device.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/network.js
   ================================================= */

//////////////////////////////////////////////////
// 🌐 MINIGRAM NETWORK DETECTION
//////////////////////////////////////////////////

window.NETWORK_TYPE =
    navigator.connection?.effectiveType ||
    "unknown";

/* =================================================
   END: main_js/boot/network.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/skeleton.js
   ================================================= */

//////////////////////////////////////////////////
// ⚡ MINIGRAM INSTANT SKELETON
//////////////////////////////////////////////////

function initInstantSkeleton(){

    //////////////////////////////////////////////////
    // NEVER RECREATE
    //////////////////////////////////////////////////

    if(
        window.__INSTANT_SKELETON__
    ){

        return;

    }


    const main =
        document.getElementById(
            "mainContent"
        );


    if(!main){

        return;

    }


    //////////////////////////////////////////////////
    // STATE
    //////////////////////////////////////////////////

    window.__INSTANT_SKELETON__ =
        true;

    window.__INSTANT_SKELETON_ACTIVE__ =
        true;


    //////////////////////////////////////////////////
    // ONLY IF EMPTY
    //////////////////////////////////////////////////

    if(
        main.childElementCount === 0
    ){

        main.innerHTML = `

            <div
                id="instantSkeleton"
                class="instant-skeleton"
                aria-hidden="true"
            >

                <div class="skel-stories">

                    ${Array.from(
                        {length:5},
                        () => `
                            <div class="skel-story"></div>
                        `
                    ).join("")}

                </div>


                ${Array.from(
                    {length:2},
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

    }

}

/* =================================================
   END: main_js/boot/skeleton.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/shell.js
   ================================================= */

//////////////////////////////////////////////////
// ⚡ MINIGRAM SHELL
//////////////////////////////////////////////////

let SHELL_READY =
    false;


//////////////////////////////////////////////////
// 🚀 PREPARE INSTANT SHELL
//////////////////////////////////////////////////

function prepareInstantShell(){

    //////////////////////////////////////////////////
    // PREVENT DUPLICATE WORK
    //////////////////////////////////////////////////

    if(SHELL_READY){

        return;

    }


    const appbar =
        document.getElementById(
            "appbar"
        );

    const nav =
        document.getElementById(
            "bottomNav"
        );

    const main =
        document.getElementById(
            "mainContent"
        );


    //////////////////////////////////////////////////
    // SHOW APP SHELL
    //////////////////////////////////////////////////

    appbar?.classList.remove(
        "hidden"
    );

    nav?.classList.remove(
        "hidden"
    );


    //////////////////////////////////////////////////
    // STABLE MAIN VISIBILITY
    //////////////////////////////////////////////////

    if(main){

        main.style.visibility =
            "visible";

        main.style.opacity =
            "1";

    }


    //////////////////////////////////////////////////
    // ICONS
    //////////////////////////////////////////////////

    try{

        window.initIcons?.();

    }catch(e){}


    //////////////////////////////////////////////////
    // REMOVE GLOBAL LOADER
    //////////////////////////////////////////////////

    document
        .getElementById(
            "loader"
        )
        ?.remove();


    SHELL_READY =
        true;


    //////////////////////////////////////////////////
    // SHELL TIMING
    //////////////////////////////////////////////////

    const shellTime =
        performance.now() -
        window.__MINIGRAM_T0;


    window.__MINIGRAM_TIMINGS
        .shell =
        shellTime;


    console.log(
        `⚡ FIRST UI SHELL READY: ${
            shellTime.toFixed(2)
        } ms`
    );


    //////////////////////////////////////////////////
    // ACTUAL NEXT FRAME
    //////////////////////////////////////////////////

    requestAnimationFrame(()=>{

        requestAnimationFrame(()=>{

            const painted =
                performance.now() -
                window.__MINIGRAM_T0;


            window.__MINIGRAM_TIMINGS
                .firstPaint =
                painted;


            console.log(
                `🎨 FIRST UI FRAME: ${
                    painted.toFixed(2)
                } ms`
            );

        });

    });

}

/* =================================================
   END: main_js/boot/shell.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/home.js
   ================================================= */

//////////////////////////////////////////////////
// 🏠 MINIGRAM HOME START
//////////////////////////////////////////////////

function startHome(){

    //////////////////////////////////////////////////
    // HOME IS CRITICAL
    //////////////////////////////////////////////////

    Promise.resolve().then(async()=>{

        try{

            //////////////////////////////////////////////////
            // CONFIG
            //////////////////////////////////////////////////

            if(
                typeof window.ensurePageConfig ===
                "function"
            ){

                await window.ensurePageConfig(
                    "home"
                );

            }


            //////////////////////////////////////////////////
            // LOAD HOME
            //////////////////////////////////////////////////

            if(
                typeof window.loadPage ===
                "function"
            ){

                await window.loadPage(
                    "home",
                    false
                );


                //////////////////////////////////////////////////
                // HOME READY TIMING
                //////////////////////////////////////////////////

                const homeTime =
                    performance.now() -
                    window.__MINIGRAM_T0;


                window.__MINIGRAM_TIMINGS
                    .home =
                    homeTime;


                console.log(
                    `🏠 HOME / FEED READY: ${
                        homeTime.toFixed(2)
                    } ms`
                );


            }else{

                console.error(
                    "❌ loadPage missing"
                );

            }

        }catch(e){

            console.error(
                "❌ HOME LOAD FAIL:",
                e
            );

        }

    });

}

/* =================================================
   END: main_js/boot/home.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/auth.js
   ================================================= */

//////////////////////////////////////////////////
// 🔐 MINIGRAM AUTH
//////////////////////////////////////////////////

async function checkAuth(){

    const client =
        window.supabaseClient ||
        window.db;


    //////////////////////////////////////////////////
    // CLIENT CHECK
    //////////////////////////////////////////////////

    if(!client){

        console.error(
            "❌ SUPABASE CLIENT NOT FOUND"
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }


    //////////////////////////////////////////////////
    // AUTH API CHECK
    //////////////////////////////////////////////////

    if(
        !client.auth ||
        typeof client.auth.getSession !==
        "function"
    ){

        console.error(
            "❌ SUPABASE AUTH API NOT AVAILABLE"
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }


    //////////////////////////////////////////////////
    // SESSION
    //////////////////////////////////////////////////

    try{

        const {
            data,
            error
        } =
            await client.auth.getSession();


        //////////////////////////////////////////////////
        // ERROR
        //////////////////////////////////////////////////

        if(error){

            console.error(
                "❌ AUTH SESSION ERROR:",
                error
            );

            window.location.replace(
                "signup/signup.html"
            );

            return false;

        }


        //////////////////////////////////////////////////
        // NO SESSION
        //////////////////////////////////////////////////

        if(!data?.session){

            window.location.replace(
                "login/login.html"
            );

            return false;

        }


        //////////////////////////////////////////////////
        // AUTHENTICATED
        //////////////////////////////////////////////////

        return true;


    }catch(e){

        console.error(
            "🔥 AUTH CHECK FAILED:",
            e
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }

}

/* =================================================
   END: main_js/boot/auth.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/criticalBoot.js
   ================================================= */

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

/* =================================================
   END: main_js/boot/criticalBoot.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/heavySystems.js
   ================================================= */

//////////////////////////////////////////////////
//  MINIGRAM HEAVY SYSTEMS V2
// IDLE + BUNDLE FIRST
//
// IMPORTANT:
// Heavy systems MUST NOT block critical boot.
//
// CRITICAL:
// - No PageLoader dependency here
// - No duplicate loading
// - Bundle-first
// - Slow network protection
// - Idle loading
// - Safe failure
//////////////////////////////////////////////////


console.log(
    " HEAVY SYSTEMS V2 READY"
);


//////////////////////////////////////////////////
//  STATE
//////////////////////////////////////////////////

window.__HEAVY_SYSTEMS_STARTED__ =
    !!window.__HEAVY_SYSTEMS_STARTED__;


window.__HEAVY_SYSTEMS_READY__ =
    !!window.__HEAVY_SYSTEMS_READY__;


window.__HEAVY_SYSTEMS_PROMISE__ =
    window.__HEAVY_SYSTEMS_PROMISE__ || null;


//////////////////////////////////////////////////
//  SAFE SCRIPT LOADER
//////////////////////////////////////////////////

function loadHeavyScript(src){

    if(
        typeof window.loadScript !==
        "function"
    ){

        return Promise.reject(
            new Error(
                "loadScript() unavailable"
            )
        );

    }


    return window.loadScript(src);

}


//////////////////////////////////////////////////
//  NETWORK CHECK
//////////////////////////////////////////////////

function isSlowNetwork(){

    const type =
        window.NETWORK_TYPE;


    return (
        type === "slow-2g" ||
        type === "2g"
    );

}


//////////////////////////////////////////////////
//  LOAD ADAPTIVE
//////////////////////////////////////////////////

async function loadAdaptiveBundle(){

    if(
        window.__ADAPTIVE_BUNDLE_READY__
    ){

        return true;

    }


    await loadHeavyScript(
        "main_js/bundles/adaptive.bundle.js"
    );


    window.__ADAPTIVE_BUNDLE_READY__ =
        true;


    console.log(
        " ADAPTIVE BUNDLE READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  REALTIME
//////////////////////////////////////////////////

async function loadRealtimeSystems(){

    if(
        window.__REALTIME_SYSTEM_READY__
    ){

        return true;

    }


    if(
        !navigator.onLine
    ){

        console.log(
            " REALTIME SKIPPED: OFFLINE"
        );

        return false;

    }


    if(
        isSlowNetwork()
    ){

        console.log(
            " REALTIME SKIPPED: SLOW NETWORK"
        );

        return false;

    }


    await Promise.all([

        loadHeavyScript(
            "main_js/realtime.js"
        ),

        loadHeavyScript(
            "main_js/pageloader/realtime.js"
        )

    ]);


    window.__REALTIME_SYSTEM_READY__ =
        true;


    console.log(
        " REALTIME SYSTEM READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  FPS MONITOR
//////////////////////////////////////////////////

async function loadFPSMonitor(){

    if(
        !window.DEBUG_MODE
    ){

        return false;

    }


    if(
        window.__FPS_MONITOR_READY__
    ){

        return true;

    }


    await loadHeavyScript(
        "main_js/debug/fpsMonitor.js"
    );


    window.__FPS_MONITOR_READY__ =
        true;


    console.log(
        " FPS MONITOR READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  START HEAVY SYSTEMS
//////////////////////////////////////////////////

function scheduleHeavySystems(){

    //////////////////////////////////////////////////
    // DUPLICATE PROTECTION
    //////////////////////////////////////////////////

    if(
        window.__HEAVY_SYSTEMS_PROMISE__
    ){

        return window.__HEAVY_SYSTEMS_PROMISE__;

    }


    //////////////////////////////////////////////////
    // ALREADY STARTED
    //////////////////////////////////////////////////

    if(
        window.__HEAVY_SYSTEMS_STARTED__
    ){

        return Promise.resolve(
            true
        );

    }


    window.__HEAVY_SYSTEMS_STARTED__ =
        true;


    //////////////////////////////////////////////////
    // IDLE SCHEDULER
    //////////////////////////////////////////////////

    const start =
        () => {

            window.__HEAVY_SYSTEMS_PROMISE__ =
                (async()=>{

                    try{

                        console.log(
                            " HEAVY SYSTEMS START"
                        );


                        //////////////////////////////////////////////////
                        // ADAPTIVE
                        //////////////////////////////////////////////////

                        await loadAdaptiveBundle();


                        //////////////////////////////////////////////////
                        // DEBUG FPS
                        //////////////////////////////////////////////////

                        await loadFPSMonitor();


                        //////////////////////////////////////////////////
                        // REALTIME
                        //////////////////////////////////////////////////

                        await loadRealtimeSystems();


                        //////////////////////////////////////////////////
                        // READY
                        //////////////////////////////////////////////////

                        window.__HEAVY_SYSTEMS_READY__ =
                            true;


                        console.log(
                            " HEAVY SYSTEMS READY"
                        );


                        return true;


                    }catch(error){

                        console.error(
                            " HEAVY SYSTEM ERROR:",
                            error
                        );


                        //////////////////////////////////////////////////
                        // IMPORTANT:
                        // Heavy system failure MUST NOT
                        // break the application.
                        //////////////////////////////////////////////////

                        return false;

                    }

                })();


            return window.__HEAVY_SYSTEMS_PROMISE__;

        };


    //////////////////////////////////////////////////
    // REQUEST IDLE CALLBACK
    //////////////////////////////////////////////////

    if(
        typeof window.requestIdleCallback ===
        "function"
    ){

        requestIdleCallback(
            start,
            {
                timeout:3000
            }
        );

    }else{

        setTimeout(
            start,
            100
        );

    }


    return window.__HEAVY_SYSTEMS_PROMISE__;

}


//////////////////////////////////////////////////
//  PUBLIC API
//////////////////////////////////////////////////

window.scheduleHeavySystems =
    scheduleHeavySystems;


//////////////////////////////////////////////////
//  READY
//////////////////////////////////////////////////

console.log(
    " Heavy Systems V2: Bundle First"
);

console.log(
    " Heavy Systems: Idle Loading"
);

console.log(
    " Heavy Systems: Failure Safe"
);

/* =================================================
   END: main_js/boot/heavySystems.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/errors.js
   ================================================= */

//////////////////////////////////////////////////
// 💀 MINIGRAM GLOBAL ERROR LOGGER
//////////////////////////////////////////////////

window.addEventListener(
    "error",
    e => {

        console.error(
            "💀 ERROR:",
            e.filename,
            e.message,
            "LINE:",
            e.lineno
        );

    }
);


//////////////////////////////////////////////////
// 💀 MINIGRAM PROMISE LOGGER
//////////////////////////////////////////////////

window.addEventListener(
    "unhandledrejection",
    e => {

        console.error(
            "💀 UNHANDLED PROMISE:",
            e.reason
        );

    }
);

/* =================================================
   END: main_js/boot/errors.js
   ================================================= */



/* =================================================
   FILE: main_js/boot/boot.js
   ================================================= */

//////////////////////////////////////////////////
// 🚀 MINIGRAM BOOT
// FAST + STABLE + SMOOTH FIRST PAINT
//
// ORCHESTRATOR
//////////////////////////////////////////////////

console.log(
    "🚀 MINIGRAM BOOT START"
);


//////////////////////////////////////////////////
// 🚀 START APP
//////////////////////////////////////////////////

function startApp(){

    //////////////////////////////////////////////////
    // SHELL
    //////////////////////////////////////////////////

    prepareInstantShell();


    //////////////////////////////////////////////////
    // HOME
    //////////////////////////////////////////////////

    startHome();

}


//////////////////////////////////////////////////
// 🚀 MAIN BOOT
//////////////////////////////////////////////////

async function boot(){

    try{

        //////////////////////////////////////////////////
        // INSTANT SKELETON
        //////////////////////////////////////////////////

        initInstantSkeleton();


        //////////////////////////////////////////////////
        // FIRST SHELL
        //////////////////////////////////////////////////

        prepareInstantShell();


        //////////////////////////////////////////////////
        // CRITICAL SYSTEMS
        //////////////////////////////////////////////////

        const authenticated =
            await loadCriticalBoot();


        //////////////////////////////////////////////////
        // AUTH FAILED
        //////////////////////////////////////////////////

        if(!authenticated){

            return;

        }


        //////////////////////////////////////////////////
        // HOME
        //////////////////////////////////////////////////

        startApp();


        //////////////////////////////////////////////////
        // HEAVY SYSTEMS
        // DELAYED UNTIL BROWSER IS IDLE
        //////////////////////////////////////////////////

        scheduleHeavySystems();


        //////////////////////////////////////////////////
        // CRITICAL BOOT COMPLETE
        //////////////////////////////////////////////////

        const bootTime =
            performance.now() -
            window.__MINIGRAM_T0;


        window.__MINIGRAM_TIMINGS
            .boot =
            bootTime;


        console.log(
            `🎉 CRITICAL BOOT COMPLETE: ${
                bootTime.toFixed(2)
            } ms`
        );


    }catch(e){

        console.error(
            "🔥 BOOT CRASH:",
            e
        );

    }

}


//////////////////////////////////////////////////
// 🚀 START
//////////////////////////////////////////////////

if(
    document.readyState ===
    "loading"
){

    document.addEventListener(
        "DOMContentLoaded",
        boot,
        {once:true}
    );

}else{

    boot();

}

/* =================================================
   END: main_js/boot/boot.js
   ================================================= */


```

---

Generated automatically.
