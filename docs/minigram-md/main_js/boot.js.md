# main_js/boot.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/boot.js` |
| Extension | `.js` |
| Bytes | 25962 |
| Lines | 1222 |
| SHA-256 | `afdeabf54270ea02ec7e891f7c99c5f3879d00aa05f155f5aab1766bb37a411f` |
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
and 3 consumers.

## 5. Dependencies

- None

## 6. Used By

- `CRITICAL_ERRORS_REPORT.md`
- `index(Copy).html`
- `report.json`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `loadScript`
- `prepareInstantShell`
- `startHome`
- `checkAuth`
- `startApp`
- `boot`
- `old`
- `promise`
- `existing`
- `done`
- `fail`
- `s`
- `main`
- `SHELL_READY`
- `appbar`
- `nav`
- `shellTime`
- `painted`
- `homeTime`
- `client`
- `corePromise`
- `configPromise`
- `supabaseLibPromise`
- `authenticated`
- `slowNetwork`
- `bootTime`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **LOW** — Duplicate Filename: boot.js appears in 3 locations

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

`/storage/emulated/0/MINIGRAM1/main_js/boot.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
// 🚀 MINIGRAM BOOT
// FAST + STABLE + SMOOTH FIRST PAINT
//
// FEATURES:
// - Race-safe script loader
// - Instant skeleton
// - No duplicate shell initialization
// - First-paint timing
// - Home-ready timing
// - Stable visibility
// - Heavy systems delayed
//////////////////////////////////////////////////

console.log("🚀 MINIGRAM BOOT START");


//////////////////////////////////////////////////
// ⏱️ PERFORMANCE TIMER
//////////////////////////////////////////////////

window.__MINIGRAM_T0 =
    performance.now();

window.__MINIGRAM_TIMINGS =
    window.__MINIGRAM_TIMINGS || {};


//////////////////////////////////////////////////
// 💤 IDLE FALLBACK
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


//////////////////////////////////////////////////
// 📦 SCRIPT CACHE
//////////////////////////////////////////////////

window.__LOADED_SCRIPTS =
    window.__LOADED_SCRIPTS ||
    new Map();

window.__LOADING_SCRIPTS =
    window.__LOADING_SCRIPTS ||
    new Map();


//////////////////////////////////////////////////
// 📜 SCRIPT LOADER
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


                /*
                 * Async scripts are intentionally
                 * loaded independently.
                 */

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


                /*
                 * Append as soon as possible.
                 */

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


    /*
     * Prevent stale promise entries
     * after success/failure.
     */

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


window.loadBootScript =
    loadScript;


//////////////////////////////////////////////////
// 📱 DEVICE
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


//////////////////////////////////////////////////
// 🌐 NETWORK
//////////////////////////////////////////////////

window.NETWORK_TYPE =
    navigator.connection?.effectiveType ||
    "unknown";


//////////////////////////////////////////////////
// ⚡ INSTANT SKELETON
//////////////////////////////////////////////////

(function(){

    /*
     * Never recreate the skeleton.
     */

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


    window.__INSTANT_SKELETON__ =
        true;

    window.__INSTANT_SKELETON_ACTIVE__ =
        true;


    /*
     * Only inject if main is actually empty.
     *
     * This prevents accidental replacement
     * of HTML already rendered by index.html.
     */

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

})();


//////////////////////////////////////////////////
// ⚡ SHELL
//////////////////////////////////////////////////

let SHELL_READY =
    false;


function prepareInstantShell(){

    /*
     * Prevent repeated shell work.
     */

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

        /*
         * Don't animate the whole main container.
         * That can cause feed flicker during replacement.
         */

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
    // REMOVE GLOBAL LOADER ONCE
    //////////////////////////////////////////////////

    document
        .getElementById(
            "loader"
        )
        ?.remove();


    SHELL_READY =
        true;


    //////////////////////////////////////////////////
    // FIRST SHELL TIMING
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


//////////////////////////////////////////////////
// 🏠 START HOME
//////////////////////////////////////////////////

function startHome(){

    /*
     * Home is critical.
     * NEVER delay it with idle callback.
     */

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
            // LOAD PAGE
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


//////////////////////////////////////////////////
// 🔐 AUTH
//////////////////////////////////////////////////

async function checkAuth(){

    const client =
        window.supabaseClient ||
        window.db;


    if(!client){

        console.error(
            "❌ SUPABASE CLIENT NOT FOUND"
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }


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


    try{

        const {
            data,
            error
        } =
            await client.auth.getSession();


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


        if(!data?.session){

            window.location.replace(
                "login/login.html"
            );

            return false;

        }


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


//////////////////////////////////////////////////
// 🚀 START APP
//////////////////////////////////////////////////

function startApp(){

    /*
     * prepareInstantShell() is now
     * idempotent, so calling it here
     * is safe.
     */

    prepareInstantShell();

    startHome();

}


//////////////////////////////////////////////////
// 🚀 MAIN BOOT
//////////////////////////////////////////////////

async function boot(){

    try{

        //////////////////////////////////////////////////
        // FIRST PAINT
        //////////////////////////////////////////////////

        prepareInstantShell();


        //////////////////////////////////////////////////
        // CORE + CONFIG + SUPABASE LIB
        // ALL START TOGETHER
        //////////////////////////////////////////////////

        const corePromise =
            Promise.all([

                loadScript(
                    "main_js/bundles/core.bundle.js"
                ),

                loadScript(
                    "main_js/bundles/ui.bundle.js"
                )

            ]);


        const configPromise =
            loadScript(
                "main_js/pageloader/config.js"
            );


        const supabaseLibPromise =
            loadScript(
                "https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"
            );


        //////////////////////////////////////////////////
        // WAIT CRITICAL BOOT
        //////////////////////////////////////////////////

        await Promise.all([

            corePromise,
            configPromise,
            supabaseLibPromise

        ]);


        //////////////////////////////////////////////////
        // CONFIG + SUPABASE CLIENT
        //////////////////////////////////////////////////

        await Promise.all([

            loadScript(
                "main_js/config_Loader.js"
            ),

            loadScript(
                "supabase.js"
            )

        ]);


        //////////////////////////////////////////////////
        // AUTH
        //////////////////////////////////////////////////

        const authenticated =
            await checkAuth();


        if(!authenticated){

            return;

        }


        //////////////////////////////////////////////////
        // PAGELOADER CORE
        //////////////////////////////////////////////////

        await Promise.all([

            loadScript(
                "main_js/pageLoader_function/state.js"
            ),

            loadScript(
                "main_js/pageLoader_function/pathUtils.js"
            ),

            loadScript(
                "main_js/pageLoader_function/safeRun.js"
            )

        ]);


        //////////////////////////////////////////////////
        // PAGELOADER DEPENDENCIES
        //////////////////////////////////////////////////

        await Promise.all([

            loadScript(
                "main_js/pageLoader_function/cacheManager.js"
            ),

            loadScript(
                "main_js/pageLoader_function/htmlFetcher.js"
            ),

            loadScript(
                "main_js/pageLoader_function/layoutManager.js"
            ),

            loadScript(
                "main_js/pageLoader_function/pageLifecycle.js"
            ),

            loadScript(
                "main_js/pageLoader_function/scrollManager.js"
            )

        ]);


        //////////////////////////////////////////////////
        // STABLE LOADERS
        //////////////////////////////////////////////////

        await Promise.all([

            loadScript(
                "main_js/pageloader/cssLoader.js"
            ),

            loadScript(
                "main_js/pageloader/jsLoader.js"
            ),

            loadScript(
                "main_js/pageloader/home.js"
            ),

            loadScript(
                "main_js/minigramPost.js"
            ),

            loadScript(
                "global/icons.js"
            )

        ]);


        //////////////////////////////////////////////////
        // MAIN PAGELOADER
        //////////////////////////////////////////////////

        await loadScript(
            "main_js/pageLoader.js"
        );


        //////////////////////////////////////////////////
        // DEBUGGER
        //////////////////////////////////////////////////

        await loadScript(
            "main_js/debugger.js"
        );


        //////////////////////////////////////////////////
        // OPTIONAL LOADER
        //////////////////////////////////////////////////

        loadScript(
            "main_js/pageloader/loader.js"
        ).catch(()=>{});


        //////////////////////////////////////////////////
        // 📰 CRITICAL FEED
        // MUST EXIST BEFORE HOME
        //////////////////////////////////////////////////

        await loadScript(
            "main_js/bundles/feed.bundle.js"
        );


        console.log(
            "📰 FEED SYSTEM READY"
        );


        //////////////////////////////////////////////////
        // 🏠 HOME NOW
        //////////////////////////////////////////////////

        startApp();


        //////////////////////////////////////////////////
        // HEAVY SYSTEMS
        // DELAYED UNTIL BROWSER IS IDLE
        //////////////////////////////////////////////////

        requestIdleCallback(
            async()=>{

                try{

                    //////////////////////////////////////////////////
                    // FPS MONITOR
                    //////////////////////////////////////////////////

                    if(
                        window.DEBUG_MODE
                    ){

                        await loadScript(
                            "main_js/debug/fpsMonitor.js"
                        );

                    }


                    //////////////////////////////////////////////////
                    // ADAPTIVE
                    //////////////////////////////////////////////////

                    await loadScript(
                        "main_js/bundles/adaptive.bundle.js"
                    );


                    //////////////////////////////////////////////////
                    // REALTIME
                    //////////////////////////////////////////////////

                    const slowNetwork =
                        window.NETWORK_TYPE ===
                            "slow-2g" ||

                        window.NETWORK_TYPE ===
                            "2g";


                    if(
                        navigator.onLine &&
                        !slowNetwork
                    ){

                        await Promise.all([

                            loadScript(
                                "main_js/realtime.js"
                            ),

                            loadScript(
                                "main_js/pageloader/realtime.js"
                            )

                        ]);

                    }

                }catch(e){

                    console.error(
                        "⚠️ IDLE SYSTEM ERROR:",
                        e
                    );

                }

            }
        );


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


//////////////////////////////////////////////////
// 💀 GLOBAL ERROR LOGGER
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
// 💀 PROMISE LOGGER
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
```

---

Generated by MiniGram MD Intelligence V6.
