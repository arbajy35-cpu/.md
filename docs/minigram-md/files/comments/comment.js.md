# comment.js

## 1. File Identity

- **File Name:** `comment.js`
- **File Path:** `comments/comment.js`
- **Extension:** `.js`
- **Lines:** 156
- **Bytes:** 4478

## 2. What This File Does

- **[FACT]** This source file contains 156 lines and is part of the MiniGram source tree.

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

- **[FACT]** Supabase-related code/reference detected.

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

- **[INFERRED]** Static size: 4478 bytes; 156 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting comments/comment.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `initCommentSheet` — line 55
- `sendComment` — line 90
- `click` — line 83

## 42. Exact Line References

- `initCommentSheet` — line 55
- `sendComment` — line 90
- `click` — line 83

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

Source file: comments/comment.js.

---

# SOURCE CODE

> Source: `comments/comment.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
//////////////////////////////////////////////////
// 🧠 COMMENT MODULE STATE - ISOLATED
//////////////////////////////////////////////////

(function(){
  
  //////////////////////////////////////////////////
  // 🧠 GLOBAL STATE - UNIQUE NAME
  //////////////////////////////////////////////////
  
  if (!window._commentModuleState) {
    window._commentModuleState = { isOpen: false };
  }
  
  const commentState = window._commentModuleState; // ✅ 'state' → 'commentState'
  
  // 👉 important: current post id store
  window.CURRENT_POST_ID = null;
  
  //////////////////////////////////////////////////
  // 🚀 OPEN COMMENTS
  //////////////////////////////////////////////////
  
  window.openComments = function (postId) {
  
    window.CURRENT_POST_ID = postId;
  
    const sheet = document.getElementById("commentSheet");
    if (!sheet || commentState.isOpen) return;
  
    initCommentSheet();
  
    sheet.classList.add("active");
    document.body.style.overflow = "hidden";
    commentState.isOpen = true;
  };
  
  //////////////////////////////////////////////////
  // ❌ CLOSE COMMENTS
  //////////////////////////////////////////////////
  
  window.closeComments = function() { // ✅ window. add kiya
    const sheet = document.getElementById("commentSheet");
    if (!sheet || !commentState.isOpen) return;
  
    sheet.classList.remove("active");
    document.body.style.overflow = "";
    commentState.isOpen = false;
  };
  
  //////////////////////////////////////////////////
  // 🧱 INIT SHEET
  //////////////////////////////////////////////////
  
  function initCommentSheet() {
    const root = document.getElementById("commentSheet");
    if (!root || root.dataset.loaded) return;
  
    root.dataset.loaded = "true";
  
    root.innerHTML = `
      <div class="sheetContent">
  
        <div class="sheetHeader">
          <h3>Comments</h3>
          <button onclick="window.closeComments()" style="background:none;border:none;color:white;font-size:24px;cursor:pointer;">×</button>
        </div>
  
        <div id="commentList">
          <div class="emptyState">No comments yet 😶</div>
        </div>
  
        <div class="inputBox">
          <input id="commentInput" placeholder="Add a comment...">
          <button id="postBtn">Post</button>
        </div>
  
      </div>
    `;
  
    document
      .getElementById("postBtn")
      ?.addEventListener("click", sendComment);
  }
  
  //////////////////////////////////////////////////
  // 💬 SEND COMMENT + SUPABASE UPDATE
  //////////////////////////////////////////////////
  
  async function sendComment() {
  
    const input = document.getElementById("commentInput");
    const list = document.getElementById("commentList");
  
    if (!input || !list) return;
  
    const text = input.value.trim();
    if (!text) return;
  
    const postId = window.CURRENT_POST_ID;
    if (!postId) return;
  
    //////////////////////////////////////////////////
    // 🧾 ADD COMMENT UI
    //////////////////////////////////////////////////
  
    const empty = list.querySelector(".emptyState");
    if (empty) empty.remove();
  
    const div = document.createElement("div");
    div.className = "commentRow";
  
    div.innerHTML = `
      <b>You:</b> <span></span>
    `;
  
    div.querySelector("span").textContent = text;
  
    list.appendChild(div);
    input.value = "";
  
    //////////////////////////////////////////////////
    // 📊 UPDATE COUNTER UI
    //////////////////////////////////////////////////
  
    const commentsEl = document.getElementById("comments-" + postId);
  
    let count = parseInt(commentsEl?.dataset.comments || "0") || 0;
    count++;
  
    if (commentsEl) {
      commentsEl.dataset.comments = count;
      commentsEl.textContent = count + " comments";
    }
  
    //////////////////////////////////////////////////
    // 🧠 SUPABASE UPDATE (POST TABLE)
    //////////////////////////////////////////////////
  
    try {
      if(window.supabaseClient){
        await window.supabaseClient
          .from("minigram_feed")
          .update({
            comments_count: count
          })
          .eq("id", postId);
      }
    } catch (e) {
      console.error("Supabase update error:", e);
    }
  }

})();

console.log("✅ comment.js loaded");
```
