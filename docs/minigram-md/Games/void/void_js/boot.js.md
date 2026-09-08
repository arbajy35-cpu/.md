# Games/void/void_js/boot.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/void/void_js/boot.js` |
| Extension | `.js` |
| Size | 386 bytes |
| Lines | 49 |
| SHA-256 | `52bd6c68520bdae3a911440b60c70d48664ce0d2a14adef53de3e2e0562023d5` |

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
Games/void/void_js/boot.js
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

`/storage/emulated/0/MINIGRAM1/Games/void/void_js/boot.js`

No AI rewriting was performed on the source code.

```javascript
// boot.js

updatePrompt();

input.addEventListener(

"keydown",

e=>{

if(e.key==="Enter"){

e.preventDefault();

const cmd =
input.value.trim();

if(!cmd) return;

playTone(
900,
0.05,
"square",
0.08
);

addLine(

document.querySelector(
".symbol"
).innerText +

" " +

cmd,

"command"

);

runCommand(cmd);

input.value = "";

}

}

);
```

---

Generated automatically.
