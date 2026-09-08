# Games/carrom/carrom_mode/carrom_game/carrom.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/carrom_game/carrom.html` |
| Extension | `.html` |
| Size | 1458 bytes |
| Lines | 48 |
| SHA-256 | `1302b769005a432eed00c78a19415ffc0f6c1007e2736f577b510f7f72d94389` |

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
Games/carrom/carrom_mode/carrom_game/carrom.html
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/carrom_game/carrom.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Carrom King - Game</title>
  <link rel="stylesheet" href="carrom.css">
</head>
<body>
  <div class="game-wrapper">
    <!-- Top Bar -->
    <div class="top-bar">
      <button id="backBtn" class="icon-btn">←</button>
      <div class="score-board">
        <div class="player-score">
          <span class="label">YOU</span>
          <span class="score" id="playerScore">0</span>
        </div>
        <div class="turn-indicator" id="turnIndicator">Your Turn</div>
        <div class="player-score">
          <span class="label">AI</span>
          <span class="score" id="aiScore">0</span>
        </div>
      </div>
      <button id="settingsBtn" class="icon-btn">⚙️</button>
    </div>

    <!-- Game Board -->
    <div class="board-container">
      <canvas id="carromBoard" width="400" height="400"></canvas>
    </div>

    <!-- Bottom Controls -->
    <div class="controls">
      <button id="resetBtn" class="reset-btn">Reset Game</button>
      <div class="power-display">
        <span>Power</span>
        <div class="power-bar">
          <div class="power-fill" id="powerFill"></div>
        </div>
        <span id="powerValue">0</span>
      </div>
    </div>
  </div>

  <script src="carrom.js"></script>
</body>
</html>
```

---

Generated automatically.
