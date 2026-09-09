# carrom_home.css

## 1. File Identity

- **File Name:** `carrom_home.css`
- **File Path:** `Games/carrom/carrom_home.css`
- **Extension:** `.css`
- **Lines:** 256
- **Bytes:** 4662

## 2. What This File Does

- **[FACT]** This source file contains 256 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 4662 bytes; 256 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/carrom/carrom_home.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: Games/carrom/carrom_home.css.

---

# SOURCE CODE

> Source: `Games/carrom/carrom_home.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  overflow-x: hidden;
  width: 100%;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
  min-height: 100vh;
  min-height: 100dvh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 0;
}

.bg-coins {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(circle at 20% 30%, rgba(255,255,255,0.05) 0%, transparent 50%),
    radial-gradient(circle at 80% 70%, rgba(255,255,255,0.05) 0%, transparent 50%);
  z-index: 1;
  pointer-events: none;
}

.home-container {
  width: 100%;
  max-width: 400px;
  padding: 20px;
  position: relative;
  z-index: 2;
  margin: 0 auto;
}

.logo {
  text-align: center;
  margin-bottom: 50px;
  animation: slideDown 0.8s ease-out;
}

.striker-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, #ff6b35, #f7931e);
  border-radius: 50%;
  margin: 0 auto 20px;
  box-shadow: 0 10px 30px rgba(255, 107, 53, 0.4);
  position: relative;
  animation: bounce 2s infinite;
}

.striker-icon::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 50px;
  height: 50px;
  background: rgba(255,255,255,0.3);
  border-radius: 50%;
}

.logo h1 {
  font-size: 48px;
  font-weight: 800;
  color: #fff;
  letter-spacing: 2px;
  text-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.logo h1 span {
  color: #facc15;
}

.tagline {
  color: rgba(255,255,255,0.8);
  font-size: 14px;
  letter-spacing: 3px;
  margin-top: 5px;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 15px;
  animation: slideUp 0.8s ease-out 0.2s both;
  width: 100%;
}

button {
  border: none;
  border-radius: 15px;
  padding: 18px 30px;
  font-size: 16px;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
  width: 100%;
}

.btn-primary {
  background: linear-gradient(135deg, #ff6b35, #f7931e);
  color: white;
  font-size: 18px;
  padding: 20px 30px;
}

.btn-primary:active {
  transform: scale(0.95);
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}

.btn-secondary {
  background: rgba(255,255,255,0.15);
  color: white;
  backdrop-filter: blur(10px);
}

.btn-secondary:active {
  background: rgba(255,255,255,0.25);
  transform: scale(0.98);
}

.icon {
  font-size: 22px;
}

.modal {
  display: none;
  position: fixed;
  z-index: 100;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.7);
  backdrop-filter: blur(5px);
  animation: fadeIn 0.3s;
}

.modal-content {
  background: linear-gradient(135deg, #2a5298, #1e3c72);
  margin: 15% auto;
  padding: 30px;
  border-radius: 20px;
  width: 90%;
  max-width: 350px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  animation: slideUp 0.4s;
  position: relative;
}

.modal-content h2 {
  color: #facc15;
  margin-bottom: 20px;
  text-align: center;
}

.close {
  color: #fff;
  position: absolute;
  right: 20px;
  top: 15px;
  font-size: 32px;
  font-weight: bold;
  cursor: pointer;
}

.close:active {
  color: #facc15;
}

.rules {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.rule-item {
  background: rgba(255,255,255,0.1);
  padding: 12px;
  border-radius: 10px;
  color: #fff;
  font-size: 13px;
  line-height: 1.6;
}

.rule-item strong {
  color: #facc15;
}

.footer {
  text-align: center;
  margin-top: 40px;
  color: rgba(255,255,255,0.5);
  font-size: 12px;
  animation: fadeIn 1s ease-out 0.5s both;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-50px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(50px);
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

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@media (max-width: 380px) {
  .logo h1 { font-size: 40px; }
  button { padding: 16px 25px; font-size: 15px; }
  .home-container { padding: 15px; }
}
```
