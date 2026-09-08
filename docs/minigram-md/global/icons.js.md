# global/icons.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `global/icons.js` |
| Extension | `.js` |
| Size | 1392 bytes |
| Lines | 63 |
| SHA-256 | `c473decaf72125dc2efb0cdb4f4008863abebd3d07349ed6b54ed9b2f2f18028` |

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
global/icons.js
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

`/storage/emulated/0/MINIGRAM1/global/icons.js`

No AI rewriting was performed on the source code.

```javascript
alert("ICONS JS RUNNING");

// 🔥 ALWAYS BASE FROM ROOT FILE
const BASE = location.pathname.includes("/pages/")
  ? "../"
  : "./";

const PATHS = {
  like: BASE + "global_css/like.html",
  comment: BASE + "global_css/comment.html",
  share: BASE + "global_css/share.html",
  save: BASE + "global_css/svg.html"
};

const cache = {};

function loadIcon(type){
  if(cache[type]){
    inject(type, cache[type]);
    return;
  }

  fetch(PATHS[type])
    .then(res => {
      if (!res.ok) throw new Error("Fetch failed: " + PATHS[type]);
      return res.text();
    })
    .then(svg => {
      cache[type] = svg;
      inject(type, svg);
    })
    .catch(err => console.error("❌ Icon error:", type, PATHS[type]));
}

function inject(type, svg){
  document.querySelectorAll("." + type).forEach(el=>{
    if(el.dataset.loaded) return;

    el.innerHTML = svg;
    el.dataset.loaded = "true";
  });
}

function initIcons(){
  Object.keys(PATHS).forEach(loadIcon);
}

// 🔥 FIX: debounce observer
let t;
const observer = new MutationObserver(() => {
  clearTimeout(t);
  t = setTimeout(initIcons, 50);
});

observer.observe(document.body, {
  childList: true,
  subtree: true
});

// First run
initIcons();
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated automatically.
