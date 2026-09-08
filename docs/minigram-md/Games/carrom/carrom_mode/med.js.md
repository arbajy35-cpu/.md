# Games/carrom/carrom_mode/med.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/med.js` |
| Extension | `.js` |
| Size | 2677 bytes |
| Lines | 77 |
| SHA-256 | `8a2d372909aea0df25a17ce587239efe1c92f72c0d915573c799a74e1aa82e1e` |

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
Games/carrom/carrom_mode/med.js
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.js`

No AI rewriting was performed on the source code.

```javascript
const backBtn = document.getElementById('backBtn');
const profileBtn = document.getElementById('profileBtn');
const modeCards = document.querySelectorAll('.mode-card');

// Back to home
backBtn?.addEventListener('click', () => {
  window.location.href = '../carrom_home.html';
});

// Profile click
profileBtn?.addEventListener('click', () => {
  alert('Profile Section\n👤 Player_01\n💰 Coins: 2500\n🏆 Wins: 12\n📊 Rank: #247\n\nComing Soon: Edit Profile, Stats, Achievements');
});

// Mode selection
modeCards.forEach(card => {
  card.addEventListener('click', () => {
    const mode = card.dataset.mode;

    if (navigator.vibrate) navigator.vibrate(50);

    card.style.transform = 'scale(0.95)';

    setTimeout(() => {
      if (mode === 'freestyle') {
        window.location.href = 'carrom_game/carrom.html?mode=freestyle';
      }
      else if (mode === 'classic') {
        let coins = parseInt(document.getElementById('coinsCount')?.textContent || '0');
        if (coins >= 100) {
          coins -= 100;
          localStorage.setItem('carromCoins', coins);
          window.location.href = 'carrom_game/carrom.html?mode=classic';
        } else {
          alert('❌ Not enough coins!\n\nYou need 100 coins to play Classic mode.');
        }
      }
      else if (mode === '2player') {
        // NEW: 2 Player mode - No AI, No coins needed
        window.location.href = 'carrom_game/carrom.html?mode=2player';
      }
      else if (mode === 'tournament') {
        let coins = parseInt(document.getElementById('coinsCount')?.textContent || '0');
        if (coins >= 500) {
          alert('🏆 TOURNAMENT MODE\n\nEntry Fee: ₹500\nPrize Pool: ₹5000\nTop 3 win!\n\nComing Soon!');
        } else {
          alert('❌ Not enough coins!\n\nYou need 500 coins for Tournament.');
        }
      }
      card.style.transform = 'scale(1)';
    }, 150);
  });
});

function loadUserData() {
  const savedCoins = localStorage.getItem('carromCoins') || '2500';
  const savedWins = localStorage.getItem('carromWins') || '12';

  const coinsEl = document.getElementById('coinsCount');
  const winsEl = document.getElementById('winsCount');
  const coinsHeaderEl = document.querySelector('.coins');

  if (coinsEl) coinsEl.textContent = savedCoins;
  if (winsEl) winsEl.textContent = savedWins;
  if (coinsHeaderEl) coinsHeaderEl.textContent = `💰 ${savedCoins}`;
}

loadUserData();

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
