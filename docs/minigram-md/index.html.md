# index.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `index.html` |
| Extension | `.html` |
| Size | 51107 bytes |
| Lines | 3074 |
| SHA-256 | `f40441f78b0c67d80627b83ade3523217db74a58861ee31578d3d767c21905e2` |

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
index.html
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

`/storage/emulated/0/MINIGRAM1/index.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="hi">

<head>

<meta charset="utf-8">

<meta
    name="viewport"
    content="width=device-width,initial-scale=1,viewport-fit=cover"
>

<meta
    name="theme-color"
    content="#000000"
>

<meta
    name="color-scheme"
    content="dark"
>

<title>MINIGRAM</title>


<!-- ============================================================
      MINIGRAM INSTANT FIRST PAINT ENGINE
     
     IMPORTANT:
     NOTHING BELOW THIS POINT IS REQUIRED FOR THE FIRST PIXELS.
     
     Browser can paint:
       BLACK  SKELETON
     
     before:
       fonts
       external CSS
       boot.bundle.js
       API
       Supabase
       page loader
     ============================================================ -->

<style>

/* ============================================================
   ZERO-BASE
   ============================================================ */

*,
*::before,
*::after{
    box-sizing:border-box;
}

html{
    margin:0;
    padding:0;
    width:100%;
    min-height:100%;
    background:#000;
    color:#fff;
    color-scheme:dark;
}

body{
    margin:0;
    padding:0;
    width:100%;
    min-height:100vh;

    background:#000;
    color:#fff;

    overflow-x:hidden;

    /*
     * System font first.
     * No external font is required for first paint.
     */
    font-family:
        Arial,
        Helvetica,
        sans-serif;

    /*
     * Avoid browser text flash affecting skeleton.
     */
    -webkit-text-size-adjust:100%;
    text-size-adjust:100%;
}

#app{
    width:100%;
    min-height:100vh;
    background:#000;
}

#mainContent{
    width:100%;
    min-height:100vh;
    background:#000;
}

.hidden{
    display:none !important;
}


/* ============================================================
    FIRST PAINT SHELL
   ============================================================ */

#instantSkeleton{

    display:block;

    width:100%;
    min-height:100vh;

    background:#000;

    /*
     * Isolate skeleton rendering from rest of app.
     */
    contain:
        layout
        style
        paint;

    /*
     * Prevent accidental selection.
     */
    user-select:none;
    -webkit-user-select:none;

}


/* ============================================================
   STORIES
   ============================================================ */

.skel-stories{

    display:flex;

    width:100%;
    height:89px;

    gap:13px;

    padding:
        12px
        14px;

    overflow:hidden;

    border-bottom:
        1px solid
        rgba(255,255,255,.07);

    contain:
        layout
        paint;
}

.skel-story{

    flex:
        0 0 64px;

    width:64px;
    height:64px;

    border-radius:50%;

    background:#171717;
}


/* ============================================================
   POST
   ============================================================ */

.skel-post{

    display:block;

    width:100%;

    background:#000;

    border-bottom:
        1px solid
        rgba(255,255,255,.07);

    contain:
        layout
        paint;
}


/* ============================================================
   USER HEADER
   ============================================================ */

.skel-user{

    width:100%;
    height:58px;

    display:flex;

    align-items:center;

    gap:10px;

    padding:
        10px
        13px;
}

.skel-avatar{

    width:36px;
    height:36px;

    flex:
        0 0 36px;

    border-radius:50%;

    background:#171717;
}

.skel-user-info{

    display:flex;

    flex-direction:column;

    gap:7px;
}

.skel-name{

    width:90px;
    height:10px;

    border-radius:5px;

    background:#171717;
}

.skel-sub{

    width:55px;
    height:7px;

    border-radius:4px;

    background:#141414;
}


/* ============================================================
   MEDIA
   ============================================================ */

.skel-media{

    display:block;

    width:100%;

    /*
     * aspect-ratio avoids layout jump.
     */
    aspect-ratio:1 / 1;

    background:#111;

    contain:
        layout
        paint;
}


/* ============================================================
   POST ACTIONS
   ============================================================ */

.skel-actions{

    height:52px;

    display:flex;

    align-items:center;

    gap:18px;

    padding:
        8px
        13px;
}

.skel-action{

    width:24px;
    height:24px;

    border-radius:50%;

    background:#171717;
}


/* ============================================================
    ULTRA-LIGHT SHIMMER
   ============================================================ */

@media (prefers-reduced-motion:no-preference){

    #instantSkeleton .skel-story,
    #instantSkeleton .skel-avatar,
    #instantSkeleton .skel-name,
    #instantSkeleton .skel-sub,
    #instantSkeleton .skel-media,
    #instantSkeleton .skel-action{

        animation:
            miniSkeletonPulse
            1.35s
            ease-in-out
            infinite
            alternate;
    }

}

@keyframes miniSkeletonPulse{

    from{
        opacity:.72;
    }

    to{
        opacity:1;
    }

}


/* ============================================================
   LOW-END DEVICE
   ============================================================ */

@media (prefers-reduced-motion:reduce){

    #instantSkeleton *{

        animation:none !important;

        transition:none !important;
    }

}


/* ============================================================
   LOADER
   ============================================================ */

#loader{
    display:none;
}

.simpleSpinner{

    width:22px;
    height:22px;

    border:
        2px solid
        rgba(255,255,255,.18);

    border-top-color:#fff;

    border-radius:50%;
}


/* ============================================================
   OLD UI PRESERVED
   ============================================================ */

#appbar,
#bottomNav{

    width:100%;
}


/* ============================================================
   OFFLINE
   ============================================================ */

#offlineIndicator{

    display:none;

    position:fixed;

    top:56px;
    left:0;
    right:0;

    z-index:2000;

    padding:6px;

    text-align:center;

    font-size:11px;

    background:#151515;
    color:#aaa;
}


/* ============================================================
   TOAST
   ============================================================ */

.toast{

    position:fixed;

    z-index:3000;

    pointer-events:none;
}

</style>


<!-- ============================================================
     CONNECTION WARM-UP
     ============================================================ -->

<link
    rel="preconnect"
    href="https://fonts.googleapis.com"
>

<link
    rel="preconnect"
    href="https://fonts.gstatic.com"
    crossorigin
>

<link
    rel="preconnect"
    href="https://cdn.jsdelivr.net"
    crossorigin
>


<!-- ============================================================
     NON-CRITICAL FONTS
     
     They no longer need to win the first-paint race.
     ============================================================ -->

<link
    rel="preload"
    as="style"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined"
    onload="
        this.onload=null;
        this.rel='stylesheet';
    "
>

<noscript>

<link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined"
>

</noscript>


<link
    rel="preload"
    as="style"
    href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@500;600&family=Open+Sans:wght@400;500&family=Poppins:wght@500;600&display=swap"
    onload="
        this.onload=null;
        this.rel='stylesheet';
    "
>

<noscript>

<link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@500;600&family=Open+Sans:wght@400;500&family=Poppins:wght@500;600&display=swap"
>

</noscript>


<!-- ============================================================
     FONT AWESOME
     OLD SYSTEM PRESERVED
     ============================================================ -->

<link
    rel="stylesheet"
    href="fontawesome/css/fontawesome.min.css"
>

<link
    rel="stylesheet"
    href="fontawesome/css/solid.min.css"
>


<!-- ============================================================
     CORE CSS
     OLD SYSTEM PRESERVED
     ============================================================ -->

<link
    rel="stylesheet"
    href="global_css/variables.css"
>

<link
    rel="stylesheet"
    href="global_css/base.css"
>

<link
    rel="stylesheet"
    href="global_css/layout.css"
>

<link
    rel="stylesheet"
    href="global_css/components.css"
>

<link
    rel="stylesheet"
    href="global_css/animations.css"
>














<!-- MINIGRAM GENERATED CRITICAL LOADPAGE START -->

<script>


(function () {

"use strict";

////////////////////////////////////////////////////////////
// 🚀 MINIGRAM CRITICAL LOADPAGE
////////////////////////////////////////////////////////////

const CRITICAL_PAGES =
{
    "search": "search_critical.css"
};


////////////////////////////////////////////////////////////
// 🧠 PROMISE CACHE
////////////////////////////////////////////////////////////

const PAGE_PROMISES =
    new Map();


////////////////////////////////////////////////////////////
// 🧠 REQUEST QUEUE
////////////////////////////////////////////////////////////

const PENDING_PAGES =
    new Map();


////////////////////////////////////////////////////////////
// 🔍 LOADPAGE DETECTION
////////////////////////////////////////////////////////////

function hasLoadPage() {

    return (
        typeof window.loadPage ===
        "function"
    );

}


////////////////////////////////////////////////////////////
// ⏳ WAIT FOR LOADPAGE
////////////////////////////////////////////////////////////

function waitForLoadPage() {

    if (hasLoadPage()) {

        return Promise.resolve(
            window.loadPage
        );

    }


    return new Promise(
        function (resolve) {

            const started =
                Date.now();

            const timeout =
                15000;


            function check() {

                if (hasLoadPage()) {

                    resolve(
                        window.loadPage
                    );

                    return;

                }


                if (
                    Date.now() -
                    started >=
                    timeout
                ) {

                    resolve(
                        null
                    );

                    return;

                }


                requestAnimationFrame(
                    check
                );

            }


            check();

        }
    );

}


////////////////////////////////////////////////////////////
// 🚀 EXECUTE PAGE
////////////////////////////////////////////////////////////

async function executePage(page) {

    const loadPage =
        await waitForLoadPage();


    if (
        typeof loadPage !==
        "function"
    ) {

        console.error(
            "[MiniGram] loadPage is not ready:",
            page
        );

        return false;

    }


    try {

        return await loadPage(
            page
        );

    } catch (error) {

        console.error(
            "[MiniGram] loadPage failed:",
            page,
            error
        );

        throw error;

    }

}


////////////////////////////////////////////////////////////
// 🚀 CRITICAL LOADPAGE
////////////////////////////////////////////////////////////

window.critical_loadpage =
function (page) {

    if (
        typeof page !==
        "string"
    ) {

        return Promise.resolve(
            false
        );

    }


    page =
        page.trim();


    if (!page) {

        return Promise.resolve(
            false
        );

    }


    //////////////////////////////////////////////////////////
    // PAGE EXISTENCE
    //////////////////////////////////////////////////////////

    if (
        !Object.prototype.hasOwnProperty.call(
            CRITICAL_PAGES,
            page
        )
    ) {

        console.warn(
            "[MiniGram] No critical CSS:",
            page
        );

    }


    //////////////////////////////////////////////////////////
    // PROMISE DEDUP
    //////////////////////////////////////////////////////////

    if (
        PAGE_PROMISES.has(page)
    ) {

        return PAGE_PROMISES.get(
            page
        );

    }


    //////////////////////////////////////////////////////////
    // CREATE SINGLE PROMISE
    //////////////////////////////////////////////////////////

    const promise =
        executePage(
            page
        );


    PAGE_PROMISES.set(
        page,
        promise
    );


    promise.finally(
        function () {

            /*
             * Keep successful page promise cached.
             *
             * This means repeated navigation
             * does not create another execution
             * promise unnecessarily.
             */

        }
    );


    return promise;

};


////////////////////////////////////////////////////////////
// 🧩 READY STATE
////////////////////////////////////////////////////////////

window.__MINIGRAM_CRITICAL_STATE__ =
function () {

    return {

        loadPageReady:
            hasLoadPage(),

        pages:
            Object.keys(
                CRITICAL_PAGES
            ),

        cachedPages:
            Array.from(
                PAGE_PROMISES.keys()
            )

    };

};


////////////////////////////////////////////////////////////
// 🚀 LOADPAGE READY HOOK
////////////////////////////////////////////////////////////

window.__MINIGRAM_PAGELOADER_READY__ =
function () {

    console.log(
        "[MiniGram] PageLoader ready"
    );


    for (
        const [
            page,
            resolver
        ] of PENDING_PAGES
    ) {

        try {

            resolver(
                executePage(
                    page
                )
            );

        } catch (error) {

            resolver(
                Promise.reject(
                    error
                )
            );

        }

        PENDING_PAGES.delete(
            page
        );

    }

};


////////////////////////////////////////////////////////////
// 🛡️ GLOBAL SAFE HELPER
////////////////////////////////////////////////////////////

window.__MINIGRAM_HAS_LOADPAGE__ =
function () {

    return hasLoadPage();

};


////////////////////////////////////////////////////////////
// 🔥 DEBUG
////////////////////////////////////////////////////////////

console.log(
    "[MiniGram] Critical Loader Ready"
);

console.log(
    "[MiniGram] Critical Pages:",
    Object.keys(
        CRITICAL_PAGES
    )
);

})();

</script>

<!-- MINIGRAM GENERATED CRITICAL LOADPAGE END -->







</style>

<!-- MINIGRAM GENERATED CRITICAL CSS END -->













<!-- MINIGRAM GENERATED CRITICAL NAV START -->

<script>


/* ============================================================
   🚀 MINIGRAM CRITICAL NAVIGATION SYSTEM V8
   ============================================================

   GENERATED AUTOMATICALLY.

   IMPORTANT:

   Every page navigation goes through:

       critical_loadpage("page")

   Page critical CSS is already INLINE inside index.html.

   No external page critical CSS request is required.

   ============================================================ */

(function () {

"use strict";


////////////////////////////////////////////////////////////
// 📦 PAGE MAP
////////////////////////////////////////////////////////////

const CRITICAL_PAGES =
{
    "search": "search_critical.css"
};


////////////////////////////////////////////////////////////
// 🧠 STATE
////////////////////////////////////////////////////////////

let currentPage =
    null;

let pendingPage =
    null;

let realLoadPage =
    null;

let bridgeInstalled =
    false;

let ready =
    false;


////////////////////////////////////////////////////////////
// 📦 READY QUEUE
////////////////////////////////////////////////////////////

const pendingCalls =
    [];


////////////////////////////////////////////////////////////
// 🎨 FIND PAGE STYLE
////////////////////////////////////////////////////////////

function getPageStyle(page) {

    return document.querySelector(
        'style[data-minigram-critical-page="' +
        page +
        '"]'
    );

}


////////////////////////////////////////////////////////////
// 🎨 DEACTIVATE PAGE CSS
////////////////////////////////////////////////////////////

function deactivatePageCSS(page) {

    if (
        !page
    ) {

        return;

    }

    const style =
        getPageStyle(
            page
        );

    if (
        style
    ) {

        style.media =
            "not all";

    }

}


////////////////////////////////////////////////////////////
// 🎨 ACTIVATE PAGE CSS
////////////////////////////////////////////////////////////

function activatePageCSS(page) {

    const style =
        getPageStyle(
            page
        );

    if (
        !style
    ) {

        console.warn(
            "[MiniGram] No critical CSS:",
            page
        );

        return false;

    }

    ////////////////////////////////////////////////////////
    // Disable previous page
    ////////////////////////////////////////////////////////

    if (
        currentPage &&
        currentPage !== page
    ) {

        deactivatePageCSS(
            currentPage
        );

    }

    ////////////////////////////////////////////////////////
    // Enable requested page
    ////////////////////////////////////////////////////////

    style.media =
        "all";

    currentPage =
        page;

    return true;

}


////////////////////////////////////////////////////////////
// 🦴 SKELETON HOOK
////////////////////////////////////////////////////////////

function activateSkeleton(page) {

    try {

        ////////////////////////////////////////////////////
        // Optional runtime hooks
        ////////////////////////////////////////////////////

        if (
            typeof window.showSkeleton ===
            "function"
        ) {

            window.showSkeleton(
                page
            );

        }

        if (
            typeof window.showPageSkeleton ===
            "function"
        ) {

            window.showPageSkeleton(
                page
            );

        }

    } catch (
        error
    ) {

        console.warn(
            "[MiniGram] Skeleton hook failed",
            error
        );

    }

}


////////////////////////////////////////////////////////////
// 🚀 CALL REAL PAGELOADER
////////////////////////////////////////////////////////////

function callRealLoadPage(
    page
) {

    if (
        typeof realLoadPage !==
        "function"
    ) {

        pendingPage =
            page;

        return false;

    }

    try {

        return realLoadPage(
            page
        );

    } catch (
        error
    ) {

        console.error(
            "[MiniGram] loadPage failed:",
            error
        );

        throw error;

    }

}


////////////////////////////////////////////////////////////
// ⚡ CRITICAL LOAD PAGE
////////////////////////////////////////////////////////////

window.critical_loadpage =
function (page) {

    if (
        typeof page !==
        "string"
    ) {

        return Promise.resolve(
            false
        );

    }

    page =
        page.trim();

    if (
        !page
    ) {

        return Promise.resolve(
            false
        );

    }

    ////////////////////////////////////////////////////////
    // Unknown page
    ////////////////////////////////////////////////////////

    if (
        !CRITICAL_PAGES[page]
    ) {

        console.warn(
            "[MiniGram] Critical page not found:",
            page
        );

        ////////////////////////////////////////////////////
        // Still allow normal PageLoader
        ////////////////////////////////////////////////////

        if (
            typeof realLoadPage ===
            "function"
        ) {

            return Promise.resolve(
                callRealLoadPage(
                    page
                )
            );

        }

        pendingPage =
            page;

        return Promise.resolve(
            false
        );

    }

    ////////////////////////////////////////////////////////
    // CRITICAL CSS FIRST
    //
    // It is INLINE, therefore this is synchronous.
    ////////////////////////////////////////////////////////

    activateSkeleton(
        page
    );

    activatePageCSS(
        page
    );

    ////////////////////////////////////////////////////////
    // PageLoader ready?
    ////////////////////////////////////////////////////////

    if (
        typeof realLoadPage ===
        "function"
    ) {

        return Promise.resolve(
            callRealLoadPage(
                page
            )
        );

    }

    ////////////////////////////////////////////////////////
    // PageLoader not ready
    ////////////////////////////////////////////////////////

    pendingPage =
        page;

    return new Promise(
        function (resolve) {

            pendingCalls.push({
                page: page,
                resolve: resolve
            });

        }
    );

};


////////////////////////////////////////////////////////////
// 🔥 INSTALL LOADPAGE BRIDGE
////////////////////////////////////////////////////////////

function installBridge() {

    if (
        bridgeInstalled
    ) {

        return;

    }

    if (
        typeof window.loadPage !==
        "function"
    ) {

        return;

    }

    ////////////////////////////////////////////////////////
    // Save original PageLoader
    ////////////////////////////////////////////////////////

    realLoadPage =
        window.loadPage;

    ////////////////////////////////////////////////////////
    // Replace global loadPage
    //
    // Existing UI code can continue doing:
    //
    // loadPage("search")
    //
    // but internally it becomes:
    //
    // critical_loadpage("search")
    ////////////////////////////////////////////////////////

    window.loadPage =
    function (page) {

        return window.critical_loadpage(
            page
        );

    };

    bridgeInstalled =
        true;

    ready =
        true;

    console.log(
        "[MiniGram] PageLoader detected"
    );

    console.log(
        "[MiniGram] Critical navigation bridge installed"
    );

    console.log(
        "[MiniGram] All page navigation -> critical_loadpage()"
    );

    ////////////////////////////////////////////////////////
    // Pending page
    ////////////////////////////////////////////////////////

    if (
        pendingPage
    ) {

        const page =
            pendingPage;

        pendingPage =
            null;

        window.critical_loadpage(
            page
        );

    }

    ////////////////////////////////////////////////////////
    // Pending promises
    ////////////////////////////////////////////////////////

    while (
        pendingCalls.length
    ) {

        const call =
            pendingCalls.shift();

        try {

            const result =
                window.critical_loadpage(
                    call.page
                );

            call.resolve(
                result
            );

        } catch (
            error
        ) {

            console.error(
                "[MiniGram] Pending page failed:",
                error
            );

            call.resolve(
                false
            );

        }

    }

}


////////////////////////////////////////////////////////////
// ⏳ WAIT FOR PAGELOADER
////////////////////////////////////////////////////////////

function waitForPageLoader() {

    if (
        bridgeInstalled
    ) {

        return;

    }

    if (
        typeof window.loadPage ===
        "function"
    ) {

        installBridge();

        return;

    }

    setTimeout(
        waitForPageLoader,
        0
    );

}


////////////////////////////////////////////////////////////
// 🔄 READY HOOK
////////////////////////////////////////////////////////////

window.__CRITICAL_PAGELOADER_READY__ =
function () {

    installBridge();

};


////////////////////////////////////////////////////////////
// 🧩 PUBLIC STATE
////////////////////////////////////////////////////////////

window.__CRITICAL_LOADPAGE_STATE__ =
function () {

    return {

        ready:
            ready,

        bridgeInstalled:
            bridgeInstalled,

        currentPage:
            currentPage,

        pendingPage:
            pendingPage,

        pages:
            Object.keys(
                CRITICAL_PAGES
            )

    };

};


////////////////////////////////////////////////////////////
// 🚀 PUBLIC PAGE MAP
////////////////////////////////////////////////////////////

window.__MINIGRAM_CRITICAL_PAGES__ =
    CRITICAL_PAGES;


////////////////////////////////////////////////////////////
// 🔥 START
////////////////////////////////////////////////////////////

console.log(
    "[MiniGram] Critical Loader Ready"
);

console.log(
    "[MiniGram] Critical Pages:",
    Object.keys(
        CRITICAL_PAGES
    )
);


waitForPageLoader();


////////////////////////////////////////////////////////////
// 🛡️ EXTRA RETRY
////////////////////////////////////////////////////////////

setTimeout(
    installBridge,
    0
);

setTimeout(
    installBridge,
    10
);

setTimeout(
    installBridge,
    50
);

setTimeout(
    installBridge,
    100
);

setTimeout(
    installBridge,
    250
);

setTimeout(
    installBridge,
    500
);

setTimeout(
    installBridge,
    1000
);


})();

</script>

<!-- MINIGRAM GENERATED CRITICAL NAV END -->




<!-- MINIGRAM GENERATED CRITICAL CSS START -->



<style
    data-minigram-critical="true"
    data-critical-page="search"
    id="minigram-critical-search"
>
/* =====================================================
   MINIGRAM CRITICAL CSS
   PAGE: search
   SOURCE: critical_css/search_critical.css
   ===================================================== */

/* ============================================================
   🔥 MINIGRAM — SEARCH CRITICAL CSS
   FILE: search_critical.css

   PURPOSE:
   - Instant Search page skeleton
   - Reserve layout space
   - Prevent layout shift
   - No images
   - No heavy effects
   - No external dependencies
   - No actual search UI styling

   NON-CRITICAL:
   search.css handles the real UI after page load.
   ============================================================ */


/* ============================================================
   🌐 SEARCH PAGE BASE
   ============================================================ */

.searchPage{

    width:100%;

    min-height:100vh;

    margin:0;

    padding:
        12px
        12px
        90px;

    box-sizing:border-box;

    background:#0b0b0b;

}


/* ============================================================
   🔍 SEARCH BAR SKELETON
   ============================================================ */

.searchBar{

    width:100%;

    height:48px;

    box-sizing:border-box;

    display:flex;

    align-items:center;

    gap:10px;

    padding:12px;

    border-radius:14px;

    background:#1e1e1e;

}


/* ============================================================
   🔍 SEARCH ICON SKELETON
   ============================================================ */

.searchBar span{

    display:block;

    width:22px;

    height:22px;

    flex:
        0 0 22px;

    border-radius:50%;

    background:#303030;

    font-size:0;

}


/* ============================================================
   📝 SEARCH INPUT PLACEHOLDER
   ============================================================ */

.searchBar input{

    flex:1;

    min-width:0;

    height:18px;

    border:0;

    outline:0;

    background:#303030;

    border-radius:9px;

    color:transparent;

}


/* ============================================================
   👤 SEARCH RESULTS CONTAINER
   ============================================================ */

.searchResults{

    width:100%;

    margin-top:15px;

    display:flex;

    flex-direction:column;

    gap:10px;

}


/* ============================================================
   👤 SEARCH USER SKELETON
   ============================================================ */

.searchUser{

    width:100%;

    min-height:65px;

    box-sizing:border-box;

    display:flex;

    align-items:center;

    gap:12px;

    padding:10px;

    border-radius:12px;

    background:#111;

}


/* ============================================================
   👤 USER AVATAR
   ============================================================ */

.searchUser img{

    width:45px;

    height:45px;

    flex:
        0 0 45px;

    border-radius:50%;

    object-fit:cover;

    background:#222;

}


/* ============================================================
   📝 USER NAME SKELETON
   ============================================================ */

.searchUser span{

    display:block;

    width:100px;

    height:14px;

    border-radius:7px;

    background:#292929;

    font-size:0;

}


/* ============================================================
   🔥 EXPLORE GRID
   ============================================================ */

.exploreGrid{

    width:100%;

    box-sizing:border-box;

    display:grid;

    grid-template-columns:
        repeat(3,1fr);

    gap:3px;

    padding:
        0
        4px;

    margin-top:14px;

}


/* ============================================================
   📦 GRID ITEM
   ============================================================ */

.gridItem{

    position:relative;

    width:100%;

    height:120px;

    min-height:120px;

    overflow:hidden;

    border-radius:12px;

    background:#151515;

}


/* ============================================================
   🔥 BIG GRID ITEM
   ============================================================ */

.gridItem.big{

    grid-column:
        span 2;

    grid-row:
        span 2;

    height:243px;

    min-height:243px;

}


/* ============================================================
   🖼️ GRID IMAGE PLACEHOLDER
   ============================================================ */

.gridItem img{

    position:absolute;

    inset:0;

    width:100%;

    height:100%;

    display:block;

    object-fit:cover;

    background:#151515;

}


/* ============================================================
   ⚡ CRITICAL SKELETON
   ============================================================ */

.searchPage .skeleton{

    background:
        linear-gradient(
            90deg,
            #111 25%,
            #1a1a1a 50%,
            #111 75%
        );

    background-size:
        200% 100%;

    animation:
        searchCriticalShimmer
        1.2s
        infinite;

}


/* ============================================================
   🌊 LIGHTWEIGHT SHIMMER
   ============================================================ */

@keyframes searchCriticalShimmer{

    0%{

        background-position:
            200% 0;

    }

    100%{

        background-position:
            -200% 0;

    }

}


/* ============================================================
   📱 MOBILE SAFETY
   ============================================================ */

@media (max-width:480px){

    .searchPage{

        padding-left:12px;

        padding-right:12px;

    }

    .gridItem{

        height:120px;

        min-height:120px;

    }

    .gridItem.big{

        height:243px;

        min-height:243px;

    }

}


/* ============================================================
   ♿ REDUCED MOTION
   ============================================================ */

@media (prefers-reduced-motion:reduce){

    .searchPage .skeleton{

        animation:none;

    }

}


/* ============================================================
   🛡️ PREVENT FLASH / COLLAPSE
   ============================================================ */

.searchPage{

    contain:
        layout;

}

.exploreGrid{

    contain:
        layout;

}


/* ============================================================
   🚫 NON-CRITICAL UI IS NOT INCLUDED HERE
   ============================================================

   search.css handles:

   - sticky search effects
   - gradients
   - shadows
   - hover
   - active transforms
   - postViewer
   - postContainer
   - glass buttons
   - animations
   - backdrop-filter
   - real colors/details

   ============================================================ */

/* =====================================================
   END CRITICAL CSS
   ===================================================== */
</style>


<!-- MINIGRAM GENERATED CRITICAL CSS END -->



<!-- MINIGRAM GENERATED CRITICAL LOADER START -->

<script>

(function () {

"use strict";


/*
============================================================
🚀 MINIGRAM CRITICAL LOADPAGE
============================================================

ALL CRITICAL CSS IS ALREADY INLINE.

THEREFORE:

critical_loadpage("search")
        ↓
search critical UI already available
        ↓
ensure skeleton
        ↓
wait for real loadPage
        ↓
loadPage("search")

NO CSS NETWORK REQUEST.

============================================================
*/


////////////////////////////////////////////////////////////
// 📦 AVAILABLE CRITICAL PAGES
////////////////////////////////////////////////////////////

window.__MINIGRAM_CRITICAL_PAGES__ =
[
    "search"
];


////////////////////////////////////////////////////////////
// 🧠 STATE
////////////////////////////////////////////////////////////

var pendingCalls = [];

var waitingForLoadPage = false;


////////////////////////////////////////////////////////////
// 🔎 GET CRITICAL STYLE
////////////////////////////////////////////////////////////

function getCriticalStyle(page) {

    return document.querySelector(
        'style[data-minigram-critical="true"][data-critical-page="' +
        page +
        '"]'
    );

}


////////////////////////////////////////////////////////////
// ⚡ CRITICAL UI READY
////////////////////////////////////////////////////////////

function ensureCriticalUI(page) {

    var style =
        getCriticalStyle(page);

    if (style) {

        /*
         * CSS is already parsed/available
         * because it is inline in index.html.
         */

        style.setAttribute(
            "data-critical-ready",
            "true"
        );

        return true;

    }

    return false;

}


////////////////////////////////////////////////////////////
// 💀 SAFE LOADPAGE CHECK
////////////////////////////////////////////////////////////

function getRealLoadPage() {

    if (
        typeof window.loadPage ===
        "function"
    ) {

        /*
         * Avoid accidentally calling ourselves
         * if another system assigns a proxy.
         */

        if (
            window.loadPage !==
            window.critical_loadpage
        ) {

            return window.loadPage;

        }

    }

    return null;

}


////////////////////////////////////////////////////////////
// ⏳ WAIT FOR PAGELOADER
////////////////////////////////////////////////////////////

function waitForLoadPage() {

    return new Promise(
        function (resolve) {

            var start =
                performance.now();

            var maxWait =
                15000;

            function check() {

                var loader =
                    getRealLoadPage();

                if (loader) {

                    resolve(
                        loader
                    );

                    return;

                }

                if (
                    performance.now() -
                    start >=
                    maxWait
                ) {

                    resolve(
                        null
                    );

                    return;

                }

                /*
                 * Very small polling interval.
                 *
                 * Does NOT block the main thread.
                 */

                setTimeout(
                    check,
                    10
                );

            }

            check();

        }
    );

}


////////////////////////////////////////////////////////////
// 🦴 SKELETON
////////////////////////////////////////////////////////////

function ensureSkeleton() {

    /*
     * Global skeleton CSS is already inline.
     *
     * If your existing skeleton boot system exists,
     * it remains responsible for DOM skeleton creation.
     *
     * We intentionally do NOT create a fake skeleton
     * here because the project's existing skeleton manager
     * owns the actual DOM.
     */

    var skeletonStyle =
        document.querySelector(
            'style[data-critical-page="skeleton"]'
        );

    if (
        skeletonStyle
    ) {

        skeletonStyle.setAttribute(
            "data-critical-ready",
            "true"
        );

    }

}


////////////////////////////////////////////////////////////
// 🚀 EXECUTE
////////////////////////////////////////////////////////////

async function executeCriticalPage(
    page
) {

    /*
     * STEP 1
     *
     * Critical CSS is already inline.
     */

    ensureCriticalUI(
        page
    );


    /*
     * STEP 2
     *
     * Global skeleton CSS is already inline.
     */

    ensureSkeleton();


    /*
     * STEP 3
     *
     * Wait for actual PageLoader.
     */

    var loader =
        getRealLoadPage();

    if (!loader) {

        waitingForLoadPage =
            true;

        loader =
            await waitForLoadPage();

        waitingForLoadPage =
            false;

    }


    /*
     * STEP 4
     *
     * PageLoader still unavailable.
     */

    if (!loader) {

        console.warn(
            "[MiniGram] loadPage not ready for:",
            page
        );

        return false;

    }


    /*
     * STEP 5
     *
     * Actual PageLoader.
     */

    try {

        return await loader(
            page
        );

    } catch (error) {

        console.error(
            "[MiniGram] loadPage failed:",
            page,
            error
        );

        throw error;

    }

}


////////////////////////////////////////////////////////////
// ⚡ PUBLIC API
////////////////////////////////////////////////////////////

window.critical_loadpage =
function (page) {

    if (
        typeof page !== "string"
    ) {

        return Promise.resolve(
            false
        );

    }

    page =
        page.trim();

    if (!page) {

        return Promise.resolve(
            false
        );

    }

    return executeCriticalPage(
        page
    );

};


////////////////////////////////////////////////////////////
// 🛡️ SAFE EARLY loadPage BRIDGE
////////////////////////////////////////////////////////////

/*
 * IMPORTANT:
 *
 * Some existing UI code may execute:
 *
 *     loadPage("search")
 *
 * before PageLoader has loaded.
 *
 * Instead of:
 *
 *     ReferenceError
 *
 * we provide a temporary bridge.
 *
 * Once PageLoader creates the real loadPage,
 * this bridge is naturally replaced by the real API.
 */

if (
    typeof window.loadPage !==
    "function"
) {

    window.loadPage =
    function (page) {

        return window.critical_loadpage(
            page
        );

    };

}


////////////////////////////////////////////////////////////
// 🔄 PAGELOADER READY HOOK
////////////////////////////////////////////////////////////

window.__MINIGRAM_CRITICAL_READY__ =
function () {

    console.log(
        "[MiniGram] PageLoader Ready"
    );

};


////////////////////////////////////////////////////////////
// 📊 DEBUG
////////////////////////////////////////////////////////////

window.__MINIGRAM_CRITICAL_STATE__ =
function () {

    return {

        pages:
            window.__MINIGRAM_CRITICAL_PAGES__,

        waitingForLoadPage:
            waitingForLoadPage,

        criticalStyles:
            document.querySelectorAll(
                'style[data-minigram-critical="true"]'
            ).length

    };

};


console.log(
    "[MiniGram] Critical Loader Ready"
);

console.log(
    "[MiniGram] Critical Pages:",
    window.__MINIGRAM_CRITICAL_PAGES__
);


})();

</script>

<!-- MINIGRAM GENERATED CRITICAL LOADER END -->


</head>


<body>

<div id="app">


<!-- ============================================================
     OLD LOADER
     ============================================================ -->

<div
    id="loader"
>

    <div class="simpleSpinner"></div>

</div>


<!-- ============================================================
     OLD APPBAR
     COMPLETELY PRESERVED
     ============================================================ -->

<header
    class="appbar hidden"
    id="appbar"
>

    <div class="title">
        MINIGRAM
    </div>


    <div class="appbarIcons">

        <span
            class="material-symbols-outlined"
            onclick="loadPage?.('home')"
        >
            refresh
        </span>


        <span
            class="material-symbols-outlined"
            onclick="createPost?.()"
        >
            add_box
        </span>


        <span
            class="material-symbols-outlined"
            onclick="openNotifications?.()"
        >
            favorite
        </span>


        <span
            class="material-symbols-outlined"
            onclick="openChat?.()"
        >
            chat
        </span>

    </div>

</header>


<!-- ============================================================
     SINGLE PAGE OWNER
     
      REAL FIRST-PAINT DOM
     
     Previously this was EMPTY.
     
     Now browser has something to paint immediately.
     ============================================================ -->

<main
    id="mainContent"
>


<!-- ============================================================
      INSTANT SKELETON
     ============================================================ -->

<div
    id="instantSkeleton"
    class="instant-skeleton"
    aria-hidden="true"
>


    <!-- ========================================================
         STORIES
         ======================================================== -->

    <div class="skel-stories">

        <div class="skel-story"></div>

        <div class="skel-story"></div>

        <div class="skel-story"></div>

        <div class="skel-story"></div>

        <div class="skel-story"></div>

        <div class="skel-story"></div>

    </div>


    <!-- ========================================================
         POST 1
         ======================================================== -->

    <article class="skel-post">


        <div class="skel-user">

            <div class="skel-avatar"></div>


            <div class="skel-user-info">

                <div class="skel-name"></div>

                <div class="skel-sub"></div>

            </div>

        </div>


        <div class="skel-media"></div>


        <div class="skel-actions">

            <div class="skel-action"></div>

            <div class="skel-action"></div>

            <div class="skel-action"></div>

        </div>


    </article>


    <!-- ========================================================
         POST 2
         ======================================================== -->

    <article class="skel-post">


        <div class="skel-user">

            <div class="skel-avatar"></div>


            <div class="skel-user-info">

                <div class="skel-name"></div>

                <div class="skel-sub"></div>

            </div>

        </div>


        <div class="skel-media"></div>


        <div class="skel-actions">

            <div class="skel-action"></div>

            <div class="skel-action"></div>

            <div class="skel-action"></div>

        </div>


    </article>


</div>


</main>


<!-- ============================================================
     OLD TOAST
     ============================================================ -->

<div
    class="toast"
    id="toast"
></div>


<!-- ============================================================
     OLD OFFLINE INDICATOR
     ============================================================ -->

<div
    id="offlineIndicator"
>

    Offline � showing saved content

</div>


<!-- ============================================================
     OLD BOTTOM NAV
     COMPLETELY PRESERVED
     ============================================================ -->

<nav
    class="bottomNav hidden"
    id="bottomNav"
>


    <div
        class="navIcon active"
        onclick="loadPage?.('home')"
    >

        <span class="material-symbols-outlined">
            home
        </span>

    </div>


    <div
        class="navIcon"
        onclick="loadPage?.('search')"
    >

        <span class="material-symbols-outlined">
            search
        </span>

    </div>


    <div
        class="navIcon"
        onclick="createPost?.()"
    >

        <span class="material-symbols-outlined addBtn">
            add_circle
        </span>

    </div>


    <div
        class="navIcon"
        onclick="loadPage?.('profile')"
    >

        <span class="material-symbols-outlined">
            person
        </span>

    </div>


    <div
        class="navIcon"
        onclick="loadPage?.('reels')"
    >

        <span class="material-symbols-outlined">
            slideshow
        </span>

    </div>


</nav>


</div>


<!-- ============================================================
     DEBUG
     ============================================================ -->

<script>

(function(){

    if(
        !new URLSearchParams(location.search)
            .has("debug")
    ){

        return;

    }


    const script =
        document.createElement("script");


    script.src =
        "eruda.min.js";


    script.onload =
        function(){

            window.eruda?.init();

        };


    document.body.appendChild(
        script
    );

})();

</script>


<!-- ============================================================
     OFFLINE
     ============================================================ -->

<script>

(function(){

    const indicator =
        document.getElementById(
            "offlineIndicator"
        );


    function updateNetwork(){

        const offline =
            !navigator.onLine;


        document.body.classList.toggle(
            "offline",
            offline
        );


        if(indicator){

            indicator.style.display =
                offline
                    ? "block"
                    : "none";

        }

    }


    updateNetwork();


    window.addEventListener(
        "online",
        updateNetwork,
        {
            passive:true
        }
    );


    window.addEventListener(
        "offline",
        updateNetwork,
        {
            passive:true
        }
    );

})();

</script>


<!-- ============================================================
      BOOT
     
     DEFER:
     HTML parsing continues immediately.
     
     The skeleton is already in the DOM.
     ============================================================ -->

<script
    src="main_js/bundles/boot.bundle.js"
    defer
></script>


<!-- ============================================================
      SKELETON HANDOFF
     
     IMPORTANT:
     boot.bundle.js should ideally remove #instantSkeleton
     itself when real Home UI is ready.
     
     This fallback detects when boot replaces the skeleton.
     ============================================================ -->

<script>

(function(){

    const main =
        document.getElementById(
            "mainContent"
        );

    const skeleton =
        document.getElementById(
            "instantSkeleton"
        );


    if(
        !main ||
        !skeleton
    ){

        return;

    }


    /*
     * Observe ONLY direct children.
     *
     * Very cheap compared with observing the entire app tree.
     */

    const observer =
        new MutationObserver(
            function(){

                const first =
                    main.firstElementChild;


                /*
                 * If boot/page-loader has replaced
                 * the skeleton with real UI,
                 * remove skeleton.
                 */

                if(
                    first &&
                    first !== skeleton
                ){

                    skeleton.remove();

                    observer.disconnect();

                }

            }
        );


    observer.observe(
        main,
        {
            childList:true
        }
    );


    /*
     * Safety:
     * if some system manually clears the main area,
     * don't keep observer alive forever.
     */

    window.setTimeout(
        function(){

            observer.disconnect();

        },
        15000
    );

})();

</script>


</body>

</html>
```

---

Generated automatically.
