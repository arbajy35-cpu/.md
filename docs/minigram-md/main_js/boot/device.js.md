# main_js/boot/device.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/device.js` |
| Extension | `.js` |
| Size | 354 bytes |
| Lines | 15 |
| SHA-256 | `9516e8ef9783fd580f0f930dd5ce2c8b6736f667b0c16987247460fd57a8e2a9` |

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
main_js/boot/device.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/device.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 📱 MINIGRAM DEVICE DETECTION
//////////////////////////////////////////////////

window.IS_LOW_END =

    (
        navigator.deviceMemory &&
        navigator.deviceMemory <= 4
    ) ||

    (
        navigator.hardwareConcurrency &&
        navigator.hardwareConcurrency <= 4
    );
```

---

Generated automatically.
