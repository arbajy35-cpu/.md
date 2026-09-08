# Games/carrom/carrom_home.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_home.js` |
| Extension | `.js` |
| Size | 1612 bytes |
| Lines | 56 |
| SHA-256 | `cb14479889836cc0faf7a80db3029086c12885269e85c69eaa2242f4e7da3928` |

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
Games/carrom/carrom_home.js
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_home.js`

No AI rewriting was performed on the source code.

```javascript
const startBtn = document.getElementById('startBtn');
const howToBtn = document.getElementById('howToBtn');
const settingsBtn = document.getElementById('settingsBtn');
const howToModal = document.getElementById('howToModal');
const closeBtn = document.querySelector('.close');

// Start Game - Game page pe le jao
startBtn.addEventListener('click', () => {
  // Button press effect
  startBtn.style.transform = 'scale(0.9)';
  setTimeout(() => {
    // Yaha apne game ka HTML file ka naam daal
    window.location.href = '/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html';
  }, 150);
});

// How To Play Modal
howToBtn.addEventListener('click', () => {
  howToModal.style.display = 'block';
});

closeBtn.addEventListener('click', () => {
  howToModal.style.display = 'none';
});

window.addEventListener('click', (e) => {
  if (e.target === howToModal) {
    howToModal.style.display = 'none';
  }
});

// Settings - Abhi simple alert
settingsBtn.addEventListener('click', () => {
  alert('Settings coming soon! 🔧\n\nFeatures:\n• Sound On/Off\n• Difficulty Level\n• Theme Selection');
});

// Haptic feedback for mobile
function vibrate() {
  if (navigator.vibrate) {
    navigator.vibrate(50);
  }
}

[startBtn, howToBtn, settingsBtn].forEach(btn => {
  btn.addEventListener('touchstart', vibrate);
});

// Prevent double-tap zoom on mobile
let lastTouchEnd = 0;
document.addEventListener('touchend', (e) => {
  const now = Date.now();
  if (now - lastTouchEnd <= 300) {
    e.preventDefault();
  }
  lastTouchEnd = now;
}, false);
```

---

Generated automatically.
