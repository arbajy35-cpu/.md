# flappy.js

## 1. File Identity

- **File Name:** `flappy.js`
- **File Path:** `Games/flappy/flappy.js`
- **Extension:** `.js`
- **Lines:** 171
- **Bytes:** 3311

## 2. What This File Does

- **[FACT]** This source file contains 171 lines and is part of the MiniGram source tree.

## 3. 5th-Standard Explanation

- **[INFERRED]** The file can be understood by examining its executable code, references, functions, events and relationships with other source files.

## 4. When It Runs

- **[UNKNOWN]** Not determinable from static source analysis.

## 5. Called By

- None detected.

## 6. Calls / Uses

- None detected.

## 7. Imports

- None detected.

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

- **[INFERRED]** Static size: 3311 bytes; 171 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/flappy/flappy.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `resetGame` — line 20
- `startGame` — line 34
- `flap` — line 46
- `updateBird` — line 63
- `spawnPipe` — line 76
- `movePipes` — line 116
- `loop` — line 156
- `gameOver` — line 165
- `keydown` — line 51
- `touchstart` — line 56
- `click` — line 61

## 42. Exact Line References

- `resetGame` — line 20
- `startGame` — line 34
- `flap` — line 46
- `updateBird` — line 63
- `spawnPipe` — line 76
- `movePipes` — line 116
- `loop` — line 156
- `gameOver` — line 165
- `keydown` — line 51
- `touchstart` — line 56
- `click` — line 61

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

Source file: Games/flappy/flappy.js.

---

# SOURCE CODE

> Source: `Games/flappy/flappy.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
const bird = document.getElementById("bird");
const gameArea = document.getElementById("gameArea");
const scoreEl = document.getElementById("score");
const startBtn = document.getElementById("startBtn");

let birdY = 200;
let velocity = 0;

const gravity = 0.45;
const jumpPower = -7.5;

let gameRunning = false;
let gameStarted = false;

let score = 0;
let pipes = [];

let loopId = null;

function resetGame() {
  birdY = 200;
  velocity = 0;
  score = 0;
  pipes = [];

  scoreEl.innerText = score;

  document.querySelectorAll(".pipe").forEach(p => p.remove());

  bird.style.top = birdY + "px";
  bird.style.transform = "rotate(0deg)";
}

function startGame() {
  if (gameRunning) return;

  resetGame();

  gameRunning = true;
  gameStarted = true;

  spawnPipe();
  loop();
}

function flap() {
  if (!gameRunning) return;
  velocity = jumpPower;
}

document.addEventListener("keydown", (e) => {
  if (!gameStarted) startGame();
  flap();
});

document.addEventListener("touchstart", () => {
  if (!gameStarted) startGame();
  flap();
});

startBtn.addEventListener("click", startGame);

function updateBird() {
  velocity += gravity;
  birdY += velocity;

  bird.style.top = birdY + "px";

  bird.style.transform = `rotate(${velocity * 3}deg)`;

  if (birdY > 490 || birdY < 0) {
    gameOver();
  }
}

function spawnPipe() {
  if (!gameRunning) return;

  const gap = 135;
  const minTop = 60;
  const maxTop = 260;

  const topHeight = Math.random() * (maxTop - minTop) + minTop;

  const topPipe = document.createElement("div");
  const bottomPipe = document.createElement("div");

  topPipe.classList.add("pipe");
  bottomPipe.classList.add("pipe");

  topPipe.style.height = topHeight + "px";
  bottomPipe.style.height = (520 - topHeight - gap) + "px";

  let x = 340;

  topPipe.style.left = x + "px";
  bottomPipe.style.left = x + "px";

  topPipe.style.top = "0px";
  bottomPipe.style.bottom = "0px";

  gameArea.appendChild(topPipe);
  gameArea.appendChild(bottomPipe);

  pipes.push({
    x,
    topPipe,
    bottomPipe,
    topHeight,
    passed: false
  });

  setTimeout(spawnPipe, 1300);
}

function movePipes() {
  pipes.forEach(pipe => {
    pipe.x -= 2.7;

    pipe.topPipe.style.left = pipe.x + "px";
    pipe.bottomPipe.style.left = pipe.x + "px";

    // score
    if (!pipe.passed && pipe.x < 60) {
      score++;
      scoreEl.innerText = score;
      pipe.passed = true;
    }

    // collision (smooth)
    const birdTop = birdY;
    const birdBottom = birdY + 32;

    const pipeLeft = pipe.x;
    const pipeRight = pipe.x + 52;

    if (pipeLeft < 90 && pipeRight > 60) {
      if (
        birdTop < pipe.topHeight ||
        birdBottom > pipe.topHeight + 135
      ) {
        gameOver();
      }
    }

    // cleanup
    if (pipe.x < -100) {
      pipe.topPipe.remove();
      pipe.bottomPipe.remove();
    }
  });

  pipes = pipes.filter(p => p.x > -150);
}

function loop() {
  if (!gameRunning) return;

  updateBird();
  movePipes();

  loopId = requestAnimationFrame(loop);
}

function gameOver() {
  gameRunning = false;

  cancelAnimationFrame(loopId);

  alert(" Game Over! Score: " + score);
}
```
