# Games/void/void_js/ui.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/void/void_js/ui.js` |
| Extension | `.js` |
| Size | 506 bytes |
| Lines | 46 |
| SHA-256 | `265ac1070a300c752accc97eb3c30ac8a58458577d44503d1844125c151daa9b` |

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
Games/void/void_js/ui.js
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

`/storage/emulated/0/MINIGRAM1/Games/void/void_js/ui.js`

No AI rewriting was performed on the source code.

```javascript
function addLine(

text,
type="normal"

){

const line =
document.createElement("div");

line.className =
"line";

line.innerText =
text;

terminal.insertBefore(
line,
document.querySelector(
".input-line"
)
);

scrollBottom();

}

function scrollBottom(){

terminal.scrollTop =
terminal.scrollHeight;

}

function updatePrompt(){

const shortPath =
currentPath.replace(
"/storage/emulated/0/MINIGRAM1",
"~"
);

symbol.innerText =
`root@void:${shortPath} $`;

}
```

---

Generated automatically.
