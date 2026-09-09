# hill_climb_racing.html

## 1. File Identity

- **File Name:** `hill_climb_racing.html`
- **File Path:** `Games/Hill_climb_racing/hill_climb_racing.html`
- **Extension:** `.html`
- **Lines:** 144
- **Bytes:** 3486

## 2. What This File Does

- **[FACT]** This source file contains 144 lines and is part of the MiniGram source tree.

## 3. 5th-Standard Explanation

- **[INFERRED]** The file can be understood by examining its executable code, references, functions, events and relationships with other source files.

## 4. When It Runs

- **[UNKNOWN]** Not determinable from static source analysis.

## 5. Called By

- None detected.

## 6. Calls / Uses

- None detected.

## 7. Imports

- `hill_climb_racing.js` — line 141
- `hill_climb_racing.css` — line 11

## 8. Exports

- None detected.

## 9. Globals Read

- None detected.

## 10. Globals Written

- None detected.

## 11. Inputs

- **[INFERRED]** Inputs are derived from function parameters, events, referenced globals, DOM APIs and external resources when detectable.

## 12. Outputs

- **[INFERRED]** Outputs are derived from return statements, DOM mutations, exported values and external effects when detectable.

## 13. Exact Execution Flow

- **[INFERRED]** Static execution order is represented by discovered declarations, references and dependency relationships. Runtime branch order may require execution tracing.

## 14. Forward Flow

- None detected.

## 15. Reverse Flow

- None detected.

## 16. Data Flow

- **[INFERRED]** Data flow is reconstructed only from statically detectable references. Runtime values that depend on user input or network responses may remain unknown.

## 17. UI Flow

- **[INFERRED]** UI interaction points are reported when DOM APIs, event listeners or HTML references are detected.

## 18. Network Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 19. Cache Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 20. Supabase Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 21. Error Flow

- **[INFERRED]** Potential error paths are identified from detectable error handling constructs; complete runtime error behavior cannot be proven statically.

## 22. Fallback Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 23. Dependency Graph

### Incoming
- None detected.

### Outgoing
- None detected.

## 24. Before This File

- [object Object]

## 25. After This File

- [object Object]

## 26. Parallel Files

- **[TODO]** Runtime parallelism requires execution tracing or explicit asynchronous scheduling analysis.

## 27. Blocking Files

- **[TODO]** Blocking behavior cannot always be proven from static source analysis.

## 28. Required Files

- None detected.

## 29. Optional Files

- **[TODO]** Optionality requires runtime/build configuration evidence.

## 30. Performance Impact

- **[INFERRED]** Static size: 3486 bytes; 144 lines. Runtime performance requires profiling for reliable measurement.

## 31. Memory Impact

- **[UNKNOWN]** Not determinable from static source analysis.

## 32. Network Impact

- **[UNKNOWN]** Not determinable from static source analysis.

## 33. Low-End Behavior

- **[UNKNOWN]** Not determinable from static source analysis.

## 34. Security

- **[WARNING]** Static analysis is not a complete security audit. Secrets, dangerous sinks and sensitive configuration should be reviewed separately.

## 35. Common Bugs

- **[TODO]** Potential bugs require combining static findings with tests and runtime reports.

## 36. Debugging

- **[INFERRED]** Start by inspecting Games/Hill_climb_racing/hill_climb_racing.html, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `hill_climb_racing.js` — line 141
- `hill_climb_racing.css` — line 11

## 42. Exact Line References

- `hill_climb_racing.js` — line 141
- `hill_climb_racing.css` — line 11

## 43. Tests

- **[TODO]** No test result is claimed unless tests are actually executed.

## 44. Developer Checklist

- Verify source behavior before changing it.
- Check incoming dependencies.
- Check outgoing dependencies.
- Run relevant tests.
- Review generated documentation after changes.

## 45. Simple Example

- **[INFERRED]** Use the detected functions, events and dependency graph as the starting point for understanding this file.

## 46. Confidence / Evidence

- Static facts: **HIGH**
- Runtime behavior: **LIMITED**
- Inferred behavior: **MEDIUM**
- Unknown areas: **EXPLICIT**

The system does not present unknown runtime behavior as proven fact.

## 47. One-Line Summary

Source file: Games/Hill_climb_racing/hill_climb_racing.html.

---

# SOURCE CODE

> Source: `Games/Hill_climb_racing/hill_climb_racing.html`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

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
