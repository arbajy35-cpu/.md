# snake.js

## 1. File Identity

- **File Name:** `snake.js`
- **File Path:** `Games/snake_io/snake.js`
- **Extension:** `.js`
- **Lines:** 156
- **Bytes:** 3335

## 2. What This File Does

- **[FACT]** This source file contains 156 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 3335 bytes; 156 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/snake_io/snake.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `init` — line 13
- `randomFood` — line 26
- `handleStart` — line 37
- `handleEnd` — line 42
- `setDir` — line 79
- `update` — line 96
- `draw` — line 128
- `gameOver` — line 147
- `restartGame` — line 152
- `touchstart` — line 56
- `touchend` — line 61
- `mousedown` — line 67
- `mouseup` — line 71
- `keydown` — line 89

## 42. Exact Line References

- `init` — line 13
- `randomFood` — line 26
- `handleStart` — line 37
- `handleEnd` — line 42
- `setDir` — line 79
- `update` — line 96
- `draw` — line 128
- `gameOver` — line 147
- `restartGame` — line 152
- `touchstart` — line 56
- `touchend` — line 61
- `mousedown` — line 67
- `mouseup` — line 71
- `keydown` — line 89

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

Source file: Games/snake_io/snake.js.

---

# SOURCE CODE

> Source: `Games/snake_io/snake.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

const size = 10;
const grid = canvas.width / size;

let snake, dir, food, score, loop, lock;

// swipe tracking
let startX = 0;
let startY = 0;

function init() {
  snake = [{ x: 20, y: 20 }];
  dir = "RIGHT";
  food = randomFood();
  score = 0;
  lock = false;

  document.getElementById("score").innerText = score;

  clearInterval(loop);
  loop = setInterval(update, 80);
}

function randomFood() {
  return {
    x: Math.floor(Math.random() * grid),
    y: Math.floor(Math.random() * grid)
  };
}

/* =========================
   TOUCH + MOUSE CONTROL
   ========================= */

function handleStart(x, y) {
  startX = x;
  startY = y;
}

function handleEnd(x, y) {
  let dx = x - startX;
  let dy = y - startY;

  if (Math.abs(dx) > Math.abs(dy)) {
    if (dx > 20) setDir("RIGHT");
    else if (dx < -20) setDir("LEFT");
  } else {
    if (dy > 20) setDir("DOWN");
    else if (dy < -20) setDir("UP");
  }
}

// TOUCH
canvas.addEventListener("touchstart", (e) => {
  let t = e.touches[0];
  handleStart(t.clientX, t.clientY);
});

canvas.addEventListener("touchend", (e) => {
  let t = e.changedTouches[0];
  handleEnd(t.clientX, t.clientY);
});

// MOUSE
canvas.addEventListener("mousedown", (e) => {
  handleStart(e.clientX, e.clientY);
});

canvas.addEventListener("mouseup", (e) => {
  handleEnd(e.clientX, e.clientY);
});

/* =========================
   GAME LOGIC
   ========================= */

function setDir(d) {
  if (lock) return;
  lock = true;

  if (d === "UP" && dir !== "DOWN") dir = "UP";
  else if (d === "DOWN" && dir !== "UP") dir = "DOWN";
  else if (d === "LEFT" && dir !== "RIGHT") dir = "LEFT";
  else if (d === "RIGHT" && dir !== "LEFT") dir = "RIGHT";
}

document.addEventListener("keydown", (e) => {
  if (e.key === "ArrowUp") setDir("UP");
  if (e.key === "ArrowDown") setDir("DOWN");
  if (e.key === "ArrowLeft") setDir("LEFT");
  if (e.key === "ArrowRight") setDir("RIGHT");
});

function update() {
  let head = { ...snake[0] };

  if (dir === "UP") head.y--;
  if (dir === "DOWN") head.y++;
  if (dir === "LEFT") head.x--;
  if (dir === "RIGHT") head.x++;

  // wall crash
  if (head.x < 0 || head.y < 0 || head.x >= grid || head.y >= grid) {
    return gameOver();
  }

  // self crash
  for (let s of snake) {
    if (s.x === head.x && s.y === head.y) return gameOver();
  }

  snake.unshift(head);

  if (head.x === food.x && head.y === food.y) {
    score++;
    document.getElementById("score").innerText = score;
    food = randomFood();
  } else {
    snake.pop();
  }

  draw();
  lock = false;
}

function draw() {
  ctx.fillStyle = "#0b1220";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  // food glow
  ctx.fillStyle = "#f43f5e";
  ctx.shadowBlur = 12;
  ctx.shadowColor = "#f43f5e";
  ctx.fillRect(food.x * size, food.y * size, size, size);

  // snake
  ctx.shadowBlur = 0;
  ctx.fillStyle = "#22c55e";

  for (let s of snake) {
    ctx.fillRect(s.x * size, s.y * size, size, size);
  }
}

function gameOver() {
  clearInterval(loop);
  alert("Game Over 💀 Score: " + score);
}

function restartGame() {
  init();
}

init();
```
