# reel/reels.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `reel/reels.js` |
| Extension | `.js` |
| Bytes | 4406 |
| Lines | 220 |
| SHA-256 | `c3481addc879647c2869956c00cbf35f00236c657fe00d6a5cfb8bd72cc1c5ee` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`reel`

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

- `watchIndex`
- `loop`
- `initReels`
- `destroyReels`
- `dummy`
- `s`
- `video`
- `p`
- `last`
- `state`
- `container`

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

`/storage/emulated/0/MINIGRAM1/reel/reels.js`

It is NOT AI generated or rewritten.

```javascript
console.log("🎥 reels.js loaded");

// ================================
// GLOBAL HOLDER
// ================================
window.FUNCTIONS = window.FUNCTIONS || {};

// ================================
// 📦 DUMMY DATA (FIXED)
// ================================
window.loadDummy = function(){

  const dummy = [
    {
      video: "https://www.w3schools.com/html/mov_bbb.mp4",
      user: "Demo",
      likes: 120
    },
    {
      video: "https://www.w3schools.com/html/movie.mp4",
      user: "Test",
      likes: 90
    }
  ];

  const s = window.REELS_STATE;

  s.data = dummy; // 🔥 IMPORTANT SYNC FIX

  window.appendReels(dummy);
};

// ================================
// 🔥 RENDER ENGINE (SAFE)
// ================================
window.render = function(){

  const s = window.REELS_STATE;
  if (!s || !s.container) return;

  s.reels.forEach((reel, i) => {

    // 🔥 SAFETY GUARD (IMPORTANT FIX)
    if (i >= s.reels.length) return;

    reel.style.transform = `translateY(${(i - s.index) * 100}%)`;

    const video = reel.querySelector("video");
    if (!video) return;

    if (i === s.index) {

      const p = video.play?.();
      if (p !== undefined) p.catch(()=>{});

      window.startProgress?.(reel, video);

    } else {

      video.pause();
      video.currentTime = 0;
    }

  });

};

// ================================
// AUTO WATCHER
// ================================
function watchIndex(){

  let last = -1;

  function loop(){

    const s = window.REELS_STATE;
    if (!s) return requestAnimationFrame(loop);

    if (s.index !== last){
      last = s.index;
      window.render?.();
    }

    requestAnimationFrame(loop);
  }

  loop();
}

// ================================
// 🚀 INIT REELS
// ================================
async function initReels(){

  // 🔥 SAFE WAIT LOOP
  while (true) {
    if (typeof window.appendReels === "function") break;
    await new Promise(function(resolve){
      setTimeout(resolve, 20);
    });
  }

  console.log("✅ appendReels ready");

  // ================================
  // STATE INIT
  // ================================
  if(!window.REELS_STATE){
    window.REELS_STATE = {
      container: null,
      reels: [],
      data: [],
      index: 0,
      isFetching: false,
      lastId: null
    };
  }

  const state = window.REELS_STATE;

  const container = document.querySelector(".reelsContainer");

  if(!container){
    console.error("❌ reelsContainer not found");
    return;
  }

  state.container = container;

  container.style.opacity = "0";

  state.reels = [];
  state.data = [];
  state.index = 0;
  state.isFetching = false;

  container.innerHTML = "";

  console.log("🔄 Reset done");

  // ================================
  // SWIPE INIT
  // ================================
  try{
    window.initSwipe?.();
  }catch(e){
    console.warn(e);
  }

  // ================================
  // WATCHER
  // ================================
  watchIndex();

  // ================================
  // DATA LOAD
  // ================================
  try{

    if(window.supabase){

      await window.fetchReels?.();

      if(state.reels.length === 0){
        window.loadDummy();
      }

    } else {

      window.loadDummy();

    }

  } catch(e){

    window.loadDummy();

  }

  window.render();

  requestAnimationFrame(()=>{
    container.style.opacity = "1";
  });
}

// ================================
// DESTROY
// ================================
function destroyReels(){

  const state = window.REELS_STATE;
  if(!state) return;

  document.querySelectorAll("video").forEach(v=>{
    v.pause();
    v.currentTime = 0;
  });

  if(state.container){
    state.container.innerHTML = "";
  }

  state.reels = [];
  state.data = [];
  state.index = 0;

  console.log("🧹 destroyed");
}

// ================================
// EXPORT
// ================================
window.initReels = initReels;
window.destroyReels = destroyReels;
window.FUNCTIONS.initReels = initReels;
window.FUNCTIONS.destroyReels = destroyReels;
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
