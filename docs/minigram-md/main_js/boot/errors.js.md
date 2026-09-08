# main_js/boot/errors.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/errors.js` |
| Extension | `.js` |
| Size | 687 bytes |
| Lines | 35 |
| SHA-256 | `75eb29b53c9b2ecd8d962924ef305cbc3ce51d1dfe645eaf2d31aadc379bbc97` |

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
main_js/boot/errors.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/errors.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 💀 MINIGRAM GLOBAL ERROR LOGGER
//////////////////////////////////////////////////

window.addEventListener(
    "error",
    e => {

        console.error(
            "💀 ERROR:",
            e.filename,
            e.message,
            "LINE:",
            e.lineno
        );

    }
);


//////////////////////////////////////////////////
// 💀 MINIGRAM PROMISE LOGGER
//////////////////////////////////////////////////

window.addEventListener(
    "unhandledrejection",
    e => {

        console.error(
            "💀 UNHANDLED PROMISE:",
            e.reason
        );

    }
);
```

---

Generated automatically.
