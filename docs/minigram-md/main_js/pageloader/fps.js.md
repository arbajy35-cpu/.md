# main_js/pageloader/fps.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageloader/fps.js` |
| Extension | `.js` |
| Bytes | 9283 |
| Lines | 517 |
| SHA-256 | `07d0609518fb355f7575d15bf7d6b0435bbeb752aaaa6336e0bbba3d3c8ffc91` |
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

`/storage/emulated/0/MINIGRAM1/main_js/pageloader/fps.js`

It is NOT AI generated or rewritten.

```javascript
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
```

---

Generated by MiniGram MD Intelligence V6.
