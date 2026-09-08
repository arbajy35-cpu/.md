# Games/Hill_climb_racing/hill_climb_racing.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/Hill_climb_racing/hill_climb_racing.html` |
| Extension | `.html` |
| Size | 3486 bytes |
| Lines | 144 |
| SHA-256 | `ad6cf24f8e8899aeac20bc31b808301fd7c2df567e80958ab16a4164d93465d7` |

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
Games/Hill_climb_racing/hill_climb_racing.html
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

`/storage/emulated/0/MINIGRAM1/Games/Hill_climb_racing/hill_climb_racing.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#1a1a1a">
<meta name="description" content="Hill Climb Racing Game">
<title>Hill Climb Racing</title>

<link rel="stylesheet" href="hill_climb_racing.css">
</head>
<body>

<div id="game-wrapper">

    <!-- Game Canvas -->
    <canvas id="game-canvas"></canvas>

    <!-- HUD -->
    <div id="hud">

        <div class="hud-item">
            <span class="hud-label">DISTANCE</span>
            <span id="distance" class="hud-value">0 m</span>
        </div>

        <div class="hud-item">
            <span class="hud-label">COINS</span>
            <span id="coins" class="hud-value">0</span>
        </div>

        <div class="hud-item fuel-item">
            <span class="hud-label">FUEL</span>

            <div class="fuel-bar">
                <div id="fuel-fill"></div>
            </div>
        </div>

    </div>

    <!-- Mobile Controls -->
    <div id="controls">

        <button
            id="btn-brake"
            class="ctrl-btn"
            aria-label="Brake"
            type="button">

            <svg viewBox="0 0 24 24" width="38" height="38">
                <path d="M6 6h12v12H6z" fill="#ffffff"/>
            </svg>

        </button>

        <button
            id="btn-gas"
            class="ctrl-btn"
            aria-label="Gas"
            type="button">

            <svg viewBox="0 0 24 24" width="42" height="42">
                <path d="M8 5v14l11-7z" fill="#ffffff"/>
            </svg>

        </button>

    </div>

    <!-- Start Screen -->
    <div id="start-screen" class="overlay">

        <div class="overlay-inner">

            <h1>HILL CLIMB</h1>

            <p class="tag">
                Tap GAS to move forward.<br>
                Tap BRAKE to reverse.<br>
                Collect coins, grab fuel and avoid flipping.
            </p>

            <button
                id="btn-start"
                class="big-btn"
                type="button">
                PLAY
            </button>

            <p class="hint">
                Keyboard: → Gas &nbsp;|&nbsp; ← Brake
            </p>

        </div>

    </div>

    <!-- Game Over Screen -->
    <div id="gameover-screen" class="overlay hidden">

        <div class="overlay-inner">

            <h2 id="go-title">GAME OVER</h2>

            <p id="go-reason" class="tag"></p>

            <div class="stats">

                <div>
                    <span class="hud-label">DISTANCE</span>
                    <span id="go-distance">0 m</span>
                </div>

                <div>
                    <span class="hud-label">COINS</span>
                    <span id="go-coins">0</span>
                </div>

                <div>
                    <span class="hud-label">BEST</span>
                    <span id="go-best">0 m</span>
                </div>

            </div>

            <button
                id="btn-restart"
                class="big-btn"
                type="button">
                RETRY
            </button>

        </div>

    </div>

</div>

<script src="hill_climb_racing.js"></script>

</body>
</html>
```

---

Generated automatically.
