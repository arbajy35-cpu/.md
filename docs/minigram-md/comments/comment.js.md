# comments/comment.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `comments/comment.js` |
| Extension | `.js` |
| Size | 4478 bytes |
| Lines | 156 |
| SHA-256 | `84a4ac5f7e408ced705f461269ab60fb9f2d118b1f6fca0f3187efbc73b62f59` |

## Project Understanding

AI analysis unavailable.

## Architecture Context

Architecture generated from local file relations.

## Dependencies

- None

## Used By

- None

## Relation Flow

```text
comments/comment.js
  ↓
  └─ No local dependencies
```

## AI Project Patterns

- None

## AI Warnings

- None

---

# Original Source Code

The following content is copied directly from:

`/storage/emulated/0/MINIGRAM1/comments/comment.js`

No AI rewriting was performed on the source code.

```javascript
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

---

Generated automatically.
