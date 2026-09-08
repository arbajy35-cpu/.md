# Games/void/void_js/audio.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/void/void_js/audio.js` |
| Extension | `.js` |
| Size | 554 bytes |
| Lines | 47 |
| SHA-256 | `0878fbb9f1462750762f271309c1f1eee7fde3f8f8a79b63c6d7ff2d888f274a` |

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
Games/void/void_js/audio.js
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

`/storage/emulated/0/MINIGRAM1/Games/void/void_js/audio.js`

No AI rewriting was performed on the source code.

```javascript
const audioCtx =
new (
window.AudioContext ||
window.webkitAudioContext
)();

function playTone(

freq,
duration=0.03,
type="square",
volume=0.05

){

const osc =
audioCtx.createOscillator();

const gain =
audioCtx.createGain();

osc.type = type;

osc.frequency.value =
freq;

osc.connect(gain);

gain.connect(
audioCtx.destination
);

gain.gain.value =
volume;

gain.gain.exponentialRampToValueAtTime(
0.0001,
audioCtx.currentTime + duration
);

osc.start();

osc.stop(
audioCtx.currentTime + duration
);

}
```

---

Generated automatically.
