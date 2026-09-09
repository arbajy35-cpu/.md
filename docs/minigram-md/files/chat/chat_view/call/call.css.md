# call.css

## 1. File Identity

- **File Name:** `call.css`
- **File Path:** `chat/chat_view/call/call.css`
- **Extension:** `.css`
- **Lines:** 242
- **Bytes:** 4627

## 2. What This File Does

- **[FACT]** This source file contains 242 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 4627 bytes; 242 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting chat/chat_view/call/call.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: chat/chat_view/call/call.css.

---

# SOURCE CODE

> Source: `chat/chat_view/call/call.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
/* ===== RESET ===== */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system,BlinkMacSystemFont,"SF Pro Text",system-ui,sans-serif;
  -webkit-tap-highlight-color: transparent;
}

body{
  background:#000;
  color:#fff;
  height:100vh;
  overflow:hidden;
}

/* ===== SCREEN ===== */
.callScreen{
  height:100dvh;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  padding:18px;
  background:
    radial-gradient(circle at 50% -10%, rgba(255,255,255,0.08), transparent 60%),
    radial-gradient(circle at bottom, rgba(255,255,255,0.05), transparent 70%),
    #000;
  animation:fadeIn 0.5s ease;
}

@keyframes fadeIn{
  from{opacity:0; transform:scale(1.02);}
  to{opacity:1; transform:scale(1);}
}

/* ===== TOP BAR ===== */
.topBar{
  display:flex;
  align-items:center;
  justify-content:space-between;
}

/* glass button */
.iconBtn{
  width:44px;
  height:44px;
  border-radius:50%;
  border:1px solid rgba(255,255,255,0.08);
  background:rgba(255,255,255,0.05);
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  backdrop-filter: blur(14px);
  box-shadow:0 4px 15px rgba(0,0,0,0.4);
  cursor:pointer;
  transition:all 0.2s ease;
}

.iconBtn:hover{
  background:rgba(255,255,255,0.08);
}

.iconBtn:active{
  transform:scale(0.88);
  background:rgba(255,255,255,0.18);
}

/* ===== USER INFO ===== */
.userInfo{
  text-align:center;
}

.userInfo h2{
  font-size:18px;
  font-weight:600;
  letter-spacing:0.3px;
}

.userInfo p{
  font-size:12px;
  color:rgba(255,255,255,0.55);
  margin-top:3px;
}

/* ===== PROFILE ===== */
.profileContainer{
  flex:1;
  display:flex;
  align-items:center;
  justify-content:center;
}

.profileCircle{
  position:relative;
  width:150px;
  height:150px;
  border-radius:50%;
  background:linear-gradient(145deg,#1a1a1a,#0a0a0a);
  display:flex;
  align-items:center;
  justify-content:center;
  box-shadow:
    0 15px 50px rgba(0,0,0,0.9),
    inset 0 0 25px rgba(255,255,255,0.05);
}

/* subtle glow ring */
.profileCircle::after{
  content:"";
  position:absolute;
  inset:-6px;
  border-radius:50%;
  background:linear-gradient(120deg,transparent,#0A84FF,transparent);
  opacity:0.15;
  filter:blur(8px);
}

/* pulse animation (call active feel) */
.profileCircle{
  animation:pulse 2.5s infinite ease-in-out;
}

@keyframes pulse{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.05);}
}

/* ===== CONTROLS ===== */
.controls{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:14px;
  padding-bottom:12px;
}

/* small buttons */
.controlBtn{
  flex:1;
  height:58px;
  border-radius:50%;
  border:1px solid rgba(255,255,255,0.08);
  background:rgba(255,255,255,0.06);
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  backdrop-filter:blur(16px);
  box-shadow:0 6px 20px rgba(0,0,0,0.5);
  transition:all 0.2s ease;
  cursor:pointer;
}

/* hover + press */
.controlBtn:hover{
  background:rgba(255,255,255,0.1);
}

.controlBtn:active{
  transform:scale(0.88);
  background:rgba(255,255,255,0.2);
}

/* active states */
.controlBtn.active{
  background:#0A84FF;
  color:#fff;
  box-shadow:0 6px 20px rgba(10,132,255,0.5);
}

/* mute state */
.controlBtn.mute{
  background:rgba(255,70,70,0.15);
  color:#ff4d4d;
  border-color:rgba(255,70,70,0.3);
}

/* ===== END CALL ===== */
.endCall{
  width:72px;
  height:72px;
  border-radius:50%;
  border:none;
  background:linear-gradient(145deg,#ff3b30,#ff1f1f);
  display:flex;
  align-items:center;
  justify-content:center;
  color:#fff;
  box-shadow:
    0 10px 30px rgba(255,59,48,0.6),
    inset 0 -3px 10px rgba(0,0,0,0.3);
  transition:all 0.2s ease;
  cursor:pointer;
}

.endCall:hover{
  filter:brightness(1.1);
}

.endCall:active{
  transform:scale(0.85);
}

/* ===== RIPPLE CLICK EFFECT ===== */
.controlBtn::after,
.iconBtn::after,
.endCall::after{
  content:"";
  position:absolute;
  width:100%;
  height:100%;
  border-radius:inherit;
  background:rgba(255,255,255,0.2);
  opacity:0;
  transform:scale(0.6);
  transition:0.4s;
}

.controlBtn:active::after,
.iconBtn:active::after,
.endCall:active::after{
  opacity:0.3;
  transform:scale(1.2);
}

/* ===== RESPONSIVE ===== */
@media (max-width:400px){
  .profileCircle{
    width:120px;
    height:120px;
  }

  .controlBtn{
    height:52px;
  }

  .endCall{
    width:62px;
    height:62px;
  }
}
```
