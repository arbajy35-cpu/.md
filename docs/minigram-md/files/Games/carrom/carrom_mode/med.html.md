# med.html

## 1. File Identity

- **File Name:** `med.html`
- **File Path:** `Games/carrom/carrom_mode/med.html`
- **Extension:** `.html`
- **Lines:** 74
- **Bytes:** 2349

## 2. What This File Does

- **[FACT]** This source file contains 74 lines and is part of the MiniGram source tree.

## 3. 5th-Standard Explanation

- **[INFERRED]** The file can be understood by examining its executable code, references, functions, events and relationships with other source files.

## 4. When It Runs

- **[UNKNOWN]** Not determinable from static source analysis.

## 5. Called By

- None detected.

## 6. Calls / Uses

- None detected.

## 7. Imports

- `med.js` — line 72
- `med.css` — line 7

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

- **[INFERRED]** Static size: 2349 bytes; 74 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/carrom/carrom_mode/med.html, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `med.js` — line 72
- `med.css` — line 7

## 42. Exact Line References

- `med.js` — line 72
- `med.css` — line 7

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

Source file: Games/carrom/carrom_mode/med.html.

---

# SOURCE CODE

> Source: `Games/carrom/carrom_mode/med.html`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

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
