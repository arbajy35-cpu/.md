# Games/carrom/carrom_mode/med.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/med.html` |
| Extension | `.html` |
| Size | 2349 bytes |
| Lines | 74 |
| SHA-256 | `8bd06ca4c4d6489dc290c8e1a1b541803db5cb663757476363750056c354e36b` |

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
Games/carrom/carrom_mode/med.html
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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Carrom King - Select Mode</title>
  <link rel="stylesheet" href="med.css">
</head>
<body>
  <div class="game-mode-container">
    <!-- Header with Profile -->
    <div class="header">
      <button id="backBtn" class="icon-btn"></button>
      <h2>SELECT MODE</h2>
      <div class="profile-card" id="profileBtn">
        <img src="https://i.pravatar.cc/100?img=12" alt="Profile" class="avatar">
        <div class="profile-info">
          <span class="username">Player_01</span>
          <span class="coins"> 2500</span>
        </div>
      </div>
    </div>

    <!-- Game Modes -->
    <div class="modes-grid">
      <div class="mode-card freestyle" data-mode="freestyle">
        <div class="mode-icon"></div>
        <h3>FREESTYLE</h3>
        <p>No rules, just fun! Practice your shots</p>
        <div class="mode-badge">FREE</div>
      </div>

      <div class="mode-card classic" data-mode="classic">
        <div class="mode-icon"></div>
        <h3>CLASSIC</h3>
        <p>Official carrom rules. Beat the AI</p>
        <div class="mode-badge">100</div>
      </div>

      <div class="mode-card twoplayer" data-mode="2player">
        <div class="mode-icon"></div>
        <h3>2 PLAYER</h3>
        <p>Play with friend on same phone</p>
        <div class="mode-badge">FREE</div>
      </div>

      <div class="mode-card tournament" data-mode="tournament">
        <div class="mode-icon"></div>
        <h3>TOURNAMENT</h3>
        <p>Win trophies & climb leaderboard</p>
        <div class="mode-badge">500</div>
      </div>
    </div>

    <!-- Quick Stats -->
    <div class="stats-bar">
      <div class="stat-item">
        <span class="stat-value" id="winsCount">12</span>
        <span class="stat-label">WINS</span>
      </div>
      <div class="stat-item">
        <span class="stat-value" id="coinsCount">2500</span>
        <span class="stat-label">COINS</span>
      </div>
      <div class="stat-item">
        <span class="stat-value" id="rankCount">#247</span>
        <span class="stat-label">RANK</span>
      </div>
    </div>
  </div>

  <script src="med.js"></script>
</body>
</html>
```

---

Generated automatically.
