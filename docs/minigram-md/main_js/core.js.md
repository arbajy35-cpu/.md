# main_js/core.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/core.js` |
| Extension | `.js` |
| Size | 9734 bytes |
| Lines | 499 |
| SHA-256 | `7448f0087b8e7ea26d5aabd7964eedad34109ac06f117fad90f761cd6f92c80d` |

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
main_js/core.js
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

`/storage/emulated/0/MINIGRAM1/main_js/core.js`

No AI rewriting was performed on the source code.

```javascript
////////////////////////////////////////////////////////////
// 🚀 MINIGRAM CORE
// V2 — PAGELOADER BRIDGE SAFE
//
// IMPORTANT:
//
// core.js does NOT own PageLoader.
//
// PageLoader ownership:
//
// loaderCore.js
//      ↓
// __PAGE_LOADER_CORE_LOAD_PAGE__
//      ↓
// pageLoader.js
//      ↓
// window.loadPage
//
// core.js ONLY:
// - global application state
// - navigation event wiring
// - safe global exports for non-PageLoader functions
//
// NEVER:
// - create window.loadPage
// - overwrite window.loadPage
// - reference local loadPage()
// - create another PageLoader bridge
////////////////////////////////////////////////////////////


////////////////////////////////////////////////////////////
// 🌐 GLOBAL STATE
// SINGLE SOURCE
////////////////////////////////////////////////////////////

window.STATE =
    window.STATE ||
    {

        FEED: [],

        PAGE: 0,

        LIMIT: 5,

        LOADING: false,

        END: false,

        postChannel: null

    };


////////////////////////////////////////////////////////////
// 🧭 NAVIGATION
//
// Navigation talks ONLY to the public PageLoader API.
//
// core.js does not implement PageLoader.
//
////////////////////////////////////////////////////////////

function initNavigation(){

    console.log(
        "🧭 INIT NAV"
    );


    try{

        //////////////////////////////////////////////////////
        // BUTTONS
        //////////////////////////////////////////////////////

        const homeBtn =
            document.getElementById(
                "homeBtn"
            );


        const searchBtn =
            document.getElementById(
                "searchBtn"
            );


        const profileBtn =
            document.getElementById(
                "profileBtn"
            );


        const reelsBtn =
            document.getElementById(
                "reelsBtn"
            );


        const createBtn =
            document.getElementById(
                "createBtn"
            );


        //////////////////////////////////////////////////////
        // 🏠 HOME
        //////////////////////////////////////////////////////

        if(
            homeBtn
        ){

            homeBtn.onclick =
                () => {

                    if(
                        typeof window.loadPage ===
                        "function"
                    ){

                        return window.loadPage(
                            "home"
                        );

                    }


                    console.warn(
                        "⏳ PageLoader not ready: home"
                    );

                    return false;

                };

        }


        //////////////////////////////////////////////////////
        // 🔎 SEARCH
        //////////////////////////////////////////////////////

        if(
            searchBtn
        ){

            searchBtn.onclick =
                () => {

                    if(
                        typeof window.loadPage ===
                        "function"
                    ){

                        return window.loadPage(
                            "search"
                        );

                    }


                    console.warn(
                        "⏳ PageLoader not ready: search"
                    );

                    return false;

                };

        }


        //////////////////////////////////////////////////////
        // 👤 PROFILE
        //////////////////////////////////////////////////////

        if(
            profileBtn
        ){

            profileBtn.onclick =
                () => {

                    if(
                        typeof window.loadPage ===
                        "function"
                    ){

                        return window.loadPage(
                            "profile"
                        );

                    }


                    console.warn(
                        "⏳ PageLoader not ready: profile"
                    );

                    return false;

                };

        }


        //////////////////////////////////////////////////////
        // 🎬 REELS
        //////////////////////////////////////////////////////

        if(
            reelsBtn
        ){

            reelsBtn.onclick =
                () => {

                    if(
                        typeof window.loadPage ===
                        "function"
                    ){

                        return window.loadPage(
                            "reels"
                        );

                    }


                    console.warn(
                        "⏳ PageLoader not ready: reels"
                    );

                    return false;

                };

        }


        //////////////////////////////////////////////////////
        // ➕ CREATE
        //////////////////////////////////////////////////////

        if(
            createBtn
        ){

            createBtn.onclick =
                () => {

                    if(
                        typeof window.createPost ===
                        "function"
                    ){

                        return window.createPost();

                    }


                    console.warn(
                        "⚠️ createPost() not ready"
                    );

                    return false;

                };

        }


        //////////////////////////////////////////////////////
        // ✅ NAV READY
        //////////////////////////////////////////////////////

        console.log(
            "🧭 NAVIGATION READY"
        );


    }catch(error){

        console.error(
            "❌ NAV INIT ERROR:",
            error
        );

    }

}


////////////////////////////////////////////////////////////
// 🚀 DOM READY
//
// IMPORTANT:
//
// core.js does NOT call:
// initApp()
// startApp()
// loadPage()
// bootPageLoader()
//
// PageLoader boot system owns startup.
//
////////////////////////////////////////////////////////////

function initCore(){

    console.log(
        "🔥 CORE INIT"
    );


    try{

        initNavigation();


    }catch(error){

        console.error(
            "❌ CORE INIT ERROR:",
            error
        );

    }

}


////////////////////////////////////////////////////////////
// ⏱️ DOM READY
////////////////////////////////////////////////////////////

if(
    document.readyState ===
    "loading"
){

    document.addEventListener(
        "DOMContentLoaded",
        initCore,
        {
            once: true
        }
    );

}else{

    initCore();

}


////////////////////////////////////////////////////////////
// 🌐 SAFE GLOBAL EXPORTS
//
// IMPORTANT:
//
// Only non-PageLoader functions are exported here.
//
// NEVER:
//
// window.loadPage = loadPage
//
// PageLoader's public API belongs exclusively
// to main_js/pageLoader.js.
//
////////////////////////////////////////////////////////////


////////////////////////////////////////////////////////////
// ➕ CREATE POST
////////////////////////////////////////////////////////////

if(
    typeof window.createPost !==
        "function" &&

    typeof createPost ===
        "function"
){

    window.createPost =
        createPost;

}


////////////////////////////////////////////////////////////
// 💬 OPEN CHAT
////////////////////////////////////////////////////////////

if(
    typeof window.openChat !==
        "function" &&

    typeof openChat ===
        "function"
){

    window.openChat =
        openChat;

}


////////////////////////////////////////////////////////////
// 🛡️ PAGELOADER OWNERSHIP CHECK
//
// This is diagnostic only.
//
// core.js NEVER creates or modifies window.loadPage.
//
////////////////////////////////////////////////////////////

if(
    typeof window.loadPage ===
    "function"
){

    console.log(
        "🔗 PageLoader API detected"
    );

}else{

    console.log(
        "⏳ PageLoader API waiting..."
    );

}


////////////////////////////////////////////////////////////
// 🚫 PAGELOADER SAFETY
//
// Intentionally NO:
//
// window.loadPage = loadPage;
//
// Intentionally NO:
//
// window.__REAL_LOAD_PAGE__ = ...
//
// Intentionally NO:
//
// window.__PAGE_LOADER_CORE_LOAD_PAGE__ = ...
//
// Those belong to PageLoader only.
//
////////////////////////////////////////////////////////////


////////////////////////////////////////////////////////////
// 💀 GLOBAL ERROR DIAGNOSTIC
////////////////////////////////////////////////////////////

if(
    typeof window.addEventListener ===
    "function"
){

    window.addEventListener(
        "error",
        event => {

            console.log(
                "💀 ERROR IN FILE:",
                event.filename,
                event.message
            );

        }
    );

}


////////////////////////////////////////////////////////////
// 🔥 CORE READY
////////////////////////////////////////////////////////////

console.log(
    "🔥 MINIGRAM CORE READY"
);

console.log(
    "🛡️ PageLoader Ownership: EXTERNAL"
);

console.log(
    "🚫 Core loadPage Override: OFF"
);
```

---

Generated automatically.
