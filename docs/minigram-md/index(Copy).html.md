# index(Copy).html

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `index(Copy).html` |
| Extension | `.html` |
| Bytes | 8823 |
| Lines | 510 |
| SHA-256 | `74c53df161a5f08e6969315872c3d65acf63d8ab0ad65d0ade900c1647047dff` |
| Dependency Depth | 1 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`index(Copy).html`

The local intelligence engine detected
8 direct dependencies
and 0 consumers.

## 5. Dependencies

- `main_js/boot.js`
- `fontawesome/css/fontawesome.min.css`
- `fontawesome/css/solid.min.css`
- `global_css/variables.css`
- `global_css/base.css`
- `global_css/layout.css`
- `global_css/components.css`
- `global_css/animations.css`

## 6. Used By

- None

## 7. Exact Relation Flow

- `index(Copy).html` → `main_js/boot.js` **[html-script]**
- `index(Copy).html` → `fontawesome/css/fontawesome.min.css` **[html-link]**
- `index(Copy).html` → `fontawesome/css/solid.min.css` **[html-link]**
- `index(Copy).html` → `global_css/variables.css` **[html-link]**
- `index(Copy).html` → `global_css/base.css` **[html-link]**
- `index(Copy).html` → `global_css/layout.css` **[html-link]**
- `index(Copy).html` → `global_css/components.css` **[html-link]**
- `index(Copy).html` → `global_css/animations.css` **[html-link]**
- `index(Copy).html` → `fontawesome/css/fontawesome.min.css` **[html-asset]**
- `index(Copy).html` → `fontawesome/css/solid.min.css` **[html-asset]**
- `index(Copy).html` → `global_css/variables.css` **[html-asset]**
- `index(Copy).html` → `global_css/base.css` **[html-asset]**
- `index(Copy).html` → `global_css/layout.css` **[html-asset]**
- `index(Copy).html` → `global_css/components.css` **[html-asset]**
- `index(Copy).html` → `global_css/animations.css` **[html-asset]**
- `index(Copy).html` → `main_js/boot.js` **[html-asset]**
- `index(Copy).html` → `fontawesome/css/fontawesome.min.css` **[string-path]**
- `index(Copy).html` → `fontawesome/css/solid.min.css` **[string-path]**
- `index(Copy).html` → `global_css/variables.css` **[string-path]**
- `index(Copy).html` → `global_css/base.css` **[string-path]**
- `index(Copy).html` → `global_css/layout.css` **[string-path]**
- `index(Copy).html` → `global_css/components.css` **[string-path]**
- `index(Copy).html` → `global_css/animations.css` **[string-path]**
- `index(Copy).html` → `main_js/boot.js` **[string-path]**

## 8. Local Symbols

- None

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **MEDIUM** — Broken HTML Reference: html-asset: eruda.min.js

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

`/storage/emulated/0/MINIGRAM1/index(Copy).html`

It is NOT AI generated or rewritten.

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

<title>MINIGRAM</title>


<!-- =====================================================
     CRITICAL FIRST PAINT
===================================================== -->

<style>

*{
    box-sizing:border-box;
}

html,
body{
    margin:0;
    padding:0;
    width:100%;
    min-height:100%;
    background:#000;
    color:#fff;
}

body{
    overflow-x:hidden;
    background:#000;
}

#app,
#mainContent{
    width:100%;
    min-height:100vh;
    background:#000;
}

#mainContent{
    visibility:visible;
}

#appbar,
#bottomNav{
    width:100%;
}

.hidden{
    display:none !important;
}


/* =====================================================
   INSTANT SKELETON CSS
===================================================== */

.instant-skeleton{
    width:100%;
    min-height:100vh;
    background:#000;
}

.skel-stories{
    display:flex;
    gap:13px;
    padding:12px 14px;
    overflow:hidden;
    border-bottom:1px solid rgba(255,255,255,.07);
}

.skel-story{
    flex:0 0 64px;
    width:64px;
    height:64px;
    border-radius:50%;
    background:#171717;
}

.skel-post{
    width:100%;
    border-bottom:1px solid rgba(255,255,255,.07);
}

.skel-user{
    height:58px;
    display:flex;
    align-items:center;
    gap:10px;
    padding:10px 13px;
}

.skel-avatar{
    width:36px;
    height:36px;
    flex:0 0 36px;
    border-radius:50%;
    background:#171717;
}

.skel-name{
    width:90px;
    height:10px;
    border-radius:5px;
    background:#171717;
}

.skel-media{
    width:100%;
    aspect-ratio:1/1;
    background:#111;
}


/* Very light shimmer.
   No expensive animation on low-end devices. */

@media (prefers-reduced-motion:no-preference){

    .instant-skeleton .skel-avatar,
    .instant-skeleton .skel-name,
    .instant-skeleton .skel-story,
    .instant-skeleton .skel-media{

        animation:miniSkeletonPulse 1.2s
                   ease-in-out infinite alternate;

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

</style>


<!-- =====================================================
     CONNECTION WARM-UP
===================================================== -->

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


<!-- =====================================================
     FONTS
===================================================== -->

<link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined"
>

<link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@500;600&family=Open+Sans:wght@400;500&family=Poppins:wght@500;600&display=swap"
>


<!-- =====================================================
     FONT AWESOME
===================================================== -->

<link
    rel="stylesheet"
    href="fontawesome/css/fontawesome.min.css"
>

<link
    rel="stylesheet"
    href="fontawesome/css/solid.min.css"
>


<!-- =====================================================
     CORE CSS
===================================================== -->

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

</head>


<body>

<div id="app">


<!-- =====================================================
     LOADER
===================================================== -->

<div id="loader">

    <div class="simpleSpinner"></div>

</div>


<!-- =====================================================
     APPBAR
===================================================== -->

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


<!-- =====================================================
     SINGLE PAGE OWNER
===================================================== -->

<main id="mainContent"></main>


<!-- =====================================================
     TOAST
===================================================== -->

<div
    class="toast"
    id="toast"
></div>


<!-- =====================================================
     OFFLINE
===================================================== -->

<div
    id="offlineIndicator"
    style="
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
    "
>
    Offline — showing saved content
</div>


<!-- =====================================================
     BOTTOM NAV
===================================================== -->

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


<!-- =====================================================
     DEBUG
===================================================== -->

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

    script.src = "eruda.min.js";

    script.onload = function(){

        window.eruda?.init();

    };

    document.body.appendChild(script);

})();

</script>


<!-- =====================================================
     OFFLINE
===================================================== -->

<script>

(function(){

    function updateNetwork(){

        document.body.classList.toggle(
            "offline",
            !navigator.onLine
        );

        const indicator =
            document.getElementById(
                "offlineIndicator"
            );

        if(indicator){

            indicator.style.display =
                navigator.onLine
                    ? "none"
                    : "block";

        }

    }

    updateNetwork();

    window.addEventListener(
        "online",
        updateNetwork,
        {passive:true}
    );

    window.addEventListener(
        "offline",
        updateNetwork,
        {passive:true}
    );

})();

</script>


<!-- =====================================================
     BOOT
===================================================== -->

<script
    src="main_js/boot.js"
    defer
></script>


</body>

</html>
```

---

Generated by MiniGram MD Intelligence V6.
