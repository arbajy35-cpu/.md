# ludo.css

## 1. File Identity

- **File Name:** `ludo.css`
- **File Path:** `Games/Ludo/ludo.css`
- **Extension:** `.css`
- **Lines:** 113
- **Bytes:** 1517

## 2. What This File Does

- **[FACT]** This source file contains 113 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 1517 bytes; 113 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/Ludo/ludo.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: Games/Ludo/ludo.css.

---

# SOURCE CODE

> Source: `Games/Ludo/ludo.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,sans-serif;
}

body{
height:100vh;
background:#0e45b5;
background-image:
linear-gradient(
135deg,
#0e45b5,
#173d92
);
color:white;
overflow:hidden;
}

.topbar{
height:60px;
display:flex;
align-items:center;
justify-content:space-between;
padding:10px;
background:#08328f;
}

.profile{
width:40px;
height:40px;
background:white;
color:black;
border-radius:10px;
display:flex;
align-items:center;
justify-content:center;
}

.currency{
background:#001c66;
padding:8px 15px;
border-radius:10px;
font-weight:bold;
}

.center{
padding-top:40px;
text-align:center;
}

.logo h1{
font-size:42px;
color:gold;
text-shadow:3px 3px 5px black;
}

.dice{
font-size:60px;
margin:15px;
}

.menu-grid{
display:grid;
grid-template-columns:1fr 1fr 1fr;
gap:15px;
padding:20px;
}

.card{
background:#ffcc00;
color:#002c8a;
font-weight:bold;
padding:20px 10px;
border-radius:20px;
font-size:18px;
box-shadow:0 5px 0 #a06a00;
}

.tournament{
margin:25px auto;
width:250px;
background:#001f78;
padding:15px;
border-radius:20px;
font-size:24px;
font-weight:bold;
border:3px solid gold;
}

.bottom{
position:absolute;
bottom:0;
left:0;
width:100%;
height:80px;
background:#003399;
display:flex;
justify-content:space-around;
align-items:center;
}

.nav-item{
display:flex;
flex-direction:column;
align-items:center;
font-size:12px;
}

.nav-item.active{
color:gold;
}
```
