# critical_css/search_critical.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `critical_css/search_critical.css` |
| Extension | `.css` |
| Bytes | 7028 |
| Lines | 432 |
| SHA-256 | `0db813162d812de8ba145f539b4c059a994f64a153324aa47888b67755e36a72` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`critical_css`

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

- None

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

`/storage/emulated/0/MINIGRAM1/critical_css/search_critical.css`

It is NOT AI generated or rewritten.

```css
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
```

---

Generated by MiniGram MD Intelligence V6.
