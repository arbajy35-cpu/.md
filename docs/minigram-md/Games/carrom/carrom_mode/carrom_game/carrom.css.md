# Games/carrom/carrom_mode/carrom_game/carrom.css

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/carrom_game/carrom.css` |
| Extension | `.css` |
| Size | 5273 bytes |
| Lines | 286 |
| SHA-256 | `06b5abb156bb5c8bcdaa26a6844787b8458eaba5e93e95d92a40612bd745e148` |

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
Games/carrom/carrom_mode/carrom_game/carrom.css
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/carrom_game/carrom.css`

No AI rewriting was performed on the source code.

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(180deg, #1a1a2e 0%, #0f172a 100%);
  min-height: 100vh;
  min-height: 100dvh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  user-select: none;
  -webkit-user-select: none;
  padding: 10px;
}

.game-wrapper {
  width: 100%;
  max-width: 480px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 18px;
}

/* Top Bar */
.top-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}

.icon-btn {
  width: 52px;
  height: 52px;
  border-radius: 16px;
  background: rgba(255,255,0.12);
  border: 2px solid rgba(255,255,255,0.2);
  color: #fff;
  font-size: 26px;
  cursor: pointer;
  backdrop-filter: blur(10px);
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.icon-btn:active {
  transform: scale(0.92);
  background: rgba(255,255,255,0.25);
}

.score-board {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(0,0,0,0.5);
  border-radius: 18px;
  padding: 14px 18px;
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255,255,255,0.15);
  box-shadow: 0 8px 25px rgba(0,0,0,0.3);
}

.player-score {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  min-width: 60px;
}

.label {
  font-size: 11px;
  color: rgba(255,255,255,0.6);
  letter-spacing: 1.5px;
  font-weight: 700;
}

.score {
  font-size: 32px;
  font-weight: 800;
  color: #fff;
  line-height: 1;
}

.turn-indicator {
  background: linear-gradient(135deg, #ff6b35, #f7931e);
  color: #fff;
  padding: 10px 24px;
  border-radius: 25px;
  font-size: 14px;
  font-weight: 800;
  box-shadow: 0 6px 20px rgba(255, 107, 53, 0.5);
  letter-spacing: 0.5px;
  text-transform: uppercase;
  white-space: nowrap;
}

/* Board Container */
.board-container {
  background: linear-gradient(135deg, #d4a574, #c19660);
  border-radius: 28px;
  padding: 18px;
  box-shadow:
    0 25px 70px rgba(0,0,0,0.6),
    inset 0 3px 15px rgba(255,255,255,0.3);
}

#carromBoard {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 18px;
  touch-action: none;
  box-shadow: inset 0 4px 20px rgba(0,0,0,0.3);
}

/* Bottom Controls */
.controls {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.reset-btn {
  background: linear-gradient(135deg, #ef4444, #dc2626);
  color: #fff;
  border: none;
  padding: 18px 32px;
  border-radius: 18px;
  font-size: 17px;
  font-weight: 800;
  font-family: 'Poppins', sans-serif;
  cursor: pointer;
  transition: all 0.2s;
  box-shadow: 0 6px 20px rgba(239, 68, 68, 0.4);
  text-transform: uppercase;
  letter-spacing: 1px;
  width: 100%;
}

.reset-btn:active {
  transform: scale(0.96);
  box-shadow: 0 4px 12px rgba(239, 68, 0.3);
}

.power-display {
  background: rgba(0,0,0,0.5);
  border-radius: 18px;
  padding: 18px 22px;
  display: flex;
  align-items: center;
  gap: 18px;
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255,255,255,0.15);
  box-shadow: 0 8px 25px rgba(0,0,0,0.3);
}

.power-display span {
  color: #fff;
  font-size: 15px;
  font-weight: 700;
  min-width: 55px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.power-bar {
  flex: 1;
  height: 14px;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  overflow: hidden;
  position: relative;
  border: 1px solid rgba(255,255,255,0.1);
}

.power-fill {
  height: 100%;
  width: 0%;
  background: linear-gradient(90deg, #4ade80, #facc15, #ef4444);
  border-radius: 12px;
  transition: width 0.1s;
  box-shadow: 0 0 15px rgba(250, 204, 21, 0.6);
}

#powerValue {
  min-width: 35px;
  text-align: right;
  font-size: 18px;
  font-weight: 800;
  color: #facc15;
}

/* Mobile Optimization */
@media (max-width: 420px) {
  .game-wrapper {
    padding: 10px;
    gap: 14px;
  }
  
  .icon-btn {
    width: 48px;
    height: 48px;
    font-size: 24px;
  }
  
  .score-board {
    padding: 12px 14px;
  }
  
  .label {
    font-size: 10px;
  }
  
  .score {
    font-size: 28px;
  }
  
  .turn-indicator {
    font-size: 12px;
    padding: 8px 18px;
  }
  
  .board-container {
    padding: 14px;
    border-radius: 24px;
  }
  
  .reset-btn {
    padding: 16px 28px;
    font-size: 16px;
  }
  
  .power-display {
    padding: 16px 18px;
    gap: 14px;
  }
  
  .power-display span {
    font-size: 14px;
  }
  
  #powerValue {
    font-size: 16px;
  }
}

/* Extra small screens */
@media (max-width: 360px) {
  .game-wrapper {
    padding: 8px;
    gap: 12px;
  }
  
  .icon-btn {
    width: 44px;
    height: 44px;
    font-size: 22px;
  }
  
  .score {
    font-size: 26px;
  }
  
  .turn-indicator {
    font-size: 11px;
    padding: 7px 16px;
  }
  
  .reset-btn {
    padding: 14px 24px;
    font-size: 15px;
  }
}
```

---

Generated automatically.
