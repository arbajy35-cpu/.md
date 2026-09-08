# main_js/debugger.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/debugger.js` |
| Extension | `.js` |
| Size | 48393 bytes |
| Lines | 2915 |
| SHA-256 | `a912548fd81dac0ec969801e71540d6b0ec1df18679d125c625b82f8b83fc7df` |

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
main_js/debugger.js
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

`/storage/emulated/0/MINIGRAM1/main_js/debugger.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 🐞 MINIGRAM RENDER DEBUGGER V4
// Forensic Transition + DOM + Overlay +
// Hit-Test + Adaptive + Residue +
// Style Diff + Transition Timeline
//////////////////////////////////////////////////

(function () {

  "use strict";

  const VERSION = "4.0";
  const MAIN_ID = "mainContent";

  console.log(
    `🐞 MINIGRAM RENDER DEBUGGER V${VERSION} START`
  );

  //////////////////////////////////////////////////
  // STATE
  //////////////////////////////////////////////////

  const state = {

    connected: false,

    transition: 0,

    history: [],

    snapshots: [],

    lastAudit: null,

    lastTransition: null,

    waitingForLoader: false

  };

  let originalLoadPage = null;

  //////////////////////////////////////////////////
  // CONFIG
  //////////////////////////////////////////////////

  const PAGE_ROOTS = [

    "#homeRoot",
    "#reelsContainer",
    "#profileRoot",
    "#searchRoot",
    "#chatRoot",
    "#notificationsRoot",
    "#settingsRoot",
    "#savedRoot",
    "#storyRoot",
    "#activityRoot"

  ];

  //////////////////////////////////////////////////
  // UTILS
  //////////////////////////////////////////////////

  function sleep(ms) {

    return new Promise(
      resolve => setTimeout(resolve, ms)
    );

  }

  function describe(el) {

    if (!el) return "NULL";

    const cls =
      typeof el.className === "string"
        ? el.className
            .trim()
            .replace(/\s+/g, ".")
            .slice(0, 150)
        : "";

    return [

      el.tagName
        ? el.tagName.toLowerCase()
        : "?",

      el.id
        ? `#${el.id}`
        : "",

      cls
        ? `.${cls}`
        : ""

    ].join("");

  }

  function rectData(el) {

    if (!el) return null;

    const r =
      el.getBoundingClientRect();

    return {

      top: Math.round(r.top),
      bottom: Math.round(r.bottom),

      left: Math.round(r.left),
      right: Math.round(r.right),

      width: Math.round(r.width),
      height: Math.round(r.height)

    };

  }

  function styleData(el) {

    if (!el) return null;

    const s =
      getComputedStyle(el);

    return {

      position: s.position,

      zIndex: s.zIndex,

      display: s.display,

      visibility: s.visibility,

      opacity: s.opacity,

      pointerEvents:
        s.pointerEvents,

      overflow:
        s.overflow,

      overflowX:
        s.overflowX,

      overflowY:
        s.overflowY,

      transform:
        s.transform,

      isolation:
        s.isolation,

      width:
        s.width,

      height:
        s.height,

      top:
        s.top,

      right:
        s.right,

      bottom:
        s.bottom,

      left:
        s.left

    };

  }

  function isVisible(el) {

    if (!el) return false;

    const s =
      getComputedStyle(el);

    const r =
      el.getBoundingClientRect();

    return (

      s.display !== "none" &&

      s.visibility !== "hidden" &&

      Number(s.opacity) > 0 &&

      r.width > 0 &&

      r.height > 0

    );

  }

  //////////////////////////////////////////////////
  // ADAPTIVE
  //////////////////////////////////////////////////

  function auditAdaptive() {

    const width =
      window.innerWidth;

    const height =
      window.innerHeight;

    let mode;

    if (width <= 400) {

      mode = "low";

    } else if (width <= 700) {

      mode = "mid";

    } else {

      mode = "high";

    }

    const data = {

      viewport: {

        width,
        height,

        dpr:
          window.devicePixelRatio

      },

      mode,

      page:
        window.CURRENT_PAGE,

      bodyClass:
        document.body.className,

      bodyStyle:
        styleData(document.body),

      functions: {

        applyAdaptive:
          typeof window.applyAdaptive,

        applyLayout:
          typeof window.applyLayout,

        adaptive:
          typeof window.adaptive,

        setAdaptive:
          typeof window.setAdaptive

      },

      media: {

        small:
          matchMedia(
            "(max-width: 400px)"
          ).matches,

        medium:
          matchMedia(
            "(min-width: 401px) and (max-width: 700px)"
          ).matches,

        large:
          matchMedia(
            "(min-width: 701px)"
          ).matches

      }

    };

    console.log(
      "🎨 ADAPTIVE:",
      data
    );

    return data;

  }

  //////////////////////////////////////////////////
  // PAGE ROOT AUDIT
  //////////////////////////////////////////////////

  function auditRoots() {

    const result =
      PAGE_ROOTS
        .map(selector => {

          const el =
            document.querySelector(
              selector
            );

          if (!el) {

            return {

              selector,

              exists: false,

              visible: false

            };

          }

          return {

            selector,

            exists: true,

            visible:
              isVisible(el),

            connected:
              el.isConnected,

            rect:
              rectData(el),

            style:
              styleData(el),

            parent:
              describe(el.parentElement)

          };

        });

    console.group(
      "🌳 PAGE ROOT AUDIT"
    );

    console.table(
      result.map(x => ({

        selector:
          x.selector,

        exists:
          x.exists,

        visible:
          x.visible,

        connected:
          x.connected,

        width:
          x.rect?.width || 0,

        height:
          x.rect?.height || 0,

        position:
          x.style?.position || "-",

        zIndex:
          x.style?.zIndex || "-",

        pointerEvents:
          x.style?.pointerEvents || "-"

      }))
    );

    const visibleRoots =
      result.filter(
        x =>
          x.exists &&
          x.visible
      );

    if (visibleRoots.length > 1) {

      console.error(
        "🚨 MULTIPLE VISIBLE PAGE ROOTS!"
      );

      console.table(
        visibleRoots.map(
          x => x.selector
        )
      );

    }

    console.groupEnd();

    return result;

  }

  //////////////////////////////////////////////////
  // RESIDUE
  //////////////////////////////////////////////////

  function auditResidue() {

    const roots =
      auditRoots();

    const residue =
      roots.filter(
        x =>
          x.exists &&
          x.visible &&
          x.selector !==
            `#${String(
              window.CURRENT_PAGE || ""
            )}Root`
      );

    if (residue.length) {

      console.warn(
        "⚠️ POSSIBLE PAGE RESIDUE:",
        residue.map(
          x => x.selector
        )
      );

    } else {

      console.log(
        "✅ No obvious page residue"
      );

    }

    return residue;

  }

  //////////////////////////////////////////////////
  // BOTTOM NAV HIT TEST
  //////////////////////////////////////////////////

  function findBottomNavBlockers() {

    const nav =
      document.querySelector(
        "#bottomNav, .bottomNav"
      );

    if (!nav) {

      console.error(
        "❌ bottomNav NOT FOUND"
      );

      return [];

    }

    const nr =
      nav.getBoundingClientRect();

    const points = [

      {

        name: "LEFT",

        x:
          nr.left +
          Math.min(
            50,
            nr.width / 4
          ),

        y:
          nr.top +
          nr.height / 2

      },

      {

        name: "CENTER",

        x:
          nr.left +
          nr.width / 2,

        y:
          nr.top +
          nr.height / 2

      },

      {

        name: "RIGHT",

        x:
          nr.right -
          Math.min(
            50,
            nr.width / 4
          ),

        y:
          nr.top +
          nr.height / 2

      }

    ];

    const blockers = [];

    console.group(
      "🎯 BOTTOM NAV HIT-TEST"
    );

    console.log(
      "NAV:",
      describe(nav)
    );

    console.log(
      "RECT:",
      rectData(nav)
    );

    points.forEach(point => {

      const stack =
        document.elementsFromPoint(
          point.x,
          point.y
        );

      const top =
        stack[0];

      console.group(
        `📍 ${point.name} @ ${
          Math.round(point.x)
        },${
          Math.round(point.y)
        }`
      );

      console.table(

        stack.map(
          (el, index) => {

            const r =
              el.getBoundingClientRect();

            const s =
              getComputedStyle(el);

            return {

              index,

              element:
                describe(el),

              position:
                s.position,

              zIndex:
                s.zIndex,

              display:
                s.display,

              visibility:
                s.visibility,

              opacity:
                s.opacity,

              pointerEvents:
                s.pointerEvents,

              width:
                Math.round(r.width),

              height:
                Math.round(r.height)

            };

          }
        )

      );

      if (
        top &&
        top !== nav &&
        !nav.contains(top)
      ) {

        const r =
          top.getBoundingClientRect();

        const s =
          getComputedStyle(top);

        const realBlocker =

          r.width > 0 &&

          r.height > 0 &&

          s.display !== "none" &&

          s.visibility !== "hidden" &&

          Number(s.opacity) > 0 &&

          s.pointerEvents !== "none";

        if (realBlocker) {

          blockers.push({

            point:
              point.name,

            element:
              top,

            selector:
              describe(top),

            rect:
              rectData(top),

            style:
              styleData(top)

          });

          console.error(
            "🚨 REAL NAV BLOCKER:",
            describe(top)
          );

        } else {

          console.log(
            "ℹ️ Ignored top element:",
            describe(top)
          );

        }

      } else {

        console.log(
          "✅ bottomNav is top hit"
        );

      }

      console.groupEnd();

    });

    console.groupEnd();

    return blockers;

  }

  //////////////////////////////////////////////////
  // HIDDEN OVERLAY DETECTOR
  //////////////////////////////////////////////////

  function detectHiddenOverlays() {

    const result = [];

    document
      .querySelectorAll("*")
      .forEach(el => {

        const s =
          getComputedStyle(el);

        if (

          s.position !== "fixed" &&

          s.position !== "absolute"

        ) return;

        const r =
          el.getBoundingClientRect();

        if (
          r.width <= 0 ||
          r.height <= 0
        ) return;

        const coversLargeArea =

          r.width >=
          window.innerWidth * 0.7 &&

          r.height >=
          window.innerHeight * 0.15;

        if (!coversLargeArea) return;

        const hidden =

          s.opacity === "0" ||

          s.visibility === "hidden" ||

          s.display === "none";

        const invisibleInteractive =

          s.opacity === "0" &&

          s.visibility !== "hidden" &&

          s.display !== "none" &&

          s.pointerEvents !== "none";

        if (
          hidden ||
          invisibleInteractive
        ) {

          result.push({

            element: el,

            selector:
              describe(el),

            rect:
              rectData(el),

            style:
              styleData(el),

            type:
              invisibleInteractive
                ? "⚠️ INVISIBLE + CLICKABLE"
                : "HIDDEN OVERLAY"

          });

        }

      });

    if (result.length) {

      console.error(
        "🚨 SUSPICIOUS OVERLAYS"
      );

      console.table(

        result.map(x => ({

          selector:
            x.selector,

          type:
            x.type,

          width:
            x.rect.width,

          height:
            x.rect.height,

          opacity:
            x.style.opacity,

          pointerEvents:
            x.style.pointerEvents,

          visibility:
            x.style.visibility,

          zIndex:
            x.style.zIndex

        }))

      );

    } else {

      console.log(
        "✅ No suspicious overlays"
      );

    }

    return result;

  }

  //////////////////////////////////////////////////
  // FIXED / STICKY / ABSOLUTE
  //////////////////////////////////////////////////

  function auditFixedElements() {

    const result = [];

    document
      .querySelectorAll("*")
      .forEach(el => {

        const s =
          getComputedStyle(el);

        if (

          s.position !== "fixed" &&

          s.position !== "sticky" &&

          s.position !== "absolute"

        ) return;

        result.push({

          element: el,

          selector:
            describe(el),

          position:
            s.position,

          zIndex:
            s.zIndex,

          rect:
            rectData(el),

          style:
            styleData(el)

        });

      });

    console.table(

      result.map(x => ({

        selector:
          x.selector,

        position:
          x.position,

        zIndex:
          x.zIndex,

        top:
          x.rect.top,

        bottom:
          x.rect.bottom,

        left:
          x.rect.left,

        right:
          x.rect.right,

        width:
          x.rect.width,

        height:
          x.rect.height,

        opacity:
          x.style.opacity,

        pointerEvents:
          x.style.pointerEvents

      }))

    );

    return result;

  }

  //////////////////////////////////////////////////
  // Z INDEX
  //////////////////////////////////////////////////

  function auditZIndex() {

    const result = [];

    document
      .querySelectorAll("*")
      .forEach(el => {

        const s =
          getComputedStyle(el);

        const z =
          Number(s.zIndex);

        if (

          s.position !== "static" &&

          !Number.isNaN(z)

        ) {

          result.push({

            element: el,

            selector:
              describe(el),

            position:
              s.position,

            zIndex:
              z,

            opacity:
              s.opacity,

            pointerEvents:
              s.pointerEvents

          });

        }

      });

    result.sort(
      (a, b) =>
        b.zIndex - a.zIndex
    );

    console.table(

      result.map(x => ({

        selector:
          x.selector,

        position:
          x.position,

        zIndex:
          x.zIndex,

        opacity:
          x.opacity,

        pointerEvents:
          x.pointerEvents

      }))

    );

    return result;

  }

  //////////////////////////////////////////////////
  // OVERFLOW
  //////////////////////////////////////////////////

  function auditOverflow() {

    const result = [];

    document
      .querySelectorAll("*")
      .forEach(el => {

        const r =
          el.getBoundingClientRect();

        if (
          r.right >
          window.innerWidth + 2
        ) {

          result.push({

            selector:
              describe(el),

            problem:
              "RIGHT OVERFLOW",

            right:
              Math.round(r.right),

            viewport:
              window.innerWidth

          });

        }

        if (
          r.left < -2
        ) {

          result.push({

            selector:
              describe(el),

            problem:
              "LEFT OVERFLOW",

            left:
              Math.round(r.left)

          });

        }

      });

    if (result.length) {

      console.error(
        "⚠️ OVERFLOW FOUND"
      );

      console.table(result);

    } else {

      console.log(
        "✅ No horizontal overflow"
      );

    }

    return result;

  }

  //////////////////////////////////////////////////
  // DUPLICATE IDS
  //////////////////////////////////////////////////

  function auditDuplicateIDs() {

    const map =
      new Map();

    document
      .querySelectorAll("[id]")
      .forEach(el => {

        if (!map.has(el.id)) {

          map.set(
            el.id,
            []
          );

        }

        map
          .get(el.id)
          .push(el);

      });

    const duplicates = [];

    map.forEach(
      (elements, id) => {

        if (
          elements.length > 1
        ) {

          duplicates.push({

            id,

            count:
              elements.length,

            elements

          });

        }

      }
    );

    if (duplicates.length) {

      console.error(
        "🚨 DUPLICATE IDs"
      );

      console.table(

        duplicates.map(x => ({

          id:
            x.id,

          count:
            x.count

        }))

      );

    } else {

      console.log(
        "✅ No duplicate IDs"
      );

    }

    return duplicates;

  }

  //////////////////////////////////////////////////
  // DOM AUDIT
  //////////////////////////////////////////////////

  function auditDOM() {

    const main =
      document.getElementById(
        MAIN_ID
      );

    if (!main) {

      console.error(
        "❌ #mainContent NOT FOUND"
      );

      return null;

    }

    const data = {

      page:
        window.CURRENT_PAGE,

      children:
        main.children.length,

      nodes:
        main.querySelectorAll("*").length,

      htmlLength:
        main.innerHTML.length,

      rect:
        rectData(main),

      bodyClass:
        document.body.className,

      mainClass:
        main.className

    };

    console.log(
      "📦 DOM:",
      data
    );

    return data;

  }

  //////////////////////////////////////////////////
  // CSS AUDIT
  //////////////////////////////////////////////////

  function auditStylesheets() {

    const sheets =
      [...document.styleSheets];

    console.log(
      "🎨 CSS COUNT:",
      sheets.length
    );

    console.table(

      sheets.map(
        (sheet, index) => ({

          index,

          href:
            sheet.href ||
            "INLINE CSS"

        })
      )

    );

    return sheets;

  }

  //////////////////////////////////////////////////
  // IMPORTANT ELEMENT STATE
  //////////////////////////////////////////////////

  function importantElements() {

    const selectors = [

      "#mainContent",

      "#homeRoot",

      "#reelsContainer",

      "#bottomNav",

      ".bottomNav",

      "#appbar",

      ".appbar",

      "#shareSheet",

      "#commentSheet",

      "#fpsBox"

    ];

    const result = [];

    selectors.forEach(selector => {

      const el =
        document.querySelector(
          selector
        );

      if (!el) return;

      result.push({

        selector,

        element: el,

        connected:
          el.isConnected,

        visible:
          isVisible(el),

        rect:
          rectData(el),

        style:
          styleData(el)

      });

    });

    console.group(
      "🔬 IMPORTANT ELEMENTS"
    );

    console.table(

      result.map(x => ({

        selector:
          x.selector,

        connected:
          x.connected,

        visible:
          x.visible,

        position:
          x.style.position,

        zIndex:
          x.style.zIndex,

        display:
          x.style.display,

        visibility:
          x.style.visibility,

        opacity:
          x.style.opacity,

        pointerEvents:
          x.style.pointerEvents,

        top:
          x.rect.top,

        bottom:
          x.rect.bottom,

        width:
          x.rect.width,

        height:
          x.rect.height

      }))

    );

    console.groupEnd();

    return result;

  }

  //////////////////////////////////////////////////
  // SNAPSHOT
  //////////////////////////////////////////////////

  function snapshot(label) {

    const main =
      document.getElementById(
        MAIN_ID
      );

    const roots =
      PAGE_ROOTS.map(selector => {

        const el =
          document.querySelector(
            selector
          );

        return {

          selector,

          exists:
            !!el,

          visible:
            !!el &&
            isVisible(el),

          rect:
            el
              ? rectData(el)
              : null,

          style:
            el
              ? styleData(el)
              : null

        };

      });

    const data = {

      label,

      timestamp:
        Date.now(),

      transition:
        state.transition,

      page:
        window.CURRENT_PAGE,

      viewport: {

        width:
          window.innerWidth,

        height:
          window.innerHeight,

        dpr:
          window.devicePixelRatio

      },

      dom: main
        ? {

            children:
              main.children.length,

            nodes:
              main.querySelectorAll("*").length,

            htmlLength:
              main.innerHTML.length

          }
        : null,

      bodyClass:
        document.body.className,

      mainClass:
        main?.className || "",

      roots,

      important:
        importantElements()

    };

    state.snapshots.push(data);

    return data;

  }

  //////////////////////////////////////////////////
  // SNAPSHOT DIFF
  //////////////////////////////////////////////////

  function compareSnapshots() {

    if (
      state.snapshots.length < 2
    ) {

      console.warn(
        "⚠️ Need at least 2 snapshots."
      );

      return null;

    }

    const previous =
      state.snapshots[
        state.snapshots.length - 2
      ];

    const current =
      state.snapshots[
        state.snapshots.length - 1
      ];

    console.group(
      "🆚 SNAPSHOT DIFF"
    );

    console.log(
      "FROM:",
      previous.label,
      previous.page
    );

    console.log(
      "TO:",
      current.label,
      current.page
    );

    console.log(
      "DOM:",
      previous.dom,
      "→",
      current.dom
    );

    if (
      previous.bodyClass !==
      current.bodyClass
    ) {

      console.warn(
        "⚠️ BODY CLASS CHANGED:",
        previous.bodyClass,
        "→",
        current.bodyClass
      );

    }

    if (
      previous.mainClass !==
      current.mainClass
    ) {

      console.warn(
        "⚠️ MAIN CLASS CHANGED:",
        previous.mainClass,
        "→",
        current.mainClass
      );

    }

    const changes = [];

    current.roots.forEach(currentRoot => {

      const previousRoot =
        previous.roots.find(
          x =>
            x.selector ===
            currentRoot.selector
        );

      if (!previousRoot) return;

      if (
        previousRoot.exists !==
        currentRoot.exists
      ) {

        changes.push({

          selector:
            currentRoot.selector,

          change:
            "EXISTS",

          from:
            previousRoot.exists,

          to:
            currentRoot.exists

        });

      }

      if (
        previousRoot.visible !==
        currentRoot.visible
      ) {

        changes.push({

          selector:
            currentRoot.selector,

          change:
            "VISIBILITY",

          from:
            previousRoot.visible,

          to:
            currentRoot.visible

        });

      }

      const ps =
        previousRoot.style;

      const cs =
        currentRoot.style;

      if (ps && cs) {

        [

          "position",
          "zIndex",
          "display",
          "visibility",
          "opacity",
          "pointerEvents",
          "transform",
          "overflow"

        ].forEach(prop => {

          if (
            ps[prop] !==
            cs[prop]
          ) {

            changes.push({

              selector:
                currentRoot.selector,

              change:
                prop,

              from:
                ps[prop],

              to:
                cs[prop]

            });

          }

        });

      }

    });

    if (changes.length) {

      console.error(
        "🚨 ROOT STATE CHANGES"
      );

      console.table(changes);

    } else {

      console.log(
        "✅ No major root-state changes."
      );

    }

    console.groupEnd();

    return {

      previous,

      current,

      changes

    };

  }

  //////////////////////////////////////////////////
  // ROOT CAUSE ANALYZER
  //////////////////////////////////////////////////

  function diagnose() {

    console.group(
      "🧠 MINIGRAM ROOT CAUSE DIAGNOSIS"
    );

    const blockers =
      findBottomNavBlockers();

    const overlays =
      detectHiddenOverlays();

    const roots =
      auditRoots();

    const duplicateIDs =
      auditDuplicateIDs();

    const important =
      importantElements();

    let found = false;

    //////////////////////////////////////////////////
    // BLOCKER
    //////////////////////////////////////////////////

    if (blockers.length) {

      found = true;

      console.error(
        "🚨 ROOT CAUSE CANDIDATE #1:",
        "Real element is blocking bottomNav."
      );

      blockers.forEach(
        x =>
          console.error(
            x.selector,
            x.style,
            x.rect
          )
      );

    }

    //////////////////////////////////////////////////
    // INVISIBLE INTERACTIVE
    //////////////////////////////////////////////////

    const interactiveOverlays =
      overlays.filter(
        x =>
          x.type.includes(
            "INVISIBLE + CLICKABLE"
          )
      );

    if (
      interactiveOverlays.length
    ) {

      found = true;

      console.error(
        "🚨 ROOT CAUSE CANDIDATE #2:",
        "Invisible interactive overlay."
      );

      console.table(

        interactiveOverlays.map(
          x => ({

            selector:
              x.selector,

            zIndex:
              x.style.zIndex,

            pointerEvents:
              x.style.pointerEvents,

            opacity:
              x.style.opacity

          })
        )

      );

    }

    //////////////////////////////////////////////////
    // MULTIPLE ROOTS
    //////////////////////////////////////////////////

    const visibleRoots =
      roots.filter(
        x =>
          x.exists &&
          x.visible
      );

    if (
      visibleRoots.length > 1
    ) {

      found = true;

      console.error(
        "🚨 ROOT CAUSE CANDIDATE #3:",
        "Multiple page roots visible."
      );

      console.table(
        visibleRoots.map(
          x => x.selector
        )
      );

    }

    //////////////////////////////////////////////////
    // DUPLICATE IDs
    //////////////////////////////////////////////////

    if (
      duplicateIDs.length
    ) {

      found = true;

      console.error(
        "🚨 ROOT CAUSE CANDIDATE #4:",
        "Duplicate IDs detected."
      );

    }

    //////////////////////////////////////////////////
    // REELS RESIDUE
    //////////////////////////////////////////////////

    const reels =
      document.querySelector(
        "#reelsContainer"
      );

    const currentPage =
      String(
        window.CURRENT_PAGE || ""
      ).toLowerCase();

    if (
      reels &&
      currentPage !== "reels"
    ) {

      const s =
        getComputedStyle(reels);

      const r =
        reels.getBoundingClientRect();

      const activeReels =

        s.display !== "none" &&

        s.visibility !== "hidden" &&

        Number(s.opacity) > 0 &&

        r.width > 0 &&

        r.height > 0;

      if (activeReels) {

        found = true;

        console.error(
          "🚨 ROOT CAUSE CANDIDATE #5:",
          "#reelsContainer remains active outside Reels page."
        );

        console.log({
          style:
            styleData(reels),

          rect:
            rectData(reels)

        });

      }

    }

    //////////////////////////////////////////////////
    // RESULT
    //////////////////////////////////////////////////

    if (!found) {

      console.log(
        "🟢 No obvious root cause detected."
      );

      console.log(
        "Next suspect: page-loader state / CSS layout / event handler."
      );

    }

    console.groupEnd();

    return {

      blockers,

      overlays,

      roots,

      duplicateIDs,

      important,

      found

    };

  }

  //////////////////////////////////////////////////
  // FULL AUDIT
  //////////////////////////////////////////////////

  function fullAudit(page) {

    console.group(
      `🔍 FORENSIC AUDIT: ${page}`
    );

    const report = {

      page,

      time:
        Date.now(),

      transition:
        state.transition,

      adaptive:
        auditAdaptive(),

      dom:
        auditDOM(),

      roots:
        auditRoots(),

      residue:
        auditResidue(),

      overlays:
        detectHiddenOverlays(),

      blockers:
        findBottomNavBlockers(),

      fixed:
        auditFixedElements(),

      zindex:
        auditZIndex(),

      overflow:
        auditOverflow(),

      duplicates:
        auditDuplicateIDs(),

      important:
        importantElements()

    };

    state.lastAudit =
      report;

    console.groupEnd();

    return report;

  }

  //////////////////////////////////////////////////
  // TRANSITION SNAPSHOT
  //////////////////////////////////////////////////

  async function captureTransition(
    transitionId,
    from,
    to
  ) {

    const transition = {

      id:
        transitionId,

      from,

      to,

      start:
        Date.now(),

      before:
        null,

      after:
        null,

      diff:
        null

    };

    //////////////////////////////////////////////////
    // BEFORE
    //////////////////////////////////////////////////

    transition.before =
      snapshot(
        `T${transitionId}: BEFORE ${from} → ${to}`
      );

    //////////////////////////////////////////////////
    // AFTER PAINT
    //////////////////////////////////////////////////

    await new Promise(
      resolve =>
        requestAnimationFrame(resolve)
    );

    await new Promise(
      resolve =>
        requestAnimationFrame(resolve)
    );

    await sleep(30);

    transition.after =
      snapshot(
        `T${transitionId}: AFTER ${from} → ${to}`
      );

    //////////////////////////////////////////////////
    // COMPARE LOCAL SNAPSHOTS
    //////////////////////////////////////////////////

    const before =
      transition.before;

    const after =
      transition.after;

    const changes = [];

    if (
      before.bodyClass !==
      after.bodyClass
    ) {

      changes.push({

        target: "body",

        property: "class",

        from:
          before.bodyClass,

        to:
          after.bodyClass

      });

    }

    if (
      before.mainClass !==
      after.mainClass
    ) {

      changes.push({

        target: "mainContent",

        property: "class",

        from:
          before.mainClass,

        to:
          after.mainClass

      });

    }

    after.roots.forEach(afterRoot => {

      const beforeRoot =
        before.roots.find(
          x =>
            x.selector ===
            afterRoot.selector
        );

      if (!beforeRoot) return;

      if (
        beforeRoot.visible !==
        afterRoot.visible
      ) {

        changes.push({

          target:
            afterRoot.selector,

          property:
            "visible",

          from:
            beforeRoot.visible,

          to:
            afterRoot.visible

        });

      }

      if (
        beforeRoot.style &&
        afterRoot.style
      ) {

        [

          "position",
          "zIndex",
          "display",
          "visibility",
          "opacity",
          "pointerEvents",
          "transform",
          "overflow"

        ].forEach(property => {

          if (
            beforeRoot.style[property] !==
            afterRoot.style[property]
          ) {

            changes.push({

              target:
                afterRoot.selector,

              property,

              from:
                beforeRoot.style[property],

              to:
                afterRoot.style[property]

            });

          }

        });

      }

    });

    transition.diff =
      changes;

    transition.end =
      Date.now();

    transition.duration =
      transition.end -
      transition.start;

    state.lastTransition =
      transition;

    state.history.push(
      transition
    );

    //////////////////////////////////////////////////
    // REPORT
    //////////////////////////////////////////////////

    console.group(
      `🧬 TRANSITION #${transitionId} DIFF`
    );

    console.log(
      "FROM:",
      from
    );

    console.log(
      "TO:",
      to
    );

    console.log(
      "DURATION:",
      transition.duration + "ms"
    );

    if (changes.length) {

      console.error(
        "🚨 STATE CHANGES DETECTED"
      );

      console.table(changes);

    } else {

      console.log(
        "✅ No important state changes detected."
      );

    }

    console.groupEnd();

    return transition;

  }

  //////////////////////////////////////////////////
  // LOAD PAGE WRAPPER
  //////////////////////////////////////////////////

  function connect() {

    if (
      typeof window.loadPage !==
      "function"
    ) {

      if (
        !state.waitingForLoader
      ) {

        state.waitingForLoader = true;

        console.warn(
          "⏳ loadPage not ready. Retrying..."
        );

        let tries = 0;

        const timer =
          setInterval(() => {

            tries++;

            if (
              typeof window.loadPage ===
              "function"
            ) {

              clearInterval(timer);

              state.waitingForLoader =
                false;

              connect();

              return;

            }

            if (tries >= 50) {

              clearInterval(timer);

              state.waitingForLoader =
                false;

              console.error(
                "❌ Could not connect to loadPage."
              );

            }

          }, 200);

      }

      return false;

    }

    if (
      window.__MINIGRAM_DEBUGGER_V4_CONNECTED
    ) {

      console.log(
        "♻️ DEBUGGER V4 ALREADY CONNECTED"
      );

      return true;

    }

    originalLoadPage =
      window.loadPage;

    window.__MINIGRAM_DEBUGGER_V4_CONNECTED =
      true;

    state.connected =
      true;

    //////////////////////////////////////////////////
    // WRAP LOAD PAGE
    //////////////////////////////////////////////////

    window.loadPage =
      async function(
        page,
        force = false
      ) {

        state.transition++;

        const id =
          state.transition;

        const from =
          window.CURRENT_PAGE ||
          "FIRST_LOAD";

        const start =
          performance.now();

        console.group(
          `🚀 TRANSITION #${id}: ${from} → ${page}`
        );

        console.log({

          id,

          from,

          to:
            page,

          force

        });

        //////////////////////////////////////////////////
        // BEFORE
        //////////////////////////////////////////////////

        const beforeSnapshot =
          snapshot(
            `T${id}: BEFORE`
          );

        let result;

        try {

          result =
            await originalLoadPage.call(
              this,
              page,
              force
            );

        } catch (error) {

          console.error(
            "❌ PAGELOADER ERROR:",
            error
          );

          console.groupEnd();

          throw error;

        }

        //////////////////////////////////////////////////
        // AFTER PAINT
        //////////////////////////////////////////////////

        await new Promise(
          resolve =>
            requestAnimationFrame(resolve)
        );

        await new Promise(
          resolve =>
            requestAnimationFrame(resolve)
        );

        await sleep(30);

        const renderTime =
          Math.round(
            performance.now() -
            start
          );

        console.log(
          `⏱️ RENDER TIME: ${renderTime}ms`
        );

        //////////////////////////////////////////////////
        // AFTER SNAPSHOT
        //////////////////////////////////////////////////

        const afterSnapshot =
          snapshot(
            `T${id}: AFTER`
          );

        //////////////////////////////////////////////////
        // DIFF
        //////////////////////////////////////////////////

        const changes = [];

        if (
          beforeSnapshot.bodyClass !==
          afterSnapshot.bodyClass
        ) {

          changes.push({

            target:
              "body",

            property:
              "class",

            from:
              beforeSnapshot.bodyClass,

            to:
              afterSnapshot.bodyClass

          });

        }

        if (
          beforeSnapshot.mainClass !==
          afterSnapshot.mainClass
        ) {

          changes.push({

            target:
              "mainContent",

            property:
              "class",

            from:
              beforeSnapshot.mainClass,

            to:
              afterSnapshot.mainClass

          });

        }

        afterSnapshot.roots.forEach(
          afterRoot => {

            const beforeRoot =
              beforeSnapshot.roots.find(
                x =>
                  x.selector ===
                  afterRoot.selector
              );

            if (!beforeRoot) return;

            if (
              beforeRoot.visible !==
              afterRoot.visible
            ) {

              changes.push({

                target:
                  afterRoot.selector,

                property:
                  "visible",

                from:
                  beforeRoot.visible,

                to:
                  afterRoot.visible

              });

            }

            if (
              beforeRoot.style &&
              afterRoot.style
            ) {

              [

                "position",
                "zIndex",
                "display",
                "visibility",
                "opacity",
                "pointerEvents",
                "transform",
                "overflow",
                "width",
                "height"

              ].forEach(property => {

                if (
                  beforeRoot.style[property] !==
                  afterRoot.style[property]
                ) {

                  changes.push({

                    target:
                      afterRoot.selector,

                    property,

                    from:
                      beforeRoot.style[property],

                    to:
                      afterRoot.style[property]

                  });

                }

              });

            }

          }
        );

        //////////////////////////////////////////////////
        // HISTORY
        //////////////////////////////////////////////////

        const record = {

          id,

          from,

          to:
            page,

          force,

          renderTime,

          timestamp:
            Date.now(),

          changes

        };

        state.history.push(
          record
        );

        state.lastTransition =
          record;

        //////////////////////////////////////////////////
        // TRANSITION REPORT
        //////////////////////////////////////////////////

        console.group(
          `🧬 TRANSITION DIFF #${id}`
        );

        if (changes.length) {

          console.error(
            "🚨 CHANGES DETECTED:"
          );

          console.table(
            changes
          );

        } else {

          console.log(
            "✅ No tracked state changes."
          );

        }

        console.groupEnd();

        //////////////////////////////////////////////////
        // FULL AUDIT
        //////////////////////////////////////////////////

        fullAudit(page);

        //////////////////////////////////////////////////
        // ROOT CAUSE
        //////////////////////////////////////////////////

        diagnose();

        console.groupEnd();

        return result;

      };

    console.log(
      "✅ DEBUGGER V4 CONNECTED"
    );

    return true;

  }

  //////////////////////////////////////////////////
  // PUBLIC API
  //////////////////////////////////////////////////

  window.MinigramDebugger = {

    //////////////////////////////////////////////////
    // FULL FORENSIC
    //////////////////////////////////////////////////

    inspect: function () {

      return fullAudit(
        window.CURRENT_PAGE ||
        "UNKNOWN"
      );

    },

    //////////////////////////////////////////////////
    // ADAPTIVE
    //////////////////////////////////////////////////

    adaptive:
      auditAdaptive,

    //////////////////////////////////////////////////
    // BLOCKERS
    //////////////////////////////////////////////////

    blockers:
      findBottomNavBlockers,

    //////////////////////////////////////////////////
    // OVERLAYS
    //////////////////////////////////////////////////

    overlays:
      detectHiddenOverlays,

    //////////////////////////////////////////////////
    // ROOTS
    //////////////////////////////////////////////////

    roots:
      auditRoots,

    //////////////////////////////////////////////////
    // RESIDUE
    //////////////////////////////////////////////////

    residue:
      auditResidue,

    //////////////////////////////////////////////////
    // FIXED
    //////////////////////////////////////////////////

    fixed:
      auditFixedElements,

    //////////////////////////////////////////////////
    // Z INDEX
    //////////////////////////////////////////////////

    zindex:
      auditZIndex,

    //////////////////////////////////////////////////
    // OVERFLOW
    //////////////////////////////////////////////////

    overflow:
      auditOverflow,

    //////////////////////////////////////////////////
    // DUPLICATES
    //////////////////////////////////////////////////

    duplicates:
      auditDuplicateIDs,

    //////////////////////////////////////////////////
    // DOM
    //////////////////////////////////////////////////

    dom:
      auditDOM,

    //////////////////////////////////////////////////
    // CSS
    //////////////////////////////////////////////////

    css:
      auditStylesheets,

    //////////////////////////////////////////////////
    // IMPORTANT
    //////////////////////////////////////////////////

    important:
      importantElements,

    //////////////////////////////////////////////////
    // SNAPSHOT
    //////////////////////////////////////////////////

    snapshot:
      function(label) {

        return snapshot(
          label ||
          window.CURRENT_PAGE ||
          "MANUAL"
        );

      },

    //////////////////////////////////////////////////
    // COMPARE LAST TWO
    //////////////////////////////////////////////////

    compare:
      compareSnapshots,

    //////////////////////////////////////////////////
    // DIAGNOSE
    //////////////////////////////////////////////////

    diagnose:
      diagnose,

    //////////////////////////////////////////////////
    // HISTORY
    //////////////////////////////////////////////////

    history:
      function() {

        console.table(
          state.history
        );

        return state.history;

      },

    //////////////////////////////////////////////////
    // LAST TRANSITION
    //////////////////////////////////////////////////

    lastTransition:
      function() {

        console.log(
          state.lastTransition
        );

        return state.lastTransition;

      },

    //////////////////////////////////////////////////
    // LAST AUDIT
    //////////////////////////////////////////////////

    lastAudit:
      function() {

        console.log(
          state.lastAudit
        );

        return state.lastAudit;

      },

    //////////////////////////////////////////////////
    // STATE
    //////////////////////////////////////////////////

    state:
      function() {

        console.log(
          state
        );

        return state;

      },

    //////////////////////////////////////////////////
    // RESET
    //////////////////////////////////////////////////

    reset:
      function() {

        state.transition = 0;

        state.history.length = 0;

        state.snapshots.length = 0;

        state.lastAudit = null;

        state.lastTransition = null;

        console.log(
          "♻️ MINIGRAM DEBUGGER STATE RESET"
        );

      }

  };

  //////////////////////////////////////////////////
  // CONNECT
  //////////////////////////////////////////////////

  connect();

})();
```

---

Generated automatically.
