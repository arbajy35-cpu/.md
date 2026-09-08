# chat/chat_view/call/call.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `chat/chat_view/call/call.js` |
| Extension | `.js` |
| Size | 1105 bytes |
| Lines | 40 |
| SHA-256 | `a45e5f701405dba08e124f16f4e0fa7b35db008005b5abc671b4fde9263b43d8` |

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
chat/chat_view/call/call.js
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

`/storage/emulated/0/MINIGRAM1/chat/chat_view/call/call.js`

No AI rewriting was performed on the source code.

```javascript
function initCall() {

  const muteBtn = document.querySelector(".mute");
  const speakerBtn = document.querySelector(".speaker");
  const endCallBtn = document.querySelector(".endCall");
  const screen = document.querySelector(".callScreen");

  let muted = false;
  let speaker = false;

  muteBtn?.addEventListener("click", () => {
    muted = !muted;
    muteBtn.classList.toggle("active", muted);
  });

  speakerBtn?.addEventListener("click", () => {
    speaker = !speaker;
    speakerBtn.classList.toggle("active", speaker);
  });

  endCallBtn?.addEventListener("click", () => {

    if (navigator.vibrate) navigator.vibrate(50);

    if (screen) {
      screen.style.transition = "0.3s ease";
      screen.style.opacity = "0";
      screen.style.transform = "scale(0.95)";
    }

    setTimeout(() => {
      window.location.href = "../chat/chat.html";
    }, 300);

  });
}

document.addEventListener("DOMContentLoaded", initCall);
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated automatically.
