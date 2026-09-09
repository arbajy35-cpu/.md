# chat-v.js

## 1. File Identity

- **File Name:** `chat-v.js`
- **File Path:** `chat/chat_view/chat-v.js`
- **Extension:** `.js`
- **Lines:** 312
- **Bytes:** 8198

## 2. What This File Does

- **[FACT]** This source file contains 312 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 8198 bytes; 312 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting chat/chat_view/chat-v.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `singleTick` — line 33
- `doubleTick` — line 39
- `getTime` — line 190
- `clearPress` — line 274
- `click` — line 208
- `click` — line 214
- `touchstart` — line 224
- `touchend` — line 280
- `touchmove` — line 281
- `click` — line 284
- `click` — line 290
- `click` — line 297
- `error` — line 311

## 42. Exact Line References

- `singleTick` — line 33
- `doubleTick` — line 39
- `getTime` — line 190
- `clearPress` — line 274
- `click` — line 208
- `click` — line 214
- `touchstart` — line 224
- `touchend` — line 280
- `touchmove` — line 281
- `click` — line 284
- `click` — line 290
- `click` — line 297
- `error` — line 311

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

Source file: chat/chat_view/chat-v.js.

---

# SOURCE CODE

> Source: `chat/chat_view/chat-v.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
console.log("💬 chat-v.js loaded");

window.FUNCTIONS = window.FUNCTIONS || {};

// ================================
// INIT
// ================================
window.FUNCTIONS.initChatView = function(){

  const data = window.CHAT_VIEW_DATA || {};

  document.querySelector(".chatUserName").innerText = data.name || "User";
  document.querySelector(".chatUserAvatar").src = data.avatar || "";
  document.querySelector(".userStatus").innerText = data.status || "online";

  const box = document.getElementById("chatMessages");
  box.innerHTML = "";

  const msgs = [
    { text: "Hello 👋", type: "other" },
    { text: "Kaise ho?", type: "other" },
    { text: "Main thik hu 😎", type: "me" }
  ];

  msgs.forEach(m => FUNCTIONS.addMessage(m.text, m.type));

  FUNCTIONS.scrollToBottom();
};

// ================================
// SVG TICKS
// ================================
function singleTick(){
  return `<svg viewBox="0 0 16 16">
    <path d="M2 8L6 12L14 3" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
  </svg>`;
}

function doubleTick(){
  return `
    <svg viewBox="0 0 16 16">
      <path d="M2 8L6 12L14 3" fill="none" stroke="currentColor" stroke-width="2"/>
    </svg>
    <svg viewBox="0 0 16 16">
      <path d="M2 8L6 12L14 3" fill="none" stroke="currentColor" stroke-width="2"/>
    </svg>
  `;
}

// ================================
// ADD MESSAGE
// ================================
window.FUNCTIONS.addMessage = function(text, type){

  const box = document.getElementById("chatMessages");

  const msg = document.createElement("div");
  msg.className = "msg " + type;

  const textNode = document.createElement("div");
  textNode.className = "msgText";
  textNode.innerText = text;

  const meta = document.createElement("div");
  meta.className = "msgMeta";

  if(type === "me"){
    meta.innerHTML = `
      <span class="time">${getTime()}</span>
      <span class="ticks single">${singleTick()}</span>
    `;
  }else{
    meta.innerHTML = `<span class="time">${getTime()}</span>`;
  }

  msg.appendChild(textNode);
  msg.appendChild(meta);
  box.appendChild(msg);

  if(type === "me"){
    setTimeout(()=>{
      meta.innerHTML = `
        <span class="time">${getTime()}</span>
        <span class="ticks double">${doubleTick()}</span>
      `;
    }, 800);

    setTimeout(()=>{
      meta.innerHTML = `
        <span class="time">${getTime()}</span>
        <span class="ticks seen">${doubleTick()}</span>
      `;
    }, 1600);
  }

  FUNCTIONS.scrollToBottom();
};

// ================================
// SEND
// ================================
window.FUNCTIONS.sendMessage = function(){

  const input = document.querySelector(".chatInput");
  const text = input.value.trim();

  if(!text) return;

  FUNCTIONS.addMessage(text, "me");

  input.value = "";
  input.style.height = "auto";

  document.querySelector(".sendBtn").classList.remove("active");

  FUNCTIONS.fakeTyping();
};

// ================================
// RECEIVE
// ================================
window.FUNCTIONS.receiveMessage = function(text){
  FUNCTIONS.addMessage(text, "other");
};

// ================================
// TYPING
// ================================
window.FUNCTIONS.fakeTyping = function(){

  const box = document.getElementById("chatMessages");

  const typing = document.createElement("div");
  typing.className = "msg other typing";
  typing.innerHTML = `<span></span><span></span><span></span>`;

  box.appendChild(typing);
  FUNCTIONS.scrollToBottom();

  setTimeout(()=>{
    typing.remove();

    const replies = ["𝕄𝕀ℕ𝕀𝔾ℝ𝔸𝕄"];
    const random = replies[Math.floor(Math.random()*replies.length)];

    FUNCTIONS.receiveMessage(random);

  }, 1200);
};

// ================================
// SCROLL
// ================================
window.FUNCTIONS.scrollToBottom = function(){
  const box = document.getElementById("chatMessages");
  requestAnimationFrame(()=> box.scrollTop = box.scrollHeight);
};

// ================================
// AUTO GROW
// ================================
window.FUNCTIONS.autoGrow = function(el){
  el.style.height = "auto";
  el.style.height = el.scrollHeight + "px";
};

// ================================
// INPUT
// ================================
window.FUNCTIONS.handleInput = function(input){
  FUNCTIONS.autoGrow(input);

  document.querySelector(".sendBtn")
    ?.classList.toggle("active", !!input.value.trim());
};

// ================================
// ENTER
// ================================
window.handleEnter = function(e){
  if(e.key === "Enter" && !e.shiftKey){
    e.preventDefault();
    FUNCTIONS.sendMessage();
  }
};

// ================================
// TIME
// ================================
function getTime(){
  const d = new Date();
  return d.getHours() + ":" +
         String(d.getMinutes()).padStart(2,"0");
}

// ================================
// BACK
// ================================
window.FUNCTIONS.goBackChat = function(){
  if(window.loadPage){
    window.loadPage("chat");
  }else{
    window.history.back();
  }
};

document.querySelector(".backBtn")
  ?.addEventListener("click", FUNCTIONS.goBackChat);


// =====================================================
// 🔥 CALL BUTTON NAVIGATION (FINAL FIXED PATH)
// =====================================================
document.getElementById("callBtn")?.addEventListener("click", () => {
  window.location.href = "./call/call.html";
});

// =====================================================
// 🔥 LONG PRESS MENU
// =====================================================
let currentText = "";
let pressTimer = null;

document.addEventListener("touchstart", function(e){

  const msg = e.target.closest(".msg");
  if(!msg) return;

  pressTimer = setTimeout(()=>{

    const textEl = msg.querySelector(".msgText");
    currentText = textEl ? textEl.innerText : "";

    const menu = document.getElementById("msgMenu");

    const bubble = msg.querySelector(".msgText");
    const rect = bubble.getBoundingClientRect();

    const menuWidth = 160;
    const menuHeight = 50;
    const padding = 10;

    let left;

    if(msg.classList.contains("me")){
      left = rect.right - menuWidth - padding;
    }else{
      left = rect.left + padding;
    }

    if(rect.width < 120){
      left = rect.left + (rect.width / 2) - (menuWidth / 2);
    }

    let top = rect.top - menuHeight - 6;

    left = Math.max(10, Math.min(left, window.innerWidth - menuWidth - 10));
    top = Math.max(10, top);

    menu.style.left = left + "px";
    menu.style.top = top + "px";

    menu.classList.add("show");

    msg.classList.add("activeMsg");

    if(navigator.vibrate) navigator.vibrate(10);

  }, 400);

}, {passive:true});

// CLEAR
function clearPress(){
  clearTimeout(pressTimer);
  document.querySelectorAll(".activeMsg")
    .forEach(el => el.classList.remove("activeMsg"));
}

document.addEventListener("touchend", clearPress);
document.addEventListener("touchmove", clearPress);

// HIDE MENU
document.addEventListener("click", ()=>{
  document.getElementById("msgMenu")?.classList.remove("show");
  clearPress();
});

// COPY
document.getElementById("copyBtn")?.addEventListener("click", ()=>{
  navigator.clipboard.writeText(currentText);
  document.getElementById("msgMenu").classList.remove("show");
  clearPress();
});

// SELECT ALL
document.getElementById("selectBtn")?.addEventListener("click", ()=>{

  const selection = window.getSelection();
  const range = document.createRange();

  const box = document.getElementById("chatMessages");

  range.selectNodeContents(box);
  selection.removeAllRanges();
  selection.addRange(range);

  document.getElementById("msgMenu").classList.remove("show");
  clearPress();
});
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```
