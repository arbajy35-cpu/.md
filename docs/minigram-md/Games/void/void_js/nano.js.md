# Games/void/void_js/nano.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/void/void_js/nano.js` |
| Extension | `.js` |
| Size | 697 bytes |
| Lines | 52 |
| SHA-256 | `256cfd85be24bec9a0ea5ebefd3cf791d58be20fa73098c631befa70fcd2ee57` |

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
Games/void/void_js/nano.js
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

`/storage/emulated/0/MINIGRAM1/Games/void/void_js/nano.js`

No AI rewriting was performed on the source code.

```javascript
function openNano(file){

const viewer =
document.getElementById(
"nanoViewer"
);

document.getElementById(
"nanoFileName"
).innerText = file;

document.getElementById(
"nanoContent"
).innerText =
fileContents[file];

//////////////////////////////////////////////////
// 🌌 OPEN
//////////////////////////////////////////////////

viewer.classList.add(
"active"
);

}

//////////////////////////////////////////////////
// 🌌 EXIT
//////////////////////////////////////////////////

document.addEventListener(
"keydown",
e=>{

if(
e.ctrlKey &&
e.key==="x"
){

document
.getElementById(
"nanoViewer"
)
.classList
.remove(
"active"
);

}

}
);
```

---

Generated automatically.
