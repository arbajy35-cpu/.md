# chat.css

## 1. File Identity

- **File Name:** `chat.css`
- **File Path:** `chat/chat.css`
- **Extension:** `.css`
- **Lines:** 323
- **Bytes:** 5582

## 2. What This File Does

- **[FACT]** This source file contains 323 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 5582 bytes; 323 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting chat/chat.css, then inspect its incoming and outgoing dependency relationships.

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

Source file: chat/chat.css.

---

# SOURCE CODE

> Source: `chat/chat.css`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```css
/* ===== ROOT ===== */
:root {
  --bg: #000;
  --border: rgba(255,255,255,0.05);
  --text: #fff;
  --muted: rgba(255,255,255,0.5);
  --accent: #0A84FF;
}

/* ===== PAGE ===== */
.chatPage {
  background: radial-gradient(circle at top, #0a0a0a, #000 65%);
  color: var(--text);
  height: 100vh;
  display: flex;
  flex-direction: column;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* ===== RESET ===== */
.chatPage * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

/* ===== CONTAINER ===== */
.chatPage .container {
  width: 100%;
  max-width: 420px;
  margin: 0 auto;

  display: flex;
  flex-direction: column;
  height: 100%;

  padding: 0 2px; /*  tight edge */
}

/* ===== HEADER ===== */
.chatPage .header {
  position: sticky;
  top: 0;
  z-index: 50;

  display: flex;
  align-items: center;

  padding: 12px 14px;

  background: rgba(0,0,0,0.85);
  backdrop-filter: blur(18px);

  border-bottom: 1px solid var(--border);
}

.chatPage .header h1 {
  font-size: 16px;
  font-weight: 600;
  margin: auto;
}

/* ===== BUTTON ===== */
.chatPage .iconBtn {
  position: absolute;
  left: 14px;

  width: 30px;
  height: 30px;
  border-radius: 8px;

  display: flex;
  align-items: center;
  justify-content: center;

  background: transparent;
  color: #fff;

  transition: 0.15s ease;
}

.chatPage .iconBtn:active {
  opacity: 0.6;
  transform: scale(0.92);
}

/* ===== SEARCH ===== */
.chatPage .searchBox {
  padding: 8px 14px;
}

.chatPage .searchBox input {
  width: 100%;
  padding: 10px 12px;

  border-radius: 10px;
  border: none;
  outline: none;

  background: rgba(255,255,255,0.08);
  color: #fff;
  font-size: 14px;
}

/* ===== STORIES ===== */
.chatPage .storiesWrapper {
  display: flex;
  gap: 12px;
  padding: 10px 14px;

  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

.chatPage .storiesWrapper::-webkit-scrollbar {
  display: none;
}

.chatPage .storyItem {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 68px;
}

.chatPage .storyRing {
  width: 58px;
  height: 58px;
  border-radius: 50%;
  padding: 2px;

  background: linear-gradient(135deg, #0A84FF, #5ac8fa);
}

.chatPage .storyRing img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

.chatPage .storyUser {
  font-size: 10px;
  margin-top: 4px;
  color: var(--muted);
}

/* ===== TABS ===== */
.chatPage .tabs {
  display: flex;
  justify-content: space-around;
  border-bottom: 1px solid var(--border);
}

.chatPage .tabs span {
  padding: 10px 0;
  font-size: 13.5px;
  color: var(--muted);
}

.chatPage .tabs .active {
  color: #fff;
  font-weight: 600;
}

/* ===== CHAT LIST ===== */
.chatPage .chatList {
  flex: 1;
  overflow-y: auto;
  height: 0;

  padding-bottom: calc(80px + env(safe-area-inset-bottom));

  -webkit-overflow-scrolling: touch;
  scroll-behavior: smooth;
}

/*  SCROLL FADE */
.chatPage .chatList::before,
.chatPage .chatList::after {
  content: "";
  position: sticky;
  left: 0;
  right: 0;
  height: 10px;
  z-index: 5;
  pointer-events: none;
}

.chatPage .chatList::before {
  top: 0;
  background: linear-gradient(to bottom, #000, transparent);
}

.chatPage .chatList::after {
  bottom: 0;
  background: linear-gradient(to top, #000, transparent);
}

/* ===== CHAT ITEM ===== */
.chatPage .chatItem {
  display: flex;
  align-items: flex-start;

  padding: 10px 14px;

  border-bottom: 1px solid rgba(255,255,255,0.035);

  transition: all 0.18s ease;
}

/* hover */
.chatPage .chatItem:hover {
  background: rgba(255,255,255,0.04);
}

/* tap */
.chatPage .chatItem:active {
  background: rgba(255,255,255,0.07);
  transform: scale(0.985);
}

/* ===== AVATAR ===== */
.chatPage .avatar {
  width: 44px;
  height: 44px;
  border-radius: 50%;

  margin-right: 12px;
  margin-top: 2px;

  overflow: hidden;
  position: relative;
}

.chatPage .avatar img {
  width: 100%;
  height: 100%;
  border-radius: 50%;

  box-shadow: 0 0 0 1px rgba(255,255,255,0.04);
}

/* ===== ONLINE DOT ===== */
.onlineDot {
  position: absolute;
  bottom: 2px;
  right: 2px;

  width: 8px;
  height: 8px;
  border-radius: 50%;

  background: #22c55e;
  border: 2px solid #000;
}

/* ===== TEXT ===== */
.chatPage .chatInfo {
  flex: 1;
  min-width: 0;
}

.chatPage .chatTop {
  display: flex;
  justify-content: space-between;
  margin-bottom: 2px;
}

.chatPage .chatInfo h3 {
  font-size: 14px;
  font-weight: 600;
  color: #fff;

  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.chatPage .time {
  font-size: 11px;
  color: rgba(255,255,255,0.4);
  margin-left: 8px;
}

.chatPage .chatInfo p {
  font-size: 13px;
  color: var(--muted);

  line-height: 1.3;
  margin-top: 2px;

  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* ===== BADGE ===== */
.chatPage .unreadCount {
  background: var(--accent);
  font-size: 10px;
  padding: 3px 7px;
  border-radius: 10px;
}

/* ===== TYPING ===== */
.chatPage .typing {
  color: var(--accent);
}

.chatPage .typing::after {
  content: "...";
  animation: blink 1s infinite;
}

/* ===== ANIMATION ===== */
@keyframes blink {
  0% { opacity: 0.2; }
  50% { opacity: 1; }
  100% { opacity: 0.2; }
}
```
