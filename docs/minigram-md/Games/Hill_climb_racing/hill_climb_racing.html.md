# Games/Hill_climb_racing/hill_climb_racing.html

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `Games/Hill_climb_racing/hill_climb_racing.html` |
| Extension | `.html` |
| Bytes | 3486 |
| Lines | 144 |
| SHA-256 | `ad6cf24f8e8899aeac20bc31b808301fd7c2df567e80958ab16a4164d93465d7` |
| Dependency Depth | 1 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`Games`

The local intelligence engine detected
2 direct dependencies
and 0 consumers.

## 5. Dependencies

- `Games/Hill_climb_racing/hill_climb_racing.js`
- `Games/Hill_climb_racing/hill_climb_racing.css`

## 6. Used By

- None

## 7. Exact Relation Flow

- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.js` **[html-script]**
- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.css` **[html-link]**
- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.css` **[html-asset]**
- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.js` **[html-asset]**
- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.css` **[string-path]**
- `Games/Hill_climb_racing/hill_climb_racing.html` → `Games/Hill_climb_racing/hill_climb_racing.js` **[string-path]**

## 8. Local Symbols

- None

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- No detected errors

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/Games/Hill_climb_racing/hill_climb_racing.html`

It is NOT AI generated or rewritten.

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

Generated by MiniGram MD Intelligence V6.
