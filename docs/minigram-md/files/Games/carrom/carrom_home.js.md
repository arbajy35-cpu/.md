# carrom_home.js

## 1. File Identity

- **File Name:** `carrom_home.js`
- **File Path:** `Games/carrom/carrom_home.js`
- **Extension:** `.js`
- **Lines:** 56
- **Bytes:** 1612

## 2. What This File Does

- **[FACT]** This source file contains 56 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 1612 bytes; 56 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/carrom/carrom_home.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `vibrate` — line 38
- `click` — line 8
- `click` — line 18
- `click` — line 22
- `click` — line 26
- `click` — line 33
- `touchstart` — line 45
- `touchend` — line 50

## 42. Exact Line References

- `vibrate` — line 38
- `click` — line 8
- `click` — line 18
- `click` — line 22
- `click` — line 26
- `click` — line 33
- `touchstart` — line 45
- `touchend` — line 50

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

Source file: Games/carrom/carrom_home.js.

---

# SOURCE CODE

> Source: `Games/carrom/carrom_home.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
const startBtn = document.getElementById('startBtn');
const howToBtn = document.getElementById('howToBtn');
const settingsBtn = document.getElementById('settingsBtn');
const howToModal = document.getElementById('howToModal');
const closeBtn = document.querySelector('.close');

// Start Game - Game page pe le jao
startBtn.addEventListener('click', () => {
  // Button press effect
  startBtn.style.transform = 'scale(0.9)';
  setTimeout(() => {
    // Yaha apne game ka HTML file ka naam daal
    window.location.href = '/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html';
  }, 150);
});

// How To Play Modal
howToBtn.addEventListener('click', () => {
  howToModal.style.display = 'block';
});

closeBtn.addEventListener('click', () => {
  howToModal.style.display = 'none';
});

window.addEventListener('click', (e) => {
  if (e.target === howToModal) {
    howToModal.style.display = 'none';
  }
});

// Settings - Abhi simple alert
settingsBtn.addEventListener('click', () => {
  alert('Settings coming soon! 🔧\n\nFeatures:\n• Sound On/Off\n• Difficulty Level\n• Theme Selection');
});

// Haptic feedback for mobile
function vibrate() {
  if (navigator.vibrate) {
    navigator.vibrate(50);
  }
}

[startBtn, howToBtn, settingsBtn].forEach(btn => {
  btn.addEventListener('touchstart', vibrate);
});

// Prevent double-tap zoom on mobile
let lastTouchEnd = 0;
document.addEventListener('touchend', (e) => {
  const now = Date.now();
  if (now - lastTouchEnd <= 300) {
    e.preventDefault();
  }
  lastTouchEnd = now;
}, false);
```
