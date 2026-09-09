# void.css

## 1. File Identity

- **File Name:** `void.css`
- **File Path:** `Games/void/void.css`
- **Extension:** `.css`
- **Lines:** 276
- **Bytes:** 4989

## 2. What This File Does

- **[FACT]** This source file contains 276 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 4989 bytes; 276 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/void/void.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: Games/void/void.css.

---

# SOURCE CODE

> Source: `Games/void/void.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
/* ----------------- GLOBAL RESET ----------------- */
*{
margin:0;
padding:0;
box-sizing:border-box;
}

html{
image-rendering:pixelated;
animation:
voltageDrift 14s infinite ease-in-out,
analogTilt 32s infinite ease-in-out;
}

/* Perspective for convex glass */
body{
perspective:1200px;
}

html,body{
background:#061a0f;
font-family:'Share Tech Mono',monospace;
color:#e8e8e8;
height:100%;
overflow-x:hidden;
text-rendering:geometricPrecision;
-webkit-font-smoothing:subpixel-antialiased;
-moz-osx-font-smoothing:grayscale;
}

/* ----------------- CRT TUBE ----------------- */
body{
box-shadow:inset 0 0 140px rgba(0,0,0,0.45);
animation:
flicker 0.137s infinite,
frameImperfect 1.013s infinite,
tubeDepth 18s infinite ease-in-out,
voltageDip 40s infinite,
cornerShift 22s infinite ease-in-out,
warmupPulse 35s infinite ease-in-out;
}

/* ----------------- EDGE EFFECT ----------------- */
body::before{
content:"";
position:fixed;
inset:0;
pointer-events:none;

background:
radial-gradient(
ellipse at center,
rgba(255,255,255,0.015) 0%,
rgba(0,0,0,0.15) 60%,
rgba(0,0,0,0.55) 100%
),

linear-gradient(
to bottom,
transparent 0%,
rgba(255,255,255,0.015) 50%,
transparent 100%
);

background-size:100% 100%,100% 200%;

opacity:0.9;

animation:
verticalScan 8s linear infinite,
grainMove 0.9s steps(2) infinite;
}

/* ----------------- SCANLINES ----------------- */
body::after{
content:"";
position:fixed;
inset:0;
pointer-events:none;

background:repeating-linear-gradient(
to bottom,
rgba(255,255,255,0.12),
rgba(255,255,255,0.12) 1px,
transparent 1px,
transparent 2px
);

opacity:0.08;

animation:
crtGlitch 0.8s infinite linear,
scanlineFlicker 0.7s infinite;
}

/* ----------------- TERMINAL ----------------- */
.terminal{

padding:3px 5px;
min-height:100vh;

overflow-y:auto;

display:flex;
flex-direction:column;

line-height:1.05;
letter-spacing:0.05px;

font-size:10.2px;

transform-origin:center;

transform:
rotateX(0.3deg)
rotateY(-0.3deg);

filter:contrast(1.05) brightness(0.98);

animation:
masterDrift 9s infinite ease-in-out,
hSyncBreak 26s infinite,
subPixelJitter 6s infinite;
}

/* ----------------- TEXT ----------------- */
.line,.info{

font-weight:900;

word-break:break-word;

transition:text-shadow 0.25s linear;

text-shadow:
0.2px 0 0 rgba(255,0,0,0.08),
-0.2px 0 0 rgba(0,255,255,0.08);

animation:phosphorMicroFlicker 9s infinite;
}

.line:nth-child(odd){
text-shadow:
0 0 1px rgba(0,255,88,0.28),
0 0 2px rgba(0,255,88,0.18);
}

.line:nth-child(even){
text-shadow:
0 0 0.8px rgba(0,255,88,0.22),
0 0 1.6px rgba(0,255,88,0.14);
}

.line.new-letter{
color:#00ff88;
text-shadow:0 0 8px #00ff88,0 0 4px #00ff88;
}

/* ----------------- INPUT ----------------- */
.input-line{
display:flex;
align-items:center;
margin-top:2px;
}

.symbol{
margin-right:4px;
color:#00ff88;
text-shadow:0 0 6px #00ff88;
}

input{

background:transparent;
border:none;
outline:none;

color:#00ff88;

font-family:inherit;
font-size:10.2px;

flex:1;

caret-color:#00ff88;

text-shadow:0 0 6px #00ff88;
}

/* ----------------- KEYFRAMES ----------------- */

@keyframes voltageDrift{
0%{filter:brightness(1.01) contrast(1.04);}
50%{filter:brightness(1.015) contrast(1.06);}
100%{filter:brightness(1.01) contrast(1.04);}
}

@keyframes masterDrift{
0%{transform:translate(0,0) rotateX(0.3deg) rotateY(-0.3deg);}
50%{transform:translate(0.15px,0.1px) rotateX(0.32deg) rotateY(-0.28deg);}
100%{transform:translate(0,0) rotateX(0.3deg) rotateY(-0.3deg);}
}

@keyframes subPixelJitter{
0%{transform:translate(0px,0px);}
25%{transform:translate(0.1px,-0.1px);}
50%{transform:translate(-0.1px,0.1px);}
75%{transform:translate(0.05px,-0.05px);}
100%{transform:translate(0px,0px);}
}

@keyframes crtGlitch{
0%{background-position:0 0;}
50%{background-position:2px 0;}
100%{background-position:0 0;}
}

@keyframes scanlineFlicker{
0%,100%{opacity:0.08;}
50%{opacity:0.12;}
}

@keyframes verticalScan{
0%{background-position:0 -100%;}
100%{background-position:0 100%;}
}

@keyframes grainMove{
0%{background-position:0 0;}
100%{background-position:1px 1px;}
}

/* ----------------- SCROLLBAR ----------------- */

.terminal::-webkit-scrollbar{width:4px;}

.terminal::-webkit-scrollbar-thumb{
background:rgba(0,255,88,0.35);
border-radius:2px;
}

.hidden{
display:none;
}

/* //////////////////////////////////////// */
/* 🌌 NANO VIEWER */
/* //////////////////////////////////////// */

#nanoViewer{

position:fixed;
inset:0;

background:#000;
color:#fff;

z-index:99999;

display:none; /* 🔥 IMPORTANT */

flex-direction:column;

font-family:monospace;

}

/* //////////////////////////////////////// */
/* 🌌 ACTIVE NANO */
/* //////////////////////////////////////// */

#nanoViewer.active{

display:flex;

}
```
