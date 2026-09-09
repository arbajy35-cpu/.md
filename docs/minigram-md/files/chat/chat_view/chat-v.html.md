# chat-v.html

## 1. File Identity

- **File Name:** `chat-v.html`
- **File Path:** `chat/chat_view/chat-v.html`
- **Extension:** `.html`
- **Lines:** 125
- **Bytes:** 3905

## 2. What This File Does

- **[FACT]** This source file contains 125 lines and is part of the MiniGram source tree.

## 3. 5th-Standard Explanation

- **[INFERRED]** The file can be understood by examining its executable code, references, functions, events and relationships with other source files.

## 4. When It Runs

- **[UNKNOWN]** Not determinable from static source analysis.

## 5. Called By

- None detected.

## 6. Calls / Uses

- None detected.

## 7. Imports

- `chat-v.js` — line 122
- `chat-v.css` — line 9

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

- **[INFERRED]** Static size: 3905 bytes; 125 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting chat/chat_view/chat-v.html, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `chat-v.js` — line 122
- `chat-v.css` — line 9
- `click` — line 22
- `input` — line 87
- `keydown` — line 88
- `click` — line 102

## 42. Exact Line References

- `chat-v.js` — line 122
- `chat-v.css` — line 9
- `click` — line 22
- `input` — line 87
- `keydown` — line 88
- `click` — line 102

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

Source file: chat/chat_view/chat-v.html.

---

# SOURCE CODE

> Source: `chat/chat_view/chat-v.html`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chat View</title>

  <!-- CSS -->
  <link rel="stylesheet" href="chat-v.css">
</head>

<body>

<div class="chatContainer">

  <!-- ================================
       HEADER
  ================================= -->
  <div class="chatHeader">

    <!-- BACK -->
    <div class="backBtn rippleBtn" onclick="FUNCTIONS.goBackChat()">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none">
        <path d="M15 18L9 12L15 6" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- USER INFO -->
    <div class="userInfo">
      <div class="avatarWrapper">
        <img class="chatUserAvatar" src="" alt="user">
      </div>

      <div class="userText">
        <div class="chatUserName">user</div>
        <div class="userStatus">online</div>
      </div>
    </div>

    <!-- ACTIONS -->
    <div class="actions">

      <!-- 🔥 CALL (UPDATED WITH ID) -->
      <div class="iconBtn rippleBtn" id="callBtn">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M22 16.92V20a2 2 0 0 1-2.18 2A19.86 19.86 0 0 1 3 5.18 2 2 0 0 1 5 3h3.09a2 2 0 0 1 2 1.72c.12.9.32 1.77.59 2.6a2 2 0 0 1-.45 2.11L9.03 10.97a16 16 0 0 0 6 6l1.54-1.2a2 2 0 0 1 2.11-.45c.83.27 1.7.47 2.6.59A2 2 0 0 1 22 16.92z"
            stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>

      <!-- MENU -->
      <div class="iconBtn rippleBtn">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="white">
          <circle cx="12" cy="5" r="2"/>
          <circle cx="12" cy="12" r="2"/>
          <circle cx="12" cy="19" r="2"/>
        </svg>
      </div>

    </div>
  </div>

  <!-- ================================
       MESSAGES
  ================================= -->
  <div class="chatMessages" id="chatMessages"></div>

  <!-- ================================
       INPUT
  ================================= -->
  <div class="chatInputBox">
    <div class="chatInputWrapper">

      <!-- ADD -->
      <div class="iconBtn rippleBtn">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M12 5V19M5 12H19" stroke="white" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </div>

      <!-- INPUT -->
      <textarea
        class="chatInput"
        rows="1"
        placeholder="Message..."
        autocomplete="off"
        oninput="FUNCTIONS.handleInput(this)"
        onkeydown="handleEnter(event)"
      ></textarea>

      <!-- VOICE -->
      <div class="iconBtn voiceBtn rippleBtn">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M12 14a3 3 0 0 0 3-3V5a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Z"
            stroke="white" stroke-width="2" stroke-linecap="round"/>
          <path d="M19 11a7 7 0 0 1-14 0M12 18v3M8 21h8"
            stroke="white" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </div>

      <!-- SEND -->
      <button class="sendBtn rippleBtn" onclick="FUNCTIONS.sendMessage()">
        <svg width="18" height="18" viewBox="0 0 24 24">
          <path d="M22 2L11 13" stroke="black" stroke-width="2" stroke-linecap="round"/>
          <path d="M22 2L15 22L11 13L2 9L22 2Z" fill="black"/>
        </svg>
      </button>

    </div>
  </div>

</div>

<!-- ================================
     MESSAGE MENU
================================= -->
<div id="msgMenu" class="msgMenu">
  <div class="menuItem rippleBtn" id="copyBtn">Copy</div>
  <div class="menuItem rippleBtn" id="selectBtn">Select All</div>
</div>

<script src="chat-v.js"></script>

</body>
</html>
```
