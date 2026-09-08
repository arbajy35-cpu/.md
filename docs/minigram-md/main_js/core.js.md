# main_js/core.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/core.js` |
| Extension | `.js` |
| Bytes | 9734 |
| Lines | 499 |
| SHA-256 | `7448f0087b8e7ea26d5aabd7964eedad34109ac06f117fad90f761cd6f92c80d` |
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

- `report.json`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `initNavigation`
- `initCore`
- `homeBtn`
- `searchBtn`
- `profileBtn`
- `reelsBtn`
- `createBtn`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **LOW** — Duplicate Filename: core.js appears in 2 locations

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

`/storage/emulated/0/MINIGRAM1/main_js/core.js`

It is NOT AI generated or rewritten.

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

Generated by MiniGram MD Intelligence V6.
