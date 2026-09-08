# home/home.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `home/home.css` |
| Extension | `.css` |
| Bytes | 8589 |
| Lines | 620 |
| SHA-256 | `f15cd8c3c2ca2b187d8e24822c1eb5a292c67f9b7f59a50eb252d1dcc34e4ab2` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`home`

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

`/storage/emulated/0/MINIGRAM1/home/home.css`

It is NOT AI generated or rewritten.

```css
/* ==================================================
    MINIGRAM HOME CSS (FINAL LIGHTWEIGHT)
================================================== */

/* ===== ROOT ===== */
:root{

  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 12px;
  --space-lg: 16px;

  --text-main:
  rgba(255,255,255,.95);

  --text-secondary:
  rgba(255,255,255,.75);

  --text-muted:
  rgba(255,255,255,.4);

  --bottom-nav-height: 75px;

  --hover-opacity: .06;

  --anim-speed: .18;

}

/* ===== GLOBAL ===== */
*{

  box-sizing: border-box;

}

/* ===== HTML / BODY ===== */
html,
body{
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100%;

  overflow: hidden;
  overflow-x: hidden;

  background: #000;

  -webkit-overflow-scrolling: touch;
  text-rendering: optimizeSpeed;
}

/* ===== HOME ROOT � SMOOTH + CPU FRIENDLY ===== */
#homeRoot {
  width: 100%;

  /* Appbar ke neeche exactly viewport */
  height: calc(100dvh - 59px);
  min-height: 0;
  max-height: calc(100dvh - 59px);

  display: flex;
  flex-direction: column;

  overflow-x: hidden;
  overflow-y: auto;

  padding-bottom: calc(
    var(--bottom-nav-height) + 10px
  );

  box-sizing: border-box;

  /* Native smooth scrolling */
  -webkit-overflow-scrolling: touch;

  /* Prevent scroll chaining */
  overscroll-behavior-y: contain;

  /* Avoid scroll anchoring jumps */
  overflow-anchor: auto;

  /* Don't force GPU compositing */
  transform: none;
  will-change: auto;
}

/* ===== FEED ===== */
.feed{

  display: flex;

  flex-direction: column;

  width: 100%;

  height: auto;

  overflow: visible;

  padding-bottom:
  var(--bottom-nav-height);

}

/* ===== POST � GPU/CPU FRIENDLY ===== */
.post {
  width: 100%;
  display: flex;
  flex-direction: column;

  margin-bottom: var(--space-sm);

  border-bottom: 1px solid rgba(255,255,255,.04);

  /* No forced GPU layer */
  overflow: visible;

  /* CPU-friendly */
  animation: none;
}

/* ===== NO ANIMATION ===== */
.noAnim{

  animation: none !important;

}

/* ===== HEADER ===== */
.postHeader{

  display: flex;

  align-items: center;

  justify-content: space-between;

  padding:
  var(--space-md);

}

.postHeaderLeft{

  display: flex;

  align-items: center;

  gap:
  var(--space-sm);

}

/* ===== AVATAR ===== */
.avatar{

  width: 34px;

  height: 34px;

  border-radius: 50%;

  object-fit: cover;

  display: block;

  background: #111;

}

/* ===== REMOVE SHADOW ===== */
.noShadow .avatar{

  box-shadow: none !important;

}

/* ===== USERNAME ===== */
.username{

  font-size: 14px;

  font-weight: 600;

  letter-spacing: .2px;

  color:
  var(--text-main);

}

/* =========================================
   POST IMAGE � LIGHTWEIGHT
========================================= */

.postImageContainer {
  width: 100%;
  aspect-ratio: 1 / 1;

  background: #0a0a0a;

  border-top: 1px solid rgba(255,255,255,.03);
  border-bottom: 1px solid rgba(255,255,255,.03);

  /* No contain / forced GPU layer */
}

/* ===== IMAGE � LIGHTWEIGHT ===== */
.postImage {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;

  image-rendering: auto;
}

/* ===== ACTIONS ===== */
.postActions{

  display: flex;

  align-items: center;

  justify-content: space-between;

  padding:
  var(--space-sm)
  var(--space-md);

}

.postActionsLeft{

  display: flex;

  align-items: center;

  gap:
  var(--space-sm);

}

/* ===== BUTTON ===== */
.postActionsLeft button{

  width: 36px;

  height: 36px;

  padding: 0;

  border: none;

  outline: none;

  cursor: pointer;

  border-radius: 10px;

  background: transparent;

  display: flex;

  align-items: center;

  justify-content: center;

  /*  LIGHTWEIGHT */
  transition:
  background .15s ease,
  opacity .12s ease;

}

/* ===== HOVER ===== */
.postActionsLeft button:hover{

  background:
  rgba(
    255,
    255,
    255,
    var(--hover-opacity)
  );

}

/* ===== ACTIVE ===== */
.postActionsLeft button:active{

  opacity: .7;

  background:
  rgba(255,255,255,.1);

}

/* ===== ICON ===== */
.postActions svg{

  width: 22px;

  height: 22px;

  flex-shrink: 0;

}

/* ===== REMOVE COMMENTS ===== */
.noComments .commentBtn{

  display: none !important;

}

/* ===== LIKES ===== */
.postLikes{

  padding:
  var(--space-sm)
  var(--space-md)
  0;

  font-size: 14px;

  font-weight: 600;

  color:
  var(--text-main);

}

/* ===== CAPTION ===== */
.postCaption{

  padding:
  var(--space-xs)
  var(--space-md);

  font-size: 14px;

  line-height: 1.45;

  color:
  var(--text-secondary);

  word-break: break-word;

  overflow-wrap: break-word;

}

/* ===== CAPTION USERNAME ===== */
.postCaption b{

  font-weight: 600;

  margin-right: 4px;

  color:
  var(--text-main);

}

/* ===== TIME ===== */
.postTime{

  padding:
  var(--space-sm)
  var(--space-md)
  var(--space-md);

  font-size: 11px;

  letter-spacing: .3px;

  color:
  var(--text-muted);

}

/* ===== BOTTOM NAV ===== */
.bottomNav{

  position: fixed;

  bottom: 0;
  left: 0;

  width: 100%;

  height:
  var(--bottom-nav-height);

  z-index: 999;

  /*  NO BLUR */
  backdrop-filter: none;

  -webkit-backdrop-filter: none;

  background:
  rgba(20,20,20,.92);

  border-top:
  1px solid
  rgba(255,255,255,.05);

}

/* ===== LIGHTWEIGHT ANIMATION ===== */
@keyframes fadeIn{

  from{

    opacity: 0;

  }

  to{

    opacity: 1;

  }

}

/* ===== MOBILE ===== */
@media (max-width: 768px){

  .post{

    contain-intrinsic-size: 600px;

  }

  .postActionsLeft button{

    width: 34px;

    height: 34px;

  }

  .postActions svg{

    width: 21px;

    height: 21px;

  }

}

/* ===== LOW-END DEVICES ===== */
@media (prefers-reduced-motion: reduce){

  *{

    animation: none !important;

    transition: none !important;

  }

}

/* =========================================
    LIKE BUTTON FIX
========================================= */

.likeBtn{

  opacity: .75;

  transition:
    transform .15s ease,
    opacity .15s ease;

}

.likeBtn.liked{

  opacity: 1;

  transform: scale(1.08);

}

/*  DEFAULT HEART */

.likeBtn svg{

  fill: none !important;

  color: #fff !important;

  stroke: currentColor !important;

  stroke-width: 2;

}

/*  LIKED HEART */

.likeBtn.liked svg{

  fill: #ff3040 !important;

  color: #ff3040 !important;

  stroke: #ff3040 !important;

}

.postComments{

  padding:
    4px 12px 0;

  font-size: 14px;

  color:
    rgba(255,255,255,.75);

}

/* ==================================================
    HOME PAGE FIX - STORIES + FEED LAYOUT
================================================== */

/* ===== HOME PAGE WRAPPER ===== */
.homePage {
  display: flex;
  flex-direction: column;
  width: 100%;
  min-height: 100vh;
  background: #000;
  padding-bottom: calc(var(--bottom-nav-height) + 10px);
}

/* ===== STORIES SECTION - HORIZONTAL SCROLL ===== */
.stories-container {
  width: 100%;
  padding: 10px 0;
  border-bottom: 1px solid #222;
  flex-shrink: 0;
  background: #000;
}

.stories-wrapper {
  display: flex;
  gap: 12px;
  padding: 0 12px;
  overflow-x: auto;
  overflow-y: hidden;
  scrollbar-width: none;
  -webkit-overflow-scrolling: touch;
}

.stories-wrapper::-webkit-scrollbar {
  display: none;
}

.storyItem {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  flex-shrink: 0;
  cursor: pointer;
}

.storyRing {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  padding: 2px;
  background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
}

.storyRing img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  border: 2px solid #000;
  object-fit: cover;
}

.storyUser {
  color: #fff;
  font-size: 11px;
  max-width: 64px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/* ===== FEED SECTION - IMPORTANT ===== */
.feed-container {
  flex: 1;
  width: 100%;
  overflow: visible;
  min-height: 0;
}

.posts-container {
  width: 100%;
  min-height: 200px;
}

/* Feed bundle ka content yahan aayega */
.posts-container > * {
  width: 100%;
}
```

---

Generated by MiniGram MD Intelligence V6.
