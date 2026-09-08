# reels/swipe.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `reels/swipe.js` |
| Extension | `.js` |
| Bytes | 3994 |
| Lines | 155 |
| SHA-256 | `c62015dfccfd42cf0b3ef40e3f2d16f43fcc69754a61c70aa1300c1459f04729` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`reels`

The local intelligence engine detected
0 direct dependencies
and 2 consumers.

## 5. Dependencies

- None

## 6. Used By

- `reels/main.js`
- `reels/reels.bundle.js`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `initSwipe`
- `s`
- `el`
- `startY`
- `currentY`
- `startTime`
- `isDragging`
- `delta`
- `currentReel`
- `time`
- `velocity`
- `shouldSwipe`

## 9. Exports

- `default/export`

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **HIGH** — JavaScript Syntax Error: Unexpected token 'export'

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

`/storage/emulated/0/MINIGRAM1/reels/swipe.js`

It is NOT AI generated or rewritten.

```javascript
console.log("🖐️ swipe.js loaded");

// ================================
// 🧠 GLOBAL HANDLERS
// ================================
window._reelsTouchStart = null;
window._reelsTouchMove = null;
window._reelsTouchEnd = null;

function initSwipe(){

  const s = window.REELS_STATE;
  const el = s?.container;

  if (!el) {
    console.warn("❌ Swipe: no container");
    return;
  }

  let startY = 0;
  let currentY = 0;
  let startTime = 0;
  let isDragging = false;

  // ================================
  // 👆 TOUCH START
  // ================================
  window._reelsTouchStart = function(e){
    startY = e.touches[0].clientY;
    currentY = startY;
    startTime = Date.now();
    isDragging = true;
  };

  // ================================
  // 👆 TOUCH MOVE (SMOOTH DRAG)
  // ================================
  window._reelsTouchMove = function(e){

    if (!isDragging) return;

    currentY = e.touches[0].clientY;
    const delta = currentY - startY;

    const currentReel = s.reels[s.index];
    if (!currentReel) return;

    // 🔥 live drag effect
    currentReel.style.transition = "none";
    currentReel.style.transform = `translateY(${delta}px)`;
  };

  // ================================
  // ✋ TOUCH END
  // ================================
  window._reelsTouchEnd = function(){

    if (!isDragging) return;
    isDragging = false;

    const delta = currentY - startY;
    const time = Date.now() - startTime;

    const velocity = Math.abs(delta) / time;

    // 🔥 SMART THRESHOLD
    const shouldSwipe =
      Math.abs(delta) > 80 || velocity > 0.5;

    if (shouldSwipe){
      if (delta < 0){
        s.index++; // up
      } else {
        s.index--; // down
      }
    }

    // 🔥 LIMIT
    s.index = Math.max(0, Math.min(s.index, s.reels.length - 1));

    console.log("👉 index:", s.index);

    // ================================
    // 🎯 RESET POSITIONS
    // ================================
    s.reels.forEach((reel, i) => {
      reel.style.transition = "transform 0.3s ease";
      reel.style.transform = `translateY(${(i - s.index) * 100}%)`;
    });

    // ================================
    // 🎥 AUTO PLAY / PAUSE
    // ================================
    s.reels.forEach((reel, i) => {
      if (i === s.index){
        reel.play?.();
      } else {
        reel.pause?.();
      }
    });

    // ================================
    // 📡 PRELOAD NEXT
    // ================================
    window.preloadNext?.();
  };

  // ================================
  // 🚀 ADD EVENTS
  // ================================
  el.addEventListener("touchstart", window._reelsTouchStart, { passive: true });
  el.addEventListener("touchmove", window._reelsTouchMove, { passive: true });
  el.addEventListener("touchend", window._reelsTouchEnd, { passive: true });

}

window.initSwipe = initSwipe;


// ================================
// 🧹 DESTROY SYSTEM
// ================================
window.FUNCTIONS = window.FUNCTIONS || {};

window.FUNCTIONS.reelsDestroy = function(){

  const s = window.REELS_STATE;
  const el = s?.container;

  if (el){
    if (window._reelsTouchStart){
      el.removeEventListener("touchstart", window._reelsTouchStart);
    }
    if (window._reelsTouchMove){
      el.removeEventListener("touchmove", window._reelsTouchMove);
    }
    if (window._reelsTouchEnd){
      el.removeEventListener("touchend", window._reelsTouchEnd);
    }
  }

  window._reelsTouchStart = null;
  window._reelsTouchMove = null;
  window._reelsTouchEnd = null;

  console.log("🧹 reels cleaned");
};


// ================================
// 🔥 ESBUILD FIX
// ================================
export {};
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
