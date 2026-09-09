# flappy.css

## 1. File Identity

- **File Name:** `flappy.css`
- **File Path:** `Games/flappy/flappy.css`
- **Extension:** `.css`
- **Lines:** 51
- **Bytes:** 873

## 2. What This File Does

- **[FACT]** This source file contains 51 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 873 bytes; 51 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/flappy/flappy.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: Games/flappy/flappy.css.

---

# SOURCE CODE

> Source: `Games/flappy/flappy.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
body {
  margin: 0;
  background: linear-gradient(#70c5ce, #d0f5ff);
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: sans-serif;
}

#gameArea {
  position: relative;
  width: 320px;
  height: 520px;
  background: linear-gradient(#70c5ce, #bff2ff);
  overflow: hidden;
  border-radius: 10px;
  border: 2px solid #000;
  margin-top: 20px;
}

#bird {
  position: absolute;
  width: 32px;
  height: 32px;
  background: gold;
  border-radius: 50%;
  left: 60px;
  top: 200px;
  box-shadow: 0 3px 6px rgba(0,0,0,0.3);
}

.pipe {
  position: absolute;
  width: 52px;
  background: #1faa00;
  border: 2px solid #0b5e00;
}

#score {
  position: absolute;
  top: 10px;
  left: 10px;
  font-size: 22px;
  font-weight: bold;
}

#startBtn {
  margin-top: 12px;
  padding: 10px 18px;
  font-size: 16px;
}
```
