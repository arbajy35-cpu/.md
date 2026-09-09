# search_critical.css

## 1. File Identity

- **File Name:** `search_critical.css`
- **File Path:** `critical_css/search_critical.css`
- **Extension:** `.css`
- **Lines:** 432
- **Bytes:** 7028

## 2. What This File Does

- **[FACT]** This source file contains 432 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 7028 bytes; 432 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting critical_css/search_critical.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: critical_css/search_critical.css.

---

# SOURCE CODE

> Source: `critical_css/search_critical.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
/* ============================================================
   🔥 MINIGRAM — SEARCH CRITICAL CSS
   FILE: search_critical.css

   PURPOSE:
   - Instant Search page skeleton
   - Reserve layout space
   - Prevent layout shift
   - No images
   - No heavy effects
   - No external dependencies
   - No actual search UI styling

   NON-CRITICAL:
   search.css handles the real UI after page load.
   ============================================================ */


/* ============================================================
   🌐 SEARCH PAGE BASE
   ============================================================ */

.searchPage{

    width:100%;

    min-height:100vh;

    margin:0;

    padding:
        12px
        12px
        90px;

    box-sizing:border-box;

    background:#0b0b0b;

}


/* ============================================================
   🔍 SEARCH BAR SKELETON
   ============================================================ */

.searchBar{

    width:100%;

    height:48px;

    box-sizing:border-box;

    display:flex;

    align-items:center;

    gap:10px;

    padding:12px;

    border-radius:14px;

    background:#1e1e1e;

}


/* ============================================================
   🔍 SEARCH ICON SKELETON
   ============================================================ */

.searchBar span{

    display:block;

    width:22px;

    height:22px;

    flex:
        0 0 22px;

    border-radius:50%;

    background:#303030;

    font-size:0;

}


/* ============================================================
   📝 SEARCH INPUT PLACEHOLDER
   ============================================================ */

.searchBar input{

    flex:1;

    min-width:0;

    height:18px;

    border:0;

    outline:0;

    background:#303030;

    border-radius:9px;

    color:transparent;

}


/* ============================================================
   👤 SEARCH RESULTS CONTAINER
   ============================================================ */

.searchResults{

    width:100%;

    margin-top:15px;

    display:flex;

    flex-direction:column;

    gap:10px;

}


/* ============================================================
   👤 SEARCH USER SKELETON
   ============================================================ */

.searchUser{

    width:100%;

    min-height:65px;

    box-sizing:border-box;

    display:flex;

    align-items:center;

    gap:12px;

    padding:10px;

    border-radius:12px;

    background:#111;

}


/* ============================================================
   👤 USER AVATAR
   ============================================================ */

.searchUser img{

    width:45px;

    height:45px;

    flex:
        0 0 45px;

    border-radius:50%;

    object-fit:cover;

    background:#222;

}


/* ============================================================
   📝 USER NAME SKELETON
   ============================================================ */

.searchUser span{

    display:block;

    width:100px;

    height:14px;

    border-radius:7px;

    background:#292929;

    font-size:0;

}


/* ============================================================
   🔥 EXPLORE GRID
   ============================================================ */

.exploreGrid{

    width:100%;

    box-sizing:border-box;

    display:grid;

    grid-template-columns:
        repeat(3,1fr);

    gap:3px;

    padding:
        0
        4px;

    margin-top:14px;

}


/* ============================================================
   📦 GRID ITEM
   ============================================================ */

.gridItem{

    position:relative;

    width:100%;

    height:120px;

    min-height:120px;

    overflow:hidden;

    border-radius:12px;

    background:#151515;

}


/* ============================================================
   🔥 BIG GRID ITEM
   ============================================================ */

.gridItem.big{

    grid-column:
        span 2;

    grid-row:
        span 2;

    height:243px;

    min-height:243px;

}


/* ============================================================
   🖼️ GRID IMAGE PLACEHOLDER
   ============================================================ */

.gridItem img{

    position:absolute;

    inset:0;

    width:100%;

    height:100%;

    display:block;

    object-fit:cover;

    background:#151515;

}


/* ============================================================
   ⚡ CRITICAL SKELETON
   ============================================================ */

.searchPage .skeleton{

    background:
        linear-gradient(
            90deg,
            #111 25%,
            #1a1a1a 50%,
            #111 75%
        );

    background-size:
        200% 100%;

    animation:
        searchCriticalShimmer
        1.2s
        infinite;

}


/* ============================================================
   🌊 LIGHTWEIGHT SHIMMER
   ============================================================ */

@keyframes searchCriticalShimmer{

    0%{

        background-position:
            200% 0;

    }

    100%{

        background-position:
            -200% 0;

    }

}


/* ============================================================
   📱 MOBILE SAFETY
   ============================================================ */

@media (max-width:480px){

    .searchPage{

        padding-left:12px;

        padding-right:12px;

    }

    .gridItem{

        height:120px;

        min-height:120px;

    }

    .gridItem.big{

        height:243px;

        min-height:243px;

    }

}


/* ============================================================
   ♿ REDUCED MOTION
   ============================================================ */

@media (prefers-reduced-motion:reduce){

    .searchPage .skeleton{

        animation:none;

    }

}


/* ============================================================
   🛡️ PREVENT FLASH / COLLAPSE
   ============================================================ */

.searchPage{

    contain:
        layout;

}

.exploreGrid{

    contain:
        layout;

}


/* ============================================================
   🚫 NON-CRITICAL UI IS NOT INCLUDED HERE
   ============================================================

   search.css handles:

   - sticky search effects
   - gradients
   - shadows
   - hover
   - active transforms
   - postViewer
   - postContainer
   - glass buttons
   - animations
   - backdrop-filter
   - real colors/details

   ============================================================ */
```
