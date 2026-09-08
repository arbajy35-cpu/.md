# main_js/pageloader(Copy).js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageloader(Copy).js` |
| Extension | `.js` |
| Bytes | 35989 |
| Lines | 2085 |
| SHA-256 | `d7370ae72e16711dfc5c0dfe3d9addd4289ac920ef52e6b2c1faab6bb867a4c9` |
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

- `getContainer`
- `nextTwoFrames`
- `markMetric`
- `loadWithRetry`
- `preparePreconnect`
- `getSkeleton`
- `hasInstantSkeleton`
- `hasInstantHomeShell`
- `removeSkeleton`
- `getValidCache`
- `saveCache`
- `applyPageUI`
- `showLoadError`
- `setupDelegation`
- `initializePageLoader`
- `MAIN_CONTAINER_ID`
- `MAX_RETRY`
- `CACHE_TTL`
- `MAX_CACHE_SIZE`
- `DOM`
- `nextFrame`
- `idle`
- `elapsed`
- `attempt`
- `origins`
- `urls`
- `u`
- `link`
- `resources`
- `config`
- `destroy`
- `cache`
- `oldestKey`
- `oldestTime`
- `cached`
- `old`
- `toast`
- `container`
- `pageId`
- `thisLoad`
- `abortController`
- `signal`
- `isStale`
- `checkAbort`
- `t0`
- `previousPage`
- `cacheTime`
- `skeletonAlreadyVisible`
- `instantHome`
- `cssPromise`
- `pluginPromise`
- `htmlPromise`
- `jsPromise`
- `homeReady`
- `homePaint`
- `html`
- `initFn`
- `post`
- `likeBtn`

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

`/storage/emulated/0/MINIGRAM1/main_js/pageloader(Copy).js`

It is NOT AI generated or rewritten.

```javascript
////////////////////////////////////////////////////////////
//  PAGE LOADER V12.0
// FAST + STABLE + SMOOTH HOME TRANSITION
//
// SINGLE SKELETON OWNER:
// boot.js creates the first skeleton.
// pageLoader.js NEVER creates a duplicate Home skeleton.
//
// FEATURES:
// - Abort race protection
// - Home retry
// - TTL cache
// - Smooth Home settle
// - First UI / Home timing
// - Skeleton preservation
// - Cache protection
//
// CONTRACT:
// loadPage(page, force)
// force MUST remain boolean.
////////////////////////////////////////////////////////////


console.log(
    " PAGE LOADER V12.0 FAST STABLE SMOOTH"
);


////////////////////////////////////////////////////////////
//  GLOBAL PERFORMANCE TIMER
////////////////////////////////////////////////////////////

window.__MINIGRAM_T0 =
    Number(window.__MINIGRAM_T0) ||
    performance.now();


window.__MINIGRAM_METRICS =
    window.__MINIGRAM_METRICS || {

        bootStart:
            window.__MINIGRAM_T0,

        firstShell:
            null,

        homeStart:
            null,

        homeReady:
            null,

        homePaint:
            null

    };


////////////////////////////////////////////////////////////
//  CONFIG
////////////////////////////////////////////////////////////

const MAIN_CONTAINER_ID =
    "mainContent";


const MAX_RETRY =
    1;


const CACHE_TTL =
    60000;


const MAX_CACHE_SIZE =
    10;


////////////////////////////////////////////////////////////
//  STATE
////////////////////////////////////////////////////////////

window.ACTIVE_PAGE_ID =
    Number(window.ACTIVE_PAGE_ID) || 0;


window.LOAD_ID =
    Number(window.LOAD_ID) || 0;


window.PAGE_CACHE =
    window.PAGE_CACHE ||
    new Map();


window.LOADING =
    false;


window.CURRENT_LOAD_ABORT =
    null;


window.CURRENT_PAGE =
    window.CURRENT_PAGE ||
    null;


window._page_resources =
    window._page_resources || {

        timers: [],
        intervals: [],
        observers: [],
        listeners: [],
        videos: []

    };


////////////////////////////////////////////////////////////
//  DOM
////////////////////////////////////////////////////////////

const DOM = {

    container:null

};


function getContainer(){

    if(
        DOM.container &&
        document.contains(
            DOM.container
        )
    ){

        return DOM.container;

    }


    DOM.container =
        document.getElementById(
            MAIN_CONTAINER_ID
        );


    return DOM.container;

}


////////////////////////////////////////////////////////////
//  HELPERS
////////////////////////////////////////////////////////////

const nextFrame = () =>
    new Promise(
        resolve =>
            requestAnimationFrame(
                resolve
            )
    );


async function nextTwoFrames(){

    await nextFrame();

    await nextFrame();

}


const idle = () =>
    new Promise(resolve => {

        if(
            typeof window.requestIdleCallback ===
            "function"
        ){

            window.requestIdleCallback(
                resolve
            );

        }else{

            setTimeout(
                resolve,
                50
            );

        }

    });


////////////////////////////////////////////////////////////
//  PERFORMANCE MARK
////////////////////////////////////////////////////////////

function markMetric(
    name
){

    const elapsed =
        performance.now() -
        window.__MINIGRAM_T0;


    window.__MINIGRAM_METRICS[
        name
    ] = elapsed;


    console.log(
        ` ${name}: ${elapsed.toFixed(2)} ms`
    );


    return elapsed;

}


////////////////////////////////////////////////////////////
//  RETRY
////////////////////////////////////////////////////////////

async function loadWithRetry(
    fn,
    signal
){

    for(
        let attempt = 0;
        attempt <= MAX_RETRY;
        attempt++
    ){

        if(
            signal?.aborted
        ){

            throw new DOMException(
                "Aborted",
                "AbortError"
            );

        }


        try{

            return await fn();

        }catch(err){

            if(
                err?.name ===
                "AbortError"
            ){

                throw err;

            }


            console.warn(
                ` LOAD RETRY ${
                    attempt + 1
                }/${MAX_RETRY + 1}`,
                err
            );


            if(
                attempt >= MAX_RETRY
            ){

                throw err;

            }

        }

    }

}


////////////////////////////////////////////////////////////
//  PRECONNECT
////////////////////////////////////////////////////////////

function preparePreconnect(){

    setTimeout(()=>{

        try{

            const origins =
                new Set();


            Object.values(
                window.PAGE_CONFIG || {}
            ).forEach(config=>{

                const urls = [

                    ...(config?.css || []),
                    ...(config?.js || []),
                    config?.html

                ];


                urls.forEach(url=>{

                    if(!url) return;


                    try{

                        const u =
                            new URL(
                                url,
                                location.href
                            );


                        if(
                            u.origin !==
                            location.origin
                        ){

                            origins.add(
                                u.origin
                            );

                        }

                    }catch{}

                });

            });


            origins.forEach(origin=>{

                if(
                    document.querySelector(
                        `link[rel="preconnect"][href="${origin}"]`
                    )
                ){

                    return;

                }


                const link =
                    document.createElement(
                        "link"
                    );


                link.rel =
                    "preconnect";


                link.href =
                    origin;


                link.crossOrigin =
                    "anonymous";


                document.head.appendChild(
                    link
                );

            });

        }catch{}

    },0);

}


////////////////////////////////////////////////////////////
//  FALLBACK SKELETON
////////////////////////////////////////////////////////////

function getSkeleton(){

    return `

        <div
            class="instant-skeleton"
            data-page-skeleton="true"
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
                {length:3},
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


////////////////////////////////////////////////////////////
//  INSTANT SKELETON DETECTION
////////////////////////////////////////////////////////////

function hasInstantSkeleton(
    container
){

    return !!(
        container &&
        (
            container.querySelector(
                "#instantSkeleton"
            ) ||

            container.querySelector(
                "[data-page-skeleton='true']"
            )
        )
    );

}


////////////////////////////////////////////////////////////
//  INSTANT HOME DETECTION
////////////////////////////////////////////////////////////

function hasInstantHomeShell(
    container
){

    return !!(
        container &&
        container.querySelector(
            "#homeShell"
        )
    );

}


////////////////////////////////////////////////////////////
//  SKELETON CLEANUP
////////////////////////////////////////////////////////////

function removeSkeleton(
    container
){

    if(!container){

        return;

    }


    container
        .querySelector(
            "#instantSkeleton"
        )
        ?.remove();


    container
        .querySelectorAll(
            "[data-page-skeleton='true']"
        )
        .forEach(el=>{

            if(
                el.id !==
                "instantSkeleton"
            ){

                el.remove();

            }

        });


    window.__INSTANT_SKELETON_ACTIVE__ =
        false;

}


////////////////////////////////////////////////////////////
//  CLEANUP
////////////////////////////////////////////////////////////

window.cleanupPage =
async function(oldPage){

    const resources =
        window._page_resources || {};


    (resources.timers || [])
        .forEach(timer=>{

            try{

                clearTimeout(
                    timer
                );

            }catch{}

        });


    (resources.intervals || [])
        .forEach(interval=>{

            try{

                clearInterval(
                    interval
                );

            }catch{}

        });


    (resources.observers || [])
        .forEach(observer=>{

            try{

                observer.disconnect();

            }catch{}

        });


    (resources.listeners || [])
        .forEach(item=>{

            try{

                item.el?.removeEventListener(
                    item.type,
                    item.fn
                );

            }catch{}

        });


    document
        .querySelectorAll(
            "video"
        )
        .forEach(video=>{

            try{

                video.pause();

            }catch{}

        });


    try{

        const config =
            window.PAGE_CONFIG?.[
                oldPage
            ];


        const destroy =
            config?.destroy;


        if(
            destroy &&
            window.FUNCTIONS?.[destroy]
        ){

            await window.FUNCTIONS[
                destroy
            ]();

        }

    }catch(e){

        console.warn(
            " Page destroy:",
            e
        );

    }


    window._page_resources = {

        timers:[],
        intervals:[],
        observers:[],
        listeners:[],
        videos:[]

    };

};


////////////////////////////////////////////////////////////
//  CACHE CLEANUP
////////////////////////////////////////////////////////////

window.cleanupCache =
function(){

    const cache =
        window.PAGE_CACHE;


    if(
        cache.size <=
        MAX_CACHE_SIZE
    ){

        return;

    }


    let oldestKey =
        null;


    let oldestTime =
        Infinity;


    for(
        const [key,value] of cache
    ){

        if(
            value?.time <
            oldestTime
        ){

            oldestTime =
                value.time;


            oldestKey =
                key;

        }

    }


    if(
        oldestKey !==
        null
    ){

        cache.delete(
            oldestKey
        );

    }

};


////////////////////////////////////////////////////////////
//  CACHE GET
////////////////////////////////////////////////////////////

function getValidCache(
    page,
    force
){

    if(force){

        return null;

    }


    const cached =
        window.PAGE_CACHE.get(
            page
        );


    if(!cached){

        return null;

    }


    if(
        Date.now() -
        cached.time >=
        CACHE_TTL
    ){

        window.PAGE_CACHE.delete(
            page
        );

        return null;

    }


    if(!cached.html){

        return null;

    }


    return cached;

}


////////////////////////////////////////////////////////////
//  CACHE SAVE
////////////////////////////////////////////////////////////

function saveCache(
    page,
    html
){

    if(!html){

        return;

    }


    window.PAGE_CACHE.set(
        page,
        {

            html:html,

            time:Date.now()

        }
    );


    window.cleanupCache?.();

}


////////////////////////////////////////////////////////////
//  APPLY UI
////////////////////////////////////////////////////////////

function applyPageUI(
    config,
    page
){

    try{

        window.applyLayout?.(
            config?.layout
        );

    }catch{}


    queueMicrotask(()=>{

        try{

            window.initIcons?.();

        }catch{}


        try{

            window.initNavigation?.();

        }catch{}

    });

}


////////////////////////////////////////////////////////////
//  ERROR
////////////////////////////////////////////////////////////

function showLoadError(
    page
){

    const old =
        document.querySelector(
            "[data-page-load-error]"
        );


    old?.remove();


    const toast =
        document.createElement(
            "div"
        );


    toast.dataset.pageLoadError =
        "true";


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
        >
            Retry
        </button>

    `;


    toast
        .querySelector(
            "button"
        )
        ?.addEventListener(
            "click",
            ()=>{

                toast.remove();


                window.loadPage(
                    page,
                    true
                );

            }
        );


    document.body.appendChild(
        toast
    );


    setTimeout(
        ()=>toast.remove(),
        4000
    );

}


////////////////////////////////////////////////////////////
//  MAIN LOAD PAGE
////////////////////////////////////////////////////////////

window.loadPage =
async function(
    page,
    force = false
){

    //////////////////////////////////////////////////////////
    // CONTRACT
    //////////////////////////////////////////////////////////

    if(
        typeof force !==
        "boolean"
    ){

        force =
            !!force;

    }


    //////////////////////////////////////////////////////////
    // CONTAINER
    //////////////////////////////////////////////////////////

    const container =
        getContainer();


    if(!container){

        console.error(
            " #mainContent not found"
        );

        return false;

    }


    //////////////////////////////////////////////////////////
    // SAME REQUEST
    //////////////////////////////////////////////////////////

    if(
        window.LOADING &&
        window.CURRENT_PAGE === page &&
        !force
    ){

        return true;

    }


    //////////////////////////////////////////////////////////
    // ABORT OLD
    //////////////////////////////////////////////////////////

    window.CURRENT_LOAD_ABORT
        ?.abort();


    //////////////////////////////////////////////////////////
    // GENERATION
    //////////////////////////////////////////////////////////

    const pageId =
        ++window.ACTIVE_PAGE_ID;


    const thisLoad =
        ++window.LOAD_ID;


    const abortController =
        new AbortController();


    window.CURRENT_LOAD_ABORT =
        abortController;


    const signal =
        abortController.signal;


    const isStale = () =>

        thisLoad !==
            window.LOAD_ID ||

        pageId !==
            window.ACTIVE_PAGE_ID ||

        signal.aborted;


    const checkAbort = () => {

        if(isStale()){

            throw new DOMException(
                "Aborted",
                "AbortError"
            );

        }

    };


    window.LOADING =
        true;


    const t0 =
        performance.now();


    const previousPage =
        window.CURRENT_PAGE;


    window.LAST_PAGE =
        previousPage;


    console.log(
        " LOAD PAGE:",
        page,
        "| FROM:",
        previousPage || "FIRST",
        "| FORCE:",
        force
    );


    try{

        ////////////////////////////////////////////////////////
        // CONFIG
        ////////////////////////////////////////////////////////

        await window.ensurePageConfig?.(
            page
        );


        checkAbort();


        const config =
            window.PAGE_CONFIG?.[
                page
            ];


        if(!config){

            throw new Error(
                `Invalid config: ${page}`
            );

        }


        ////////////////////////////////////////////////////////
        // CACHE
        ////////////////////////////////////////////////////////

        const cached =
            getValidCache(
                page,
                force
            );


        if(cached){

            container.innerHTML =
                cached.html;


            container.style.opacity =
                "1";


            window.CURRENT_PAGE =
                page;


            window.__INSTANT_SKELETON_ACTIVE__ =
                false;


            applyPageUI(
                config,
                page
            );


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


            idle().then(()=>{

                if(
                    !isStale()
                ){

                    window.applyAdaptive?.(
                        page
                    );

                }

            });


            const cacheTime =
                performance.now() -
                t0;


            console.log(
                ` CACHE HIT: ${page} | ${
                    Math.round(
                        cacheTime
                    )
                }ms`
            );


            return true;

        }


        ////////////////////////////////////////////////////////
        // CLEAN OLD PAGE
        ////////////////////////////////////////////////////////

        if(
            previousPage &&
            previousPage !== page
        ){

            await window.cleanupPage(
                previousPage
            );


            checkAbort();

        }


        ////////////////////////////////////////////////////////
        // SAVE SCROLL
        ////////////////////////////////////////////////////////

        if(previousPage){

            window.saveScroll?.(
                previousPage
            );

        }


        window.CURRENT_PAGE =
            page;


        ////////////////////////////////////////////////////////
        // SKELETON
        ////////////////////////////////////////////////////////

        const skeletonAlreadyVisible =
            hasInstantSkeleton(
                container
            );


        const instantHome =
            page ===
                "home" &&

            (
                hasInstantHomeShell(
                    container
                ) ||

                skeletonAlreadyVisible
            );


        if(
            !instantHome
        ){

            container.innerHTML =
                getSkeleton();

        }


        container.style.opacity =
            "1";


        ////////////////////////////////////////////////////////
        // LAYOUT
        ////////////////////////////////////////////////////////

        try{

            window.applyLayout?.(
                config.layout
            );

        }catch{}


        ////////////////////////////////////////////////////////
        //  HOME START
        ////////////////////////////////////////////////////////

        if(
            page ===
            "home"
        ){

            window.__MINIGRAM_METRICS
                .homeStart =
                performance.now() -
                window.__MINIGRAM_T0;


            console.log(
                ` HOME START: ${
                    window.__MINIGRAM_METRICS
                        .homeStart
                        .toFixed(2)
                } ms`
            );

        }


        ////////////////////////////////////////////////////////
        // CSS
        ////////////////////////////////////////////////////////

        const cssPromise =

            config.css?.length &&

            typeof window.loadCSS ===
            "function"

                ?

                window.loadCSS(

                    config.css.map(
                        window.fixPath ||
                        (x => x)
                    ),

                    {signal}

                )

                :

                Promise.resolve();


        ////////////////////////////////////////////////////////
        // PLUGINS
        ////////////////////////////////////////////////////////

        const pluginPromise =

            typeof window.loadPlugins ===
            "function"

                ?

                Promise.resolve(
                    window.loadPlugins(
                        config
                    )
                )

                :

                Promise.resolve();


        ////////////////////////////////////////////////////////
        // HTML
        ////////////////////////////////////////////////////////

        let htmlPromise =
            null;


        if(
            page !==
            "home"
        ){

            htmlPromise =
                loadWithRetry(

                    () =>
                        window.fetchHTML(
                            config.html,
                            {signal}
                        ),

                    signal

                );

        }


        ////////////////////////////////////////////////////////
        // JS
        ////////////////////////////////////////////////////////

        const jsPromise =

            page !==
                "home" &&

            config.js?.length &&

            typeof window.loadJS ===
            "function"

                ?

                window.loadJS(

                    config.js.map(
                        window.fixPath ||
                        (x => x)
                    ),

                    {signal}

                )

                :

                Promise.resolve();


        ////////////////////////////////////////////////////////
        //  HOME
        ////////////////////////////////////////////////////////

        if(
            page ===
            "home"
        ){

            //////////////////////////////////////////////////////
            // PLUGINS
            //////////////////////////////////////////////////////

            await pluginPromise;


            checkAbort();


            //////////////////////////////////////////////////////
            // HOME FUNCTION MUST EXIST
            //////////////////////////////////////////////////////

            if(
                typeof window.loadHome !==
                "function"
            ){

                throw new Error(
                    "loadHome() is not available"
                );

            }


            //////////////////////////////////////////////////////
            // HOME RETRY
            //////////////////////////////////////////////////////

            await loadWithRetry(

                async()=>{

                    checkAbort();


                    await window.loadHome(
                        container
                    );


                    checkAbort();

                },

                signal

            );


            //////////////////////////////////////////////////////
            // DOM SETTLE
            //
            // Give browser two frames to process
            // DOM/layout/paint before skeleton cleanup.
            //////////////////////////////////////////////////////

            await nextTwoFrames();


            checkAbort();


            //////////////////////////////////////////////////////
            // REMOVE SKELETON AFTER CONTENT SETTLES
            //////////////////////////////////////////////////////

            removeSkeleton(
                container
            );


            //////////////////////////////////////////////////////
            // HOME READY
            //////////////////////////////////////////////////////

            const homeReady =
                performance.now() -
                window.__MINIGRAM_T0;


            window.__MINIGRAM_METRICS
                .homeReady =
                homeReady;


            console.log(
                ` HOME CONTENT READY: ${
                    homeReady.toFixed(2)
                } ms`
            );


            //////////////////////////////////////////////////////
            // FINAL PAINT
            //////////////////////////////////////////////////////

            await nextFrame();


            checkAbort();


            const homePaint =
                performance.now() -
                window.__MINIGRAM_T0;


            window.__MINIGRAM_METRICS
                .homePaint =
                homePaint;


            console.log(
                ` HOME PAINT SETTLED: ${
                    homePaint.toFixed(2)
                } ms`
            );


            //////////////////////////////////////////////////////
            // SAVE ONLY AFTER SKELETON REMOVAL
            //////////////////////////////////////////////////////

            saveCache(
                page,
                container.innerHTML
            );


            window.__INSTANT_SKELETON_ACTIVE__ =
                false;

        }


        ////////////////////////////////////////////////////////
        // NON-HOME
        ////////////////////////////////////////////////////////

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


            saveCache(
                page,
                html

            );

        }


        ////////////////////////////////////////////////////////
        // WAIT RESOURCES
        ////////////////////////////////////////////////////////

        await Promise.all([

            cssPromise,

            jsPromise

        ]);


        checkAbort();


        ////////////////////////////////////////////////////////
        // UI
        ////////////////////////////////////////////////////////

        applyPageUI(
            config,
            page
        );


        ////////////////////////////////////////////////////////
        // NON-HOME INIT
        ////////////////////////////////////////////////////////

        if(
            page !==
            "home"
        ){

            await pluginPromise;


            checkAbort();


            await nextFrame();


            checkAbort();


            const initFn =
                window.FUNCTIONS?.[
                    config.init
                ];


            await initFn?.(
                pageId
            );

        }


        ////////////////////////////////////////////////////////
        // SCROLL
        ////////////////////////////////////////////////////////

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


        ////////////////////////////////////////////////////////
        // ADAPTIVE
        ////////////////////////////////////////////////////////

        idle().then(()=>{

            if(
                !isStale()
            ){

                window.applyAdaptive?.(
                    page
                );

            }

        });


        ////////////////////////////////////////////////////////
        // FINAL LOAD LOG
        ////////////////////////////////////////////////////////

        console.log(
            ` Loaded: ${page} | ${
                Math.round(
                    performance.now() -
                    t0
                )
            }ms`
        );


        return true;


    }catch(err){

        ////////////////////////////////////////////////////////
        // ABORT
        ////////////////////////////////////////////////////////

        if(
            err?.name ===
            "AbortError"
        ){

            return false;

        }


        ////////////////////////////////////////////////////////
        // ERROR
        ////////////////////////////////////////////////////////

        console.error(
            " LOAD FAIL:",
            page,
            err
        );


        if(
            thisLoad ===
                window.LOAD_ID &&

            !signal.aborted
        ){

            showLoadError(
                page
            );

        }


        return false;


    }finally{

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

};


////////////////////////////////////////////////////////////
//  EVENT DELEGATION
////////////////////////////////////////////////////////////

function setupDelegation(){

    const container =
        getContainer();


    if(!container){

        return;

    }


    if(
        container.dataset.delegated ===
        "true"
    ){

        return;

    }


    container.dataset.delegated =
        "true";


    container.addEventListener(
        "click",
        event=>{

            const post =
                event.target.closest(
                    ".post"
                );


            if(post){

                window.handlePostClick?.(
                    post,
                    event
                );

                return;

            }


            const likeBtn =
                event.target.closest(
                    "[data-action='like']"
                );


            if(likeBtn){

                window.handleLike?.(
                    likeBtn
                );

            }

        }
    );

}


////////////////////////////////////////////////////////////
//  API
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


window.getCurrentPage =
function(){

    return window.CURRENT_PAGE;

};


////////////////////////////////////////////////////////////
//  PREFETCH
////////////////////////////////////////////////////////////

window.prefetchPage =
function(page){

    const cached =
        window.PAGE_CACHE.get(
            page
        );


    if(
        cached &&

        Date.now() -
        cached.time <
        CACHE_TTL
    ){

        return;

    }


    const config =
        window.PAGE_CONFIG?.[
            page
        ];


    if(
        !config?.html ||

        typeof window.fetchHTML !==
        "function"
    ){

        return;

    }


    window.fetchHTML(
        config.html
    )
    .then(html=>{

        if(!html){

            return;

        }


        saveCache(
            page,
            html
        );

    })
    .catch(()=>{});

};


////////////////////////////////////////////////////////////
//  INIT
////////////////////////////////////////////////////////////

function initializePageLoader(){

    DOM.container =
        document.getElementById(
            MAIN_CONTAINER_ID
        );


    setupDelegation();


    preparePreconnect();


    console.log(
        " PAGELOADER INIT"
    );

}


if(
    document.readyState ===
    "loading"
){

    document.addEventListener(
        "DOMContentLoaded",
        initializePageLoader,
        {once:true}
    );

}else{

    initializePageLoader();

}


////////////////////////////////////////////////////////////
//  READY
////////////////////////////////////////////////////////////

console.log(
    " PAGE LOADER V12.0 READY"
);


console.log(
    " Instant Skeleton:",
    !!document.getElementById(
        "instantSkeleton"
    )
);


console.log(
    " Abort Race Protection: ON"
);


console.log(
    " Home Retry:",
    MAX_RETRY + 1,
    "attempts"
);


console.log(
    " TTL Cache:",
    CACHE_TTL + "ms"
);


console.log(
    " Cache Limit:",
    MAX_CACHE_SIZE
);


console.log(
    " Smooth Home Settle: ON"
); 
```

---

Generated by MiniGram MD Intelligence V6.
