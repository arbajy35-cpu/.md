# Games/carrom/carrom_home.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_home.html` |
| Extension | `.html` |
| Size | 1848 bytes |
| Lines | 64 |
| SHA-256 | `fe6f7998483d3f91266052023616eda4eaf989cf555e3c1108d170fb8224711a` |

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
Games/carrom/carrom_home.html
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_home.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Carrom King - Home</title>
  <link rel="stylesheet" href="carrom_home.css">
</head>
<body>
  <div class="home-container">
    <div class="bg-coins"></div>
    
    <div class="logo">
      <div class="striker-icon"></div>
      <h1>CARROM <span>KING</span></h1>
      <p class="tagline">Master The Board</p>
    </div>

    <div class="menu">
      <button id="startBtn" class="btn-primary">
        <span class="icon">🎯</span>
        START GAME
      </button>
      
      <button id="howToBtn" class="btn-secondary">
        <span class="icon">📖</span>
        HOW TO PLAY
      </button>
      
      <button id="settingsBtn" class="btn-secondary">
        <span class="icon">⚙️</span>
        SETTINGS
      </button>
    </div>

    <div id="howToModal" class="modal">
      <div class="modal-content">
        <span class="close">&times;</span>
        <h2>How To Play</h2>
        <div class="rules">
          <div class="rule-item">
            <strong>1. Position:</strong> Tap blue zone below striker, drag left-right
          </div>
          <div class="rule-item">
            <strong>2. Shoot:</strong> Hold striker, pull back, release to shoot
          </div>
          <div class="rule-item">
            <strong>3. Score:</strong> White coins = +1, Black = AI only, Queen = +3
          </div>
          <div class="rule-item">
            <strong>4. Win:</strong> Pocket all your coins first to win!
          </div>
        </div>
      </div>
    </div>

    <div class="footer">
      <p>Made with ❤️ by Shila | v2.0</p>
    </div>
  </div>

  <script src="carrom_home.js"></script>
</body>
</html>
```

---

Generated automatically.
