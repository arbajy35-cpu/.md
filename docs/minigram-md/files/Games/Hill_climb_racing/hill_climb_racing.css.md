# hill_climb_racing.css

## 1. File Identity

- **File Name:** `hill_climb_racing.css`
- **File Path:** `Games/Hill_climb_racing/hill_climb_racing.css`
- **Extension:** `.css`
- **Lines:** 368
- **Bytes:** 7874

## 2. What This File Does

- **[FACT]** This source file contains 368 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 7874 bytes; 368 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/Hill_climb_racing/hill_climb_racing.css, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- None detected.

## 42. Exact Line References

- None detected.

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

Source file: Games/Hill_climb_racing/hill_climb_racing.css.

---

# SOURCE CODE

> Source: `Games/Hill_climb_racing/hill_climb_racing.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@700;800;900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  width: 100%; 
  height: 100%;
  height: 100dvh;
  overflow: hidden;
  background: #1a1a2e;
  font-family: 'Nunito', 'Arial Black', sans-serif;
  color: #fff;
  user-select: none;
  touch-action: none;
  -webkit-tap-highlight-color: transparent;
}

#game-wrapper {
  position: fixed;
  inset: 0;
  width: 100vw;
  height: 100vh;
  height: 100dvh;
  overflow: hidden;
}

#game-canvas {
  display: block;
  width: 100%;
  height: 100%;
  background: linear-gradient(180deg, #87CEEB 0%, #98D8E8 50%, #B0E0E6 100%);
}

/* HUD - Hill Climb Style Panels */
#hud {
  position: absolute;
  top: max(12px, env(safe-area-inset-top));
  left: max(12px, env(safe-area-inset-left));
  right: max(12px, env(safe-area-inset-right));
  display: flex;
  gap: 12px;
  pointer-events: none;
  z-index: 5;
}

.hud-item {
  background: #2C3E50;
  border: 3px solid #34495E;
  border-radius: 12px;
  padding: 8px 16px 10px;
  min-width: 100px;
  display: flex;
  flex-direction: column;
  gap: 2px;
  box-shadow: 
    0 4px 0 #1A252F,
    0 6px 12px rgba(0, 0, 0, 0.4),
    inset 0 2px 0 rgba(255, 255, 255, 0.1);
}

.hud-label {
  font-size: 10px;
  letter-spacing: 1px;
  color: #F39C12;
  font-weight: 900;
  text-transform: uppercase;
  text-shadow: 0 2px 0 rgba(0, 0, 0, 0.5);
}

.hud-value {
  font-size: 24px;
  font-weight: 900;
  letter-spacing: 0px;
  color: #ECF0F1;
  text-shadow: 
    0 2px 0 rgba(0, 0, 0, 0.6),
    0 3px 6px rgba(0, 0, 0, 0.4);
  line-height: 1;
}

.fuel-item { 
  flex: 1; 
  min-width: 160px;
}

.fuel-bar {
  height: 16px;
  background: #1A252F;
  border-radius: 8px;
  overflow: hidden;
  margin-top: 4px;
  box-shadow: 
    inset 0 2px 4px rgba(0, 0, 0, 0.6),
    inset 0 -1px 0 rgba(255, 255, 255, 0.1);
  border: 2px solid #1A252F;
  position: relative;
}

#fuel-fill {
  height: 100%;
  width: 100%;
  background: linear-gradient(90deg, 
    #27AE60 0%, 
    #2ECC71 20%, 
    #F1C40F 50%, 
    #E67E22 75%, 
    #E74C3C 100%);
  transition: width 0.15s linear;
  box-shadow: 
    inset 0 2px 0 rgba(255, 255, 255, 0.3),
    0 0 8px rgba(46, 204, 113, 0.6);
  border-radius: 6px;
}

/* Controls - Real 3D Buttons */
#controls {
  position: absolute;
  bottom: max(20px, env(safe-area-inset-bottom));
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  padding: 0 max(20px, env(safe-area-inset-left)) 0 max(20px, env(safe-area-inset-right));
  z-index: 5;
  pointer-events: none;
}

.ctrl-btn {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: linear-gradient(145deg, #E74C3C, #C0392B);
  border: 4px solid #2C3E50;
  box-shadow: 
    0 6px 0 #922B21,
    0 10px 20px rgba(0, 0, 0, 0.5),
    inset 0 -4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 0 rgba(255, 255, 255, 0.2);
  display: flex; 
  align-items: center; 
  justify-content: center;
  cursor: pointer;
  pointer-events: auto;
  transition: all 0.05s ease;
  position: relative;
}

.ctrl-btn::after {
  content: '';
  position: absolute;
  width: 20px;
  height: 20px;
  background: #ECF0F1;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
}

#btn-brake::after {
  border-radius: 2px;
}

#btn-gas {
  background: linear-gradient(145deg, #2ECC71, #27AE60);
  box-shadow: 
    0 6px 0 #1E8449,
    0 10px 20px rgba(0, 0, 0, 0.5),
    inset 0 -4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 0 rgba(255, 255, 255, 0.2);
}

#btn-gas::after {
  width: 0;
  height: 0;
  background: transparent;
  border-left: 16px solid #ECF0F1;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
  margin-left: 4px;
}

.ctrl-btn:active, .ctrl-btn.pressed {
  transform: translateY(4px);
  box-shadow: 
    0 2px 0 #922B21,
    0 4px 8px rgba(0, 0, 0, 0.5),
    inset 0 -2px 4px rgba(0, 0, 0, 0.3);
}

#btn-gas:active, #btn-gas.pressed {
  box-shadow: 
    0 2px 0 #1E8449,
    0 4px 8px rgba(0, 0, 0, 0.5),
    inset 0 -2px 4px rgba(0, 0, 0, 0.3);
}

/* Overlays */
.overlay {
  position: absolute;
  inset: 0;
  background: rgba(26, 26, 46, 0.92);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  animation: fadeIn 0.3s ease;
}

.overlay.hidden { display: none; }

.overlay-inner {
  text-align: center;
  padding: 40px 36px;
  border-radius: 20px;
  background: #2C3E50;
  border: 4px solid #34495E;
  box-shadow: 
    0 8px 0 #1A252F,
    0 16px 40px rgba(0, 0, 0, 0.6),
    inset 0 2px 0 rgba(255, 255, 255, 0.1);
  max-width: 360px;
  width: 90%;
}

h1 {
  font-size: 42px;
  letter-spacing: 3px;
  color: #F39C12;
  text-shadow: 
    0 3px 0 #D68910, 
    0 4px 0 #B9770E,
    0 8px 16px rgba(0, 0, 0, 0.6);
  margin-bottom: 16px;
  font-weight: 900;
}

h2 {
  font-size: 32px;
  letter-spacing: 2px;
  color: #E74C3C;
  margin-bottom: 14px;
  font-weight: 900;
  text-shadow: 
    0 3px 0 #C0392B,
    0 6px 12px rgba(0, 0, 0, 0.5);
}

.tag {
  font-size: 16px;
  line-height: 1.5;
  color: #BDC3C7;
  margin-bottom: 24px;
  font-weight: 700;
}

.hint {
  font-size: 12px;
  color: #7F8C8D;
  margin-top: 18px;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 700;
}

.big-btn {
  background: linear-gradient(180deg, #F39C12 0%, #E67E22 100%);
  color: #1A252F;
  font-weight: 900;
  font-size: 22px;
  letter-spacing: 2px;
  padding: 18px 48px;
  border: 4px solid #D68910;
  border-radius: 14px;
  cursor: pointer;
  box-shadow: 
    0 6px 0 #B9770E,
    0 10px 20px rgba(0, 0, 0, 0.4),
    inset 0 2px 0 rgba(255, 255, 255, 0.3);
  transition: all 0.05s ease;
  text-transform: uppercase;
  font-family: 'Nunito', sans-serif;
}

.big-btn:active {
  transform: translateY(4px);
  box-shadow: 
    0 2px 0 #B9770E,
    0 4px 10px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.3);
}

.stats {
  display: flex;
  justify-content: space-around;
  margin: 24px 0 28px;
  gap: 14px;
}

.stats > div {
  display: flex;
  flex-direction: column;
  gap: 6px;
  font-size: 20px;
  font-weight: 900;
  padding: 14px 18px;
  background: #1A252F;
  border-radius: 12px;
  border: 3px solid #34495E;
  box-shadow: 
    inset 0 2px 4px rgba(0, 0, 0, 0.4),
    0 2px 0 rgba(0, 0, 0, 0.3);
  color: #ECF0F1;
}

.stats > div span:first-child {
  font-size: 11px;
  color: #F39C12;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  text-shadow: 0 2px 0 rgba(0, 0, 0, 0.5);
}

@keyframes fadeIn {
  from { 
    opacity: 0; 
    transform: scale(0.9); 
  }
  to { 
    opacity: 1; 
    transform: scale(1); 
  }
}

/* Responsive */
@media (max-height: 500px) {
  .ctrl-btn { width: 80px; height: 80px; }
  #hud { top: max(8px, env(safe-area-inset-top)); gap: 8px; }
  .hud-item { padding: 6px 12px; min-width: 85px; }
  .hud-value { font-size: 20px; }
  .overlay-inner { padding: 28px 24px; }
  h1 { font-size: 34px; }
}

@media (min-width: 700px) {
  #controls { 
    padding: 0 max(60px, env(safe-area-inset-left)) 0 max(60px, env(safe-area-inset-right)); 
    bottom: max(30px, env(safe-area-inset-bottom)); 
  }
  .ctrl-btn { width: 110px; height: 110px; }
  .hud-item { min-width: 120px; padding: 10px 18px; }
  .hud-value { font-size: 26px; }
}

@media (min-width: 1024px) {
  .ctrl-btn:hover {
    transform: scale(1.05);
  }
  .big-btn:hover {
    transform: translateY(-2px);
    box-shadow: 
      0 8px 0 #B9770E,
      0 12px 24px rgba(0, 0, 0, 0.5),
      inset 0 2px 0 rgba(255, 255, 255, 0.3);
  }
}
```
