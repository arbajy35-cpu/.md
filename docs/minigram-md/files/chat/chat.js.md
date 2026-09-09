# chat.js

## 1. File Identity

- **File Name:** `chat.js`
- **File Path:** `chat/chat.js`
- **Extension:** `.js`
- **Lines:** 123
- **Bytes:** 3126

## 2. What This File Does

- **[FACT]** This source file contains 123 lines and is part of the MiniGram source tree.

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

- **[FACT]** https://i.pravatar.cc/100?u=${user.name},https://i.pravatar.cc/100?u=${user.name},https://i.pravatar.cc/100?u=${user.name}

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

- **[INFERRED]** Static size: 3126 bytes; 123 lines. Runtime performance requires profiling for reliable measurement.

## 31. Memory Impact

- **[UNKNOWN]** Not determinable from static source analysis.

## 32. Network Impact

- **[INFERRED]** Network endpoints/references were detected.

## 33. Low-End Behavior

- **[UNKNOWN]** Not determinable from static source analysis.

## 34. Security

- **[WARNING]** Static analysis is not a complete security audit. Secrets, dangerous sinks and sensitive configuration should be reviewed separately.

## 35. Common Bugs

- **[TODO]** Potential bugs require combining static findings with tests and runtime reports.

## 36. Debugging

- **[INFERRED]** Start by inspecting chat/chat.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `openChat` — line 6
- `initChat` — line 27
- `click` — line 97
- `error` — line 122

## 42. Exact Line References

- `openChat` — line 6
- `initChat` — line 27
- `click` — line 97
- `error` — line 122
- `https://i.pravatar.cc/100?u=${user.name}` — line 57
- `https://i.pravatar.cc/100?u=${user.name}` — line 81
- `https://i.pravatar.cc/100?u=${user.name}` — line 85

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

Source file: chat/chat.js.

---

# SOURCE CODE

> Source: `chat/chat.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
console.log("💬 chat.js loaded");

// ================================
// 🚀 OPEN CHAT (GLOBAL)
// ================================
function openChat(user){

  if(!user){
    console.warn("❌ No user data");
    return;
  }

  // 🔥 store selected user
  window.CHAT_VIEW_DATA = user;

  // 🚀 open chat view page
  window.loadPage("chat_view");

}

window.openChat = openChat;


// ================================
// 🚀 INIT CHAT LIST
// ================================
function initChat(){

  const chatList = document.getElementById("chatList");
  const loader = document.getElementById("loader");
  const stories = document.getElementById("stories");

  if (!chatList || !stories || !loader) return;

  chatList.innerHTML = "";
  stories.innerHTML = "";

  const users = [
    { id: "1", name: "Aman", msg: "Hii ", time: "1m" },
    { id: "2", name: "Riya", msg: "Kal milte hai", time: "5m" },
    { id: "3", name: "Karan", msg: "Game khelega?", time: "10m" },
    { id: "4", name: "Neha", msg: "Photo bhej", time: "20m" },
    { id: "5", name: "Rahul", msg: "Ok done 👍", time: "30m" },
    { id: "6", name: "Simran", msg: "Nice reel 🔥", time: "1h" }
  ];

  // ================================
  // 🔥 STORIES (FIXED)
  // ================================
  users.forEach(user => {

    const div = document.createElement("div");
    div.className = "storyItem"; // ✅ FIXED

    div.innerHTML = `
      <div class="storyRing">
        <img src="https://i.pravatar.cc/100?u=${user.name}">
      </div>
      <div class="storyUser">${user.name}</div>
    `;

    stories.appendChild(div);

  });

  // ================================
  // 🚀 CHATS (WITH DELAY LOADER)
  // ================================
  setTimeout(() => {

    loader.style.display = "none";

    users.forEach(user => {

      const chat = document.createElement("div");
      chat.className = "chatItem";

      // 🔥 attach data
      chat.dataset.id = user.id;
      chat.dataset.name = user.name;
      chat.dataset.avatar = `https://i.pravatar.cc/100?u=${user.name}`;

      chat.innerHTML = `
        <div class="avatar">
          <img src="https://i.pravatar.cc/100?u=${user.name}">
        </div>
        <div class="chatInfo">
          <div class="chatTop">
            <h3>${user.name}</h3>
            <span class="time">${user.time}</span>
          </div>
          <p>${user.msg}</p>
        </div>
      `;

      // 🔥 CLICK → OPEN CHAT VIEW
      chat.addEventListener("click", () => {

        const selectedUser = {
          id: chat.dataset.id,
          name: chat.dataset.name,
          avatar: chat.dataset.avatar
        };

        openChat(selectedUser);

      });

      chatList.appendChild(chat);

    });

  }, 800);

}


// ================================
// GLOBAL EXPORT
// ================================
window.initChat = initChat;
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```
