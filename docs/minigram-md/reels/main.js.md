# reels/main.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `reels/main.js` |
| Extension | `.js` |
| Bytes | 10014 |
| Lines | 528 |
| SHA-256 | `b8b15109749b7b4a573e6f20a913b55ef9f5c725ad2b3a641cfe0d13f3dd1ae2` |
| Dependency Depth | 1 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`reels`

The local intelligence engine detected
10 direct dependencies
and 3 consumers.

## 5. Dependencies

- `reels/state.js`
- `reels/utils.js`
- `reels/like.js`
- `reels/progress.js`
- `reels/video.js`
- `reels/swipe.js`
- `reels/create.js`
- `reels/append.js`
- `reels/fetch.js`
- `reels/position.js`

## 6. Used By

- `reels/build.js`
- `reels/package.json`
- `reels/reels.bundle.js`

## 7. Exact Relation Flow

- `reels/main.js` → `reels/state.js` **[import]**
- `reels/main.js` → `reels/utils.js` **[import]**
- `reels/main.js` → `reels/like.js` **[import]**
- `reels/main.js` → `reels/progress.js` **[import]**
- `reels/main.js` → `reels/video.js` **[import]**
- `reels/main.js` → `reels/swipe.js` **[import]**
- `reels/main.js` → `reels/create.js` **[import]**
- `reels/main.js` → `reels/append.js` **[import]**
- `reels/main.js` → `reels/fetch.js` **[import]**
- `reels/main.js` → `reels/position.js` **[import]**
- `reels/main.js` → `reels/state.js` **[string-path]**
- `reels/main.js` → `reels/utils.js` **[string-path]**
- `reels/main.js` → `reels/like.js` **[string-path]**
- `reels/main.js` → `reels/progress.js` **[string-path]**
- `reels/main.js` → `reels/video.js` **[string-path]**
- `reels/main.js` → `reels/swipe.js` **[string-path]**
- `reels/main.js` → `reels/create.js` **[string-path]**
- `reels/main.js` → `reels/append.js` **[string-path]**
- `reels/main.js` → `reels/fetch.js` **[string-path]**
- `reels/main.js` → `reels/position.js` **[string-path]**

## 8. Local Symbols

- `pauseAllVideos`
- `playSingleVideo`
- `initVisibilitySystem`
- `initPageVisibilityFix`
- `optimizeLowEnd`
- `startReels`
- `videos`
- `video`
- `container`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **HIGH** — JavaScript Syntax Error: Cannot use import statement outside a module

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

`/storage/emulated/0/MINIGRAM1/reels/main.js`

It is NOT AI generated or rewritten.

```javascript
console.log("🔥 REELS MAIN V2 RUNNING");

//////////////////////////////////////////////////
// ✅ FORCE LOAD MODULES
//////////////////////////////////////////////////

import "./state.js";
import "./utils.js";
import "./like.js";
import "./progress.js";
import "./video.js";
import "./swipe.js";
import "./create.js";
import "./append.js";
import "./fetch.js";
import "./position.js";

//////////////////////////////////////////////////
// 🌍 GLOBAL STATE
//////////////////////////////////////////////////

window.__ACTIVE_REEL_VIDEO =
window.__ACTIVE_REEL_VIDEO || null;

window.__REELS_OBSERVER =
window.__REELS_OBSERVER || null;

//////////////////////////////////////////////////
// 📱 LOW-END DETECTION
//////////////////////////////////////////////////

window.IS_LOW_END =

  window.IS_LOW_END ||

  (
    navigator.deviceMemory &&
    navigator.deviceMemory <= 4
  );

//////////////////////////////////////////////////
// 🚀 PAUSE ALL VIDEOS
//////////////////////////////////////////////////

function pauseAllVideos(){

  //////////////////////////////////////////////////
  // 🎥 ALL VIDEOS
  //////////////////////////////////////////////////

  const videos =
    document.querySelectorAll(
      ".reelVideo"
    );

  //////////////////////////////////////////////////
  // 🛑 PAUSE
  //////////////////////////////////////////////////

  videos.forEach(video => {

    try{

      video.pause();

    }catch(e){}

  });

}

//////////////////////////////////////////////////
// 🚀 PLAY ONLY ONE VIDEO
//////////////////////////////////////////////////

function playSingleVideo(video){

  //////////////////////////////////////////////////
  // 🛑 INVALID
  //////////////////////////////////////////////////

  if(!video) return;

  //////////////////////////////////////////////////
  // ⏸️ PAUSE OLD VIDEO
  //////////////////////////////////////////////////

  if(

    window.__ACTIVE_REEL_VIDEO &&

    window.__ACTIVE_REEL_VIDEO !== video

  ){

    try{

      window.__ACTIVE_REEL_VIDEO
        .pause();

    }catch(e){}

  }

  //////////////////////////////////////////////////
  // ▶️ PLAY NEW
  //////////////////////////////////////////////////

  try{

    video.play();

    window.__ACTIVE_REEL_VIDEO =
      video;

  }catch(e){

    console.warn(
      "⚠️ Video play blocked"
    );

  }

}

//////////////////////////////////////////////////
// 🚀 VISIBILITY SYSTEM
//////////////////////////////////////////////////

function initVisibilitySystem(){

  //////////////////////////////////////////////////
  // 🛑 REMOVE OLD
  //////////////////////////////////////////////////

  if(window.__REELS_OBSERVER){

    window.__REELS_OBSERVER
      .disconnect();

  }

  //////////////////////////////////////////////////
  // 👀 OBSERVER
  //////////////////////////////////////////////////

  window.__REELS_OBSERVER =

    new IntersectionObserver(

      entries => {

        entries.forEach(entry => {

          //////////////////////////////////////////////////
          // 🎥 VIDEO
          //////////////////////////////////////////////////

          const video =

            entry.target.querySelector(
              "video"
            );

          if(!video) return;

          //////////////////////////////////////////////////
          // 👁️ VISIBLE
          //////////////////////////////////////////////////

          if(
            entry.isIntersecting &&
            entry.intersectionRatio >= 0.7
          ){

            //////////////////////////////////////////////////
            // ▶️ PLAY ONLY ONE
            //////////////////////////////////////////////////

            playSingleVideo(
              video
            );

          }

          //////////////////////////////////////////////////
          // 🙈 OFFSCREEN
          //////////////////////////////////////////////////

          else{

            try{

              video.pause();

            }catch(e){}

          }

        });

      },

      {
        threshold: [
          0.7
        ]
      }

    );

  //////////////////////////////////////////////////
  // 📦 OBSERVE REELS
  //////////////////////////////////////////////////

  document
    .querySelectorAll(".reel")
    .forEach(reel => {

      window.__REELS_OBSERVER
        .observe(reel);

    });

}

//////////////////////////////////////////////////
// 🚀 PAGE HIDDEN FIX
//////////////////////////////////////////////////

function initPageVisibilityFix(){

  //////////////////////////////////////////////////
  // 👁️ VISIBILITY CHANGE
  //////////////////////////////////////////////////

  document.addEventListener(

    "visibilitychange",

    ()=>{

      //////////////////////////////////////////////////
      // 🛑 APP HIDDEN
      //////////////////////////////////////////////////

      if(document.hidden){

        console.log(
          "⏸️ App Hidden → Pause Videos"
        );

        pauseAllVideos();

      }

      //////////////////////////////////////////////////
      // ▶️ APP BACK
      //////////////////////////////////////////////////

      else{

        console.log(
          "▶️ App Visible"
        );

        //////////////////////////////////////////////////
        // 📱 LOW-END DELAY
        //////////////////////////////////////////////////

        if(window.IS_LOW_END){

          setTimeout(()=>{

            initVisibilitySystem();

          }, 300);

        }

        //////////////////////////////////////////////////
        // ⚡ NORMAL
        //////////////////////////////////////////////////

        else{

          initVisibilitySystem();

        }

      }

    },

    {
      passive: true
    }

  );

}

//////////////////////////////////////////////////
// 🚀 LOW-END OPTIMIZATION
//////////////////////////////////////////////////

function optimizeLowEnd(){

  //////////////////////////////////////////////////
  // 📱 LOW-END CHECK
  //////////////////////////////////////////////////

  if(!window.IS_LOW_END){

    return;

  }

  console.log(
    "📱 LOW-END MODE ENABLED"
  );

  //////////////////////////////////////////////////
  // 🎥 VIDEO OPTIMIZATION
  //////////////////////////////////////////////////

  document
    .querySelectorAll("video")
    .forEach(video => {

      //////////////////////////////////////////////////
      // 🚫 AUTOPLAY
      //////////////////////////////////////////////////

      video.autoplay = false;

      //////////////////////////////////////////////////
      // 📉 LOW QUALITY HINT
      //////////////////////////////////////////////////

      video.preload = "metadata";

      //////////////////////////////////////////////////
      // 🔇 MUTED
      //////////////////////////////////////////////////

      video.muted = true;

      //////////////////////////////////////////////////
      // 📱 INLINE
      //////////////////////////////////////////////////

      video.playsInline = true;

    });

}

//////////////////////////////////////////////////
// 🚀 BOOT SYSTEM
//////////////////////////////////////////////////

async function startReels(){

  console.log(
    "🚀 STARTING REELS..."
  );

  //////////////////////////////////////////////////
  // 📦 CONTAINER
  //////////////////////////////////////////////////

  const container =

    document.querySelector(
      ".reelsContainer"
    );

  //////////////////////////////////////////////////
  // 🛑 NOT FOUND
  //////////////////////////////////////////////////

  if(!container){

    console.error(
      "❌ reelsContainer NOT FOUND"
    );

    return;

  }

  //////////////////////////////////////////////////
  // 🛑 REQUIRED FUNCTIONS
  //////////////////////////////////////////////////

  if(!window.initReelsState){

    console.error(
      "❌ initReelsState missing"
    );

    return;

  }

  if(!window.initSwipe){

    console.error(
      "❌ initSwipe missing"
    );

    return;

  }

  if(!window.fetchReels){

    console.error(
      "❌ fetchReels missing"
    );

    return;

  }

  //////////////////////////////////////////////////
  // 🧠 INIT STATE
  //////////////////////////////////////////////////

  window.initReelsState(
    container
  );

  //////////////////////////////////////////////////
  // 👆 SWIPE
  //////////////////////////////////////////////////

  window.initSwipe();

  //////////////////////////////////////////////////
  // 📱 LOW-END OPTIMIZE
  //////////////////////////////////////////////////

  optimizeLowEnd();

  //////////////////////////////////////////////////
  // 📡 FETCH DATA
  //////////////////////////////////////////////////

  await window.fetchReels();

  //////////////////////////////////////////////////
  // 👀 VISIBILITY OBSERVER
  //////////////////////////////////////////////////

  initVisibilitySystem();

  //////////////////////////////////////////////////
  // 👁️ PAGE VISIBILITY FIX
  //////////////////////////////////////////////////

  initPageVisibilityFix();

  //////////////////////////////////////////////////
  // 🎉 READY
  //////////////////////////////////////////////////

  console.log(
    "✅ REELS STARTED SUCCESSFULLY"
  );

}

//////////////////////////////////////////////////
// ⏳ SAFE START
//////////////////////////////////////////////////

if(
  document.readyState ===
  "loading"
){

  document.addEventListener(

    "DOMContentLoaded",

    startReels

  );

}else{

  startReels();

}

//////////////////////////////////////////////////
// 💀 GLOBAL ERROR LOGGER
//////////////////////////////////////////////////

window.addEventListener?.(

  "error",

  e => {

    console.log(

      "💀 REELS ERROR:",

      e.filename,

      e.message

    );

  }

);

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log(
  "🎉 REELS MAIN V2 READY"
);
```

---

Generated by MiniGram MD Intelligence V6.
