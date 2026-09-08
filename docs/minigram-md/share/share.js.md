# share/share.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `share/share.js` |
| Extension | `.js` |
| Bytes | 8218 |
| Lines | 309 |
| SHA-256 | `e55953e378f06e53902d7fff7ceeb111198d460339ac7d2307924cb50ba285f9` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`share`

The local intelligence engine detected
0 direct dependencies
and 0 consumers.

## 5. Dependencies

- None

## 6. Used By

- None

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `closeShare`
- `initShareSheet`
- `initScrollExpand`
- `createUser`
- `initSendButtons`
- `initSearch`
- `addOutsideClickClose`
- `addSwipeToClose`
- `SHARE`
- `sheet`
- `root`
- `list`
- `isExpanded`
- `top`
- `input`
- `val`
- `content`
- `startY`
- `currentY`

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- No detected errors

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/share/share.js`

It is NOT AI generated or rewritten.

```javascript
(function () {

  /* ============================= */
  /* 🧠 GLOBAL STATE */
  /* ============================= */
  if (!window._shareState) {
    window._shareState = { isOpen: false };
  }

  const SHARE = window._shareState;

  window._shareScroll = null;
  window._shareTouch = null;

  /* ============================= */
  /* 🚀 OPEN SHARE */
  /* ============================= */
  window.openShare = function () {
    const sheet = document.getElementById("shareSheet");

    if (!sheet || SHARE.isOpen) return;

    initShareSheet();

    sheet.classList.add("active");
    document.body.style.overflow = "hidden";

    // 🔥 SAFE OPEN
    requestAnimationFrame(() => {
      SHARE.isOpen = true;
    });
  };

  /* ============================= */
  /* ❌ CLOSE SHARE (FIXED) */
  /* ============================= */
  function closeShare() {
    const sheet = document.getElementById("shareSheet");
    if (!sheet) return;

    sheet.classList.remove("active");
    sheet.classList.remove("full");

    document.body.style.overflow = "";

    // 🔥 HARD RESET (CRITICAL)
    setTimeout(() => {
      SHARE.isOpen = false;
    }, 0);
  }

  /* ============================= */
  /* 🧱 INIT UI */
  /* ============================= */
  function initShareSheet() {
    const root = document.getElementById("shareSheet");
    if (!root || root.dataset.loaded) return;

    root.dataset.loaded = "true";

    root.innerHTML = `
      <div class="shareContent">
        <div class="shareHeader">
          <div class="dragBar"></div>
        </div>

        <input class="shareMsg" placeholder="Write a message...">

        <div class="searchBox">
          <span class="searchIcon">🔍</span>
          <input id="shareSearch" placeholder="Search">
        </div>

        <div class="storyBox">
          <div class="storyAvatar">
            <img src="https://i.pravatar.cc/100">
            <div class="plus">+</div>
          </div>
          <span class="storyText">Add post to your story</span>
          <span class="arrow">›</span>
        </div>

        <div id="shareList">
          ${createUser("Jotiba 💗","jotiba9359")}
          ${createUser("ribeka baby 💖","ronik_kerketta_07")}
          ${createUser("rajput vishesh","rajput_vishesh_0001")}
          ${createUser("Pradum Dugane","techodzz")}
          ${createUser("Saumya Dubey","tech__18",true)}
        </div>
      </div>
    `;

    /* 🔥 LIGHT FIREWALL (NOT OVERKILL) */
    root.addEventListener("click", (e)=>{
      e.stopPropagation();
    });

    addOutsideClickClose();
    addSwipeToClose();
    initSendButtons();
    initSearch();
    initScrollExpand();
  }

  /* ============================= */
  /* 🔥 SCROLL EXPAND */
  /* ============================= */
  function initScrollExpand() {
    const list = document.getElementById("shareList");
    const sheet = document.getElementById("shareSheet");

    if (!list || !sheet || list.dataset.scrollReady) return;
    list.dataset.scrollReady = "true";

    let isExpanded = false;

    window._shareScroll = function () {
      const top = list.scrollTop;

      if (top > 30 && !isExpanded) {
        sheet.classList.add("full");
        isExpanded = true;
      }

      if (top <= 0 && isExpanded) {
        sheet.classList.remove("full");
        isExpanded = false;
      }
    };

    list.addEventListener("scroll", window._shareScroll);
  }

  /* ============================= */
  /* 👤 USER */
  function createUser(name, username, online = false) {
    return `
    <div class="shareUser">
      <div class="left">
        <div class="avatarWrap">
          <img src="https://i.pravatar.cc/150?u=${name}" class="avatar">
          ${online ? `<span class="online"></span>` : ""}
        </div>
        <div class="userInfo">
          <div class="name">${name}</div>
          ${username ? `<div class="username">${username}</div>` : ""}
        </div>
      </div>
      <button class="sendBtn">Send</button>
    </div>
    `;
  }

  /* ============================= */
  /* 📤 SEND */
  function initSendButtons() {
    document.querySelectorAll(".sendBtn").forEach(btn => {

      if (btn.dataset.ready) return;
      btn.dataset.ready = "true";

      btn.addEventListener("click", () => {
        btn.classList.add("sent");
        btn.innerText = "Sent ✓";

        setTimeout(() => {
          btn.classList.remove("sent");
          btn.innerText = "Send";
        }, 1500);
      });

    });
  }

  /* ============================= */
  /* 🔍 SEARCH */
  function initSearch() {
    const input = document.getElementById("shareSearch");
    if (!input) return;

    input.addEventListener("input", () => {
      const val = input.value.toLowerCase();

      document.querySelectorAll(".shareUser").forEach(user => {
        user.style.display =
          user.innerText.toLowerCase().includes(val) ? "flex" : "none";
      });
    });
  }

  /* ============================= */
  /* 🖱 OUTSIDE CLICK (SAFE) */
  /* ============================= */
  function addOutsideClickClose() {

    if (document._shareOutsideReady) return;
    document._shareOutsideReady = true;

    document.addEventListener("click", (e) => {

      if (!SHARE.isOpen) return;

      const content = document.querySelector("#shareSheet .shareContent");
      if (!content) return;

      if (!content.contains(e.target)) {
        closeShare();
      }

    });
  }

  /* ============================= */
  /* 👆 SWIPE CLOSE (FIXED) */
  /* ============================= */
  function addSwipeToClose() {
    const sheet = document.getElementById("shareSheet");
    if (!sheet || sheet.dataset.swipe) return;

    sheet.dataset.swipe = "true";

    const content = sheet.querySelector(".shareContent");

    let startY = 0, diff = 0, dragging = false;

    window._shareTouch = function(e){
      const list = document.getElementById("shareList");
      if (list && list.scrollTop > 0) return;

      startY = e.touches[0].clientY;
      dragging = true;
      content.style.transition = "none";
    };

    sheet.addEventListener("touchstart", window._shareTouch);

    sheet.addEventListener("touchmove", e => {
      if (!dragging) return;

      const list = document.getElementById("shareList");
      if (list && list.scrollTop > 0) return;

      const currentY = e.touches[0].clientY;
      diff = currentY - startY;

      if (diff > 0) {
        content.style.transform = `translateY(${diff}px)`;
      }
    });

    sheet.addEventListener("touchend", (e) => {

      e.stopPropagation();

      dragging = false;
      content.style.transition = "0.3s cubic-bezier(0.22,1,0.36,1)";

      if (diff > 120) {
        closeShare();

        // 🔥 EXTRA RESET
        setTimeout(()=>{
          SHARE.isOpen = false;
        }, 50);

      } else {
        content.style.transform = "translateY(0)";
      }

      diff = 0;
    });
  }

  /* ============================= */
  /* 🧹 DESTROY */
  /* ============================= */
  window.FUNCTIONS = window.FUNCTIONS || {};

  window.FUNCTIONS.shareDestroy = function(){

    const list = document.getElementById("shareList");
    const sheet = document.getElementById("shareSheet");

    if(list && window._shareScroll){
      list.removeEventListener("scroll", window._shareScroll);
    }

    if(sheet && window._shareTouch){
      sheet.removeEventListener("touchstart", window._shareTouch);
    }

    window._shareScroll = null;
    window._shareTouch = null;

    console.log("🧹 share cleaned");
  };

  /* ============================= */
  /* 🔗 AUTO CONNECT */
  /* ============================= */
  document.addEventListener("click", (e) => {
    if (e.target.closest(".shareBtn")) {
      openShare();
    }
  });

})();
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
