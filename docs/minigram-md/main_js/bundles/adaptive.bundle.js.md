# main_js/bundles/adaptive.bundle.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/bundles/adaptive.bundle.js` |
| Extension | `.js` |
| Bytes | 17013 |
| Lines | 933 |
| SHA-256 | `c22edb3aa3ee0b1c5a93ab8da495a8a5c9ff3182b691ec343f2c4fb86670e715` |
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

- `updateMode`
- `updateBox`
- `applyModeIfNeeded`
- `measureFrame`
- `startMeasurement`
- `scheduler`
- `sample`
- `s`
- `config`
- `id`
- `adaptive`
- `root`
- `file`
- `modeData`
- `key`
- `page`
- `data`
- `FPS_CONFIG`
- `box`
- `measuring`
- `frameCount`
- `sampleStart`
- `lastMeasure`
- `rafId`
- `lastAdaptiveApply`
- `current`
- `mode`
- `color`
- `now`
- `previous`
- `elapsed`
- `fps`
- `changed`
- `timer`
- `load`
- `longTaskTime`
- `observer`
- `entry`
- `start`
- `delay`
- `timerLoad`
- `taskLoad`
- `target`
- `value`

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

`/storage/emulated/0/MINIGRAM1/main_js/bundles/adaptive.bundle.js`

It is NOT AI generated or rewritten.

```javascript


/*
==================================================
🚀 MINIGRAM BUNDLE
FILE: adaptive.bundle.js
GENERATED: 2026-08-29T07:28:40.403Z
SOURCE FILES: 3
==================================================
*/



/* =================================================
   FILE: page_config/adaptive_system/core/adaptive.js
   ================================================= */

//////////////////////////////////////////////////
// 🚀 ADAPTIVE ENGINE
//////////////////////////////////////////////////

console.log("🚀 adaptive.js loaded");

//////////////////////////////////////////////////
// 🌍 PERFORMANCE MODE
//////////////////////////////////////////////////

window.performanceMode =
  window.performanceMode || "high";

//////////////////////////////////////////////////
// 🧠 GLOBAL STORAGE
//////////////////////////////////////////////////

window.ADAPTIVE =
  window.ADAPTIVE || {};

//////////////////////////////////////////////////
// 🔴 MASTER SWITCH
//
// false = EVERYTHING OFF
// true  = adaptive system ON
//////////////////////////////////////////////////

window.ADAPTIVE_ENABLED = false;


//////////////////////////////////////////////////
// 📦 LOAD ADAPTIVE FILE
//////////////////////////////////////////////////

window.loadAdaptive =
async function(id){

  // 🔴 COMPLETELY DISABLED
  if(!window.ADAPTIVE_ENABLED){

    return;

  }

  // Already loaded
  if(window.ADAPTIVE?.[id])
    return;


  const s =
    document.createElement("script");

  s.src =
    `page_config/adaptive_system/adaptive_loader_${id}.js`;


  await new Promise((resolve, reject) => {

    s.onload = resolve;

    s.onerror = reject;

    document.body.appendChild(s);

  });

};


//////////////////////////////////////////////////
// 🎨 APPLY ADAPTIVE
//////////////////////////////////////////////////

window.applyAdaptive =
async function(page){

  // 🔴 COMPLETELY DISABLED
  if(!window.ADAPTIVE_ENABLED){

    return;

  }


  const config =
    window.PAGE_CONFIG?.[page];

  if(!config?.adaptive)
    return;


  const id =
    config.adaptive;


  await window.loadAdaptive(id);


  const adaptive =
    window.ADAPTIVE?.[id];

  if(!adaptive)
    return;


  const root =
    document.documentElement;


  for(const file in adaptive){

    if(file === "load")
      continue;


    const modeData =
      adaptive[file]?.[
        window.performanceMode
      ];


    if(!modeData)
      continue;


    for(const key in modeData){

      if(
        typeof modeData[key] !==
        "object"
      ){

        root.style.setProperty(
          `--${key}`,
          modeData[key]
        );

      }

    }

  }

};


//////////////////////////////////////////////////
// ⚡ GET ADAPTIVE DATA
//////////////////////////////////////////////////

window.getAdaptiveData =
function(file){

  // 🔴 COMPLETELY DISABLED
  if(!window.ADAPTIVE_ENABLED){

    return {};

  }


  const page =
    window.CURRENT_PAGE;

  const config =
    window.PAGE_CONFIG?.[page];

  if(!config?.adaptive)
    return {};


  const id =
    config.adaptive;


  const data =
    window.ADAPTIVE?.[id]?.[file];


  if(!data)
    return {};


  return (
    data[
      window.performanceMode
    ] || {}
  );

};

/* =================================================
   END: page_config/adaptive_system/core/adaptive.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/fps.js
   ================================================= */

//////////////////////////////////////////////////
// ⚡ MINIGRAM FPS ENGINE
// Lightweight + Stable Adaptive Controller
//////////////////////////////////////////////////

console.log("⚡ fps.js loaded");

//////////////////////////////////////////////////
// GLOBAL PERFORMANCE STATE
//////////////////////////////////////////////////

window.performanceMode =
  window.performanceMode || "high";

window.__LAST_MODE =
  window.__LAST_MODE || window.performanceMode;

window.__FPS =
  window.__FPS || 60;

window.__FPS_DROP_COUNT = 0;
window.__FPS_RISE_COUNT = 0;

//////////////////////////////////////////////////
// CONFIG
//////////////////////////////////////////////////

const FPS_CONFIG = {

  // Measure only once every 2 seconds
  sampleInterval: 2000,

  // Actual frame sampling window
  sampleDuration: 700,

  // Prevent adaptive re-application spam
  adaptiveCooldown: 4000,

  // Require stable readings
  lowConfirm: 2,
  highConfirm: 3

};

//////////////////////////////////////////////////
// FPS BOX
//////////////////////////////////////////////////

(function () {

  let box =
    document.querySelector("#fpsBox");

  //////////////////////////////////////////////////
  // CREATE ONLY IF NEEDED
  //////////////////////////////////////////////////

  if (!box) {

    box =
      document.createElement("div");

    box.id = "fpsBox";

    box.style.position = "fixed";
    box.style.top = "50%";
    box.style.right = "6px";

    box.style.transform =
      "translateY(-50%)";

    box.style.padding =
      "4px 7px";

    box.style.fontSize =
      "10px";

    box.style.fontWeight =
      "600";

    box.style.color =
      "#0f0";

    box.style.background =
      "rgba(0,0,0,.45)";

    box.style.borderRadius =
      "7px";

    // No backdrop-filter
    // No transition: all

    box.style.zIndex =
      "999999";

    box.style.pointerEvents =
      "none";

    box.textContent =
      "FPS: -- | HIGH";

    document.body.appendChild(box);

  }

  //////////////////////////////////////////////////
  // STATE
  //////////////////////////////////////////////////

  let measuring = false;

  let frameCount = 0;

  let sampleStart = 0;

  let lastMeasure = 0;

  let rafId = 0;

  let lastAdaptiveApply = 0;

  //////////////////////////////////////////////////
  // MODE DETECTOR
  //////////////////////////////////////////////////

  function updateMode(fps) {

    const current =
      window.performanceMode;

    //////////////////////////////////////////////////
    // LOW
    //////////////////////////////////////////////////

    if (fps < 25) {

      window.__FPS_DROP_COUNT++;

      window.__FPS_RISE_COUNT = 0;

      if (
        window.__FPS_DROP_COUNT >=
        FPS_CONFIG.lowConfirm
      ) {

        if (current !== "low") {

          window.performanceMode =
            "low";

          return true;

        }

      }

      return false;
    }

    //////////////////////////////////////////////////
    // MID
    //////////////////////////////////////////////////

    if (fps < 45) {

      window.__FPS_DROP_COUNT = 0;
      window.__FPS_RISE_COUNT = 0;

      if (current === "low") {

        // Don't immediately jump upward
        return false;

      }

      if (current !== "mid") {

        window.performanceMode =
          "mid";

        return true;

      }

      return false;
    }

    //////////////////////////////////////////////////
    // HIGH
    //////////////////////////////////////////////////

    window.__FPS_RISE_COUNT++;

    window.__FPS_DROP_COUNT = 0;

    if (
      window.__FPS_RISE_COUNT >=
      FPS_CONFIG.highConfirm
    ) {

      if (current !== "high") {

        window.performanceMode =
          "high";

        return true;

      }

    }

    return false;

  }

  //////////////////////////////////////////////////
  // UI
  //////////////////////////////////////////////////

  function updateBox(fps) {

    const mode =
      window.performanceMode;

    let color;

    if (mode === "high") {

      color = "#00ff99";

    } else if (mode === "mid") {

      color = "#ffd500";

    } else {

      color = "#ff4444";

    }

    box.style.color =
      color;

    box.textContent =
      `FPS: ${fps} | ${mode.toUpperCase()}`;

  }

  //////////////////////////////////////////////////
  // APPLY ADAPTIVE SAFELY
  //////////////////////////////////////////////////

  function applyModeIfNeeded() {

    const mode =
      window.performanceMode;

    if (
      mode === window.__LAST_MODE
    ) {

      return;

    }

    const now =
      performance.now();

    //////////////////////////////////////////////////
    // COOLDOWN
    //////////////////////////////////////////////////

    if (
      now - lastAdaptiveApply <
      FPS_CONFIG.adaptiveCooldown
    ) {

      return;

    }

    //////////////////////////////////////////////////
    // SAVE
    //////////////////////////////////////////////////

    const previous =
      window.__LAST_MODE;

    window.__LAST_MODE =
      mode;

    lastAdaptiveApply =
      now;

    console.log(
      "⚡ MODE:",
      previous,
      "→",
      mode
    );

    //////////////////////////////////////////////////
    // APPLY
    //////////////////////////////////////////////////

    if (
      window.CURRENT_PAGE &&
      typeof window.applyAdaptive ===
      "function"
    ) {

      window.applyAdaptive(
        window.CURRENT_PAGE
      );

    }

  }

  //////////////////////////////////////////////////
  // MEASUREMENT FRAME
  //////////////////////////////////////////////////

  function measureFrame(now) {

    if (!measuring) {

      return;

    }

    frameCount++;

    //////////////////////////////////////////////////
    // FINISH SAMPLE
    //////////////////////////////////////////////////

    if (
      now - sampleStart >=
      FPS_CONFIG.sampleDuration
    ) {

      const elapsed =
        now - sampleStart;

      const fps =
        Math.round(
          (frameCount * 1000) /
          elapsed
        );

      window.__FPS =
        Math.max(
          0,
          Math.min(120, fps)
        );

      const changed =
        updateMode(
          window.__FPS
        );

      updateBox(
        window.__FPS
      );

      if (changed) {

        applyModeIfNeeded();

      }

      measuring = false;

      frameCount = 0;

      rafId = 0;

      return;

    }

    //////////////////////////////////////////////////
    // NEXT FRAME ONLY DURING SAMPLE
    //////////////////////////////////////////////////

    rafId =
      requestAnimationFrame(
        measureFrame
      );

  }

  //////////////////////////////////////////////////
  // START SAMPLE
  //////////////////////////////////////////////////

  function startMeasurement(now) {

    if (measuring) {

      return;

    }

    measuring = true;

    frameCount = 0;

    sampleStart = now;

    rafId =
      requestAnimationFrame(
        measureFrame
      );

  }

  //////////////////////////////////////////////////
  // SCHEDULER
  //////////////////////////////////////////////////

  function scheduler(now) {

    //////////////////////////////////////////////////
    // Only start a sample after interval
    //////////////////////////////////////////////////

    if (
      !measuring &&
      now - lastMeasure >=
      FPS_CONFIG.sampleInterval
    ) {

      lastMeasure =
        now;

      startMeasurement(now);

    }

    //////////////////////////////////////////////////
    // Scheduler itself is NOT continuous RAF.
    // Use a low-frequency timer.
    //////////////////////////////////////////////////

  }

  //////////////////////////////////////////////////
  // LOW-FREQUENCY TIMER
  //////////////////////////////////////////////////

  const timer =
    setInterval(() => {

      scheduler(
        performance.now()
      );

    }, 2500);

  //////////////////////////////////////////////////
  // INITIAL SAMPLE
  //////////////////////////////////////////////////

  setTimeout(() => {

    lastMeasure =
      performance.now();

    startMeasurement(
      performance.now()
    );

  }, 500);

  //////////////////////////////////////////////////
  // CLEANUP
  //////////////////////////////////////////////////

  window.__FPS_STOP =
    function () {

      clearInterval(timer);

      if (rafId) {

        cancelAnimationFrame(
          rafId
        );

        rafId = 0;

      }

      measuring = false;

    };

})();

//////////////////////////////////////////////////
// ERROR LOGGER
//////////////////////////////////////////////////

window.addEventListener?.(
  "error",
  e => {

    console.log(
      "💀 FPS ERROR:",
      e.filename,
      e.message
    );

  }
);

/* =================================================
   END: main_js/pageloader/fps.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/cpu.js
   ================================================= */

//////////////////////////////////////////////////
// 🧠 LIGHTWEIGHT PERFORMANCE MONITOR
// Main-thread load estimate — NOT real hardware CPU %
//////////////////////////////////////////////////

console.log("🧠 cpu.js loaded (lightweight)");

(function () {

  const box = document.createElement("div");

  box.style.position = "fixed";
  box.style.top = "55%";
  box.style.right = "6px";

  box.style.padding = "4px 6px";
  box.style.fontSize = "10px";
  box.style.fontWeight = "600";

  box.style.background = "rgba(0,0,0,.5)";
  box.style.borderRadius = "6px";

  box.style.zIndex = "999999";
  box.style.pointerEvents = "none";

  document.body.appendChild(box);


  //////////////////////////////////////////////////
  // STATE
  //////////////////////////////////////////////////

  let load = 0;
  let longTaskTime = 0;

  let observer = null;


  //////////////////////////////////////////////////
  // LONG TASK MONITOR
  //////////////////////////////////////////////////

  if ("PerformanceObserver" in window) {

    try {

      observer = new PerformanceObserver(list => {

        for (const entry of list.getEntries()) {

          longTaskTime += entry.duration;

        }

      });

      observer.observe({
        type: "longtask",
        buffered: false
      });

    } catch (e) {

      // Long Task API unavailable
      observer = null;

    }

  }


  //////////////////////////////////////////////////
  // MAIN THREAD SAMPLE
  //////////////////////////////////////////////////

  function sample() {

    const start = performance.now();

    setTimeout(() => {

      const delay =
        performance.now() - start;

      /*
       * Expected timer delay is roughly a few ms.
       * Higher delay = busier main thread.
       */

      const timerLoad =
        Math.max(
          0,
          Math.min(
            100,
            (delay - 4) * 5
          )
        );


      //////////////////////////////////////////////////
      // LONG TASK LOAD
      //////////////////////////////////////////////////

      const taskLoad =
        Math.max(
          0,
          Math.min(
            100,
            longTaskTime / 5
          )
        );

      longTaskTime = 0;


      //////////////////////////////////////////////////
      // COMBINE
      //////////////////////////////////////////////////

      const target =
        Math.max(
          timerLoad,
          taskLoad
        );


      //////////////////////////////////////////////////
      // SMOOTH
      //////////////////////////////////////////////////

      load =
        load * 0.75 +
        target * 0.25;


      //////////////////////////////////////////////////
      // UI
      //////////////////////////////////////////////////

      const value =
        Math.round(load);


      if (value < 30) {

        box.style.color = "#0f0";

      } else if (value < 60) {

        box.style.color = "#ff0";

      } else {

        box.style.color = "#f00";

      }


      box.textContent =
        `CPU: ${value}%`;


      //////////////////////////////////////////////////
      // NEXT SAMPLE
      //////////////////////////////////////////////////

      setTimeout(sample, 500);

    }, 0);

  }


  //////////////////////////////////////////////////
  // START
  //////////////////////////////////////////////////

  sample();


})();

/* =================================================
   END: main_js/pageloader/cpu.js
   ================================================= */


```

---

Generated by MiniGram MD Intelligence V6.
