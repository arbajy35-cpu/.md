# med.css

## 1. File Identity

- **File Name:** `med.css`
- **File Path:** `Games/carrom/carrom_mode/med.css`
- **Extension:** `.css`
- **Lines:** 252
- **Bytes:** 4660

## 2. What This File Does

- **[FACT]** This source file contains 252 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 4660 bytes; 252 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/carrom/carrom_mode/med.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: Games/carrom/carrom_mode/med.css.

---

# SOURCE CODE

> Source: `Games/carrom/carrom_mode/med.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
  min-height: 100vh;
  color: #fff;
  overflow-x: hidden;
}

.game-mode-container {
  max-width: 450px;
  margin: 0 auto;
  padding: 20px;
  min-height: 100vh;
}

/* Header */
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 30px;
  animation: slideDown 0.6s ease-out;
}

.header h2 {
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 2px;
  color: #facc15;
}

.icon-btn {
  width: 45px;
  height: 45px;
  border-radius: 12px;
  background: rgba(255,255,255,0.1);
  border: none;
  color: #fff;
  font-size: 24px;
  cursor: pointer;
  backdrop-filter: blur(10px);
  transition: all 0.3s;
}

.icon-btn:active {
  transform: scale(0.9);
  background: rgba(255,255,255,0.2);
}

/* Profile Card */
.profile-card {
  display: flex;
  align-items: center;
  gap: 10px;
  background: rgba(255,255,255,0.1);
  padding: 8px 12px;
  border-radius: 15px;
  backdrop-filter: blur(10px);
  cursor: pointer;
  transition: all 0.3s;
}

.profile-card:active {
  transform: scale(0.95);
  background: rgba(255,255,255,0.15);
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #facc15;
}

.profile-info {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.username {
  font-size: 12px;
  font-weight: 600;
  color: #fff;
}

.coins {
  font-size: 11px;
  color: #facc15;
}

/* Mode Cards */
.modes-grid {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 30px;
  animation: slideUp 0.6s ease-out 0.2s both;
}

.mode-card {
  background: linear-gradient(135deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
  border: 2px solid rgba(255,255,255,0.1);
  border-radius: 20px;
  padding: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
}

.mode-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
  transition: left 0.5s;
}

.mode-card:active::before {
  left: 100%;
}

.mode-card:active {
  transform: scale(0.98);
  border-color: #facc15;
}

.freestyle {
  background: linear-gradient(135deg, rgba(34,197,94,0.2), rgba(16,185,129,0.1));
  border-color: rgba(34,197,94,0.3);
}

.classic {
  background: linear-gradient(135deg, rgba(59,130,246,0.2), rgba(37,99,235,0.1));
  border-color: rgba(59,130,246,0.3);
}

.tournament {
  background: linear-gradient(135deg, rgba(245,158,11,0.2), rgba(217,119,6,0.1));
  border-color: rgba(245,158,11,0.3);
}

.mode-icon {
  font-size: 48px;
  margin-bottom: 12px;
}

.mode-card h3 {
  font-size: 22px;
  font-weight: 800;
  margin-bottom: 8px;
  letter-spacing: 1px;
}

.mode-card p {
  font-size: 13px;
  color: rgba(255,255,255,0.7);
  line-height: 1.5;
}

.mode-badge {
  position: absolute;
  top: 20px;
  right: 20px;
  background: #facc15;
  color: #1e293b;
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
}

.tournament .mode-badge {
  background: linear-gradient(135deg, #f59e0b, #d97706);
}

/* Stats Bar */
.stats-bar {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
  animation: fadeIn 0.8s ease-out 0.4s both;
}

.stat-item {
  background: rgba(255,255,255,0.08);
  border-radius: 15px;
  padding: 18px 10px;
  text-align: center;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.1);
}

.stat-value {
  display: block;
  font-size: 24px;
  font-weight: 800;
  color: #facc15;
  margin-bottom: 5px;
}

.stat-label {
  font-size: 11px;
  color: rgba(255,255,255,0.6);
  letter-spacing: 1px;
}

/* Animations */
@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@media (max-width: 380px) {
  .mode-card h3 { font-size: 20px; }
  .mode-icon { font-size: 40px; }
}
```
