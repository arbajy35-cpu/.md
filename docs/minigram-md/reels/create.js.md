# reels/create.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `reels/create.js` |
| Extension | `.js` |
| Bytes | 3919 |
| Lines | 150 |
| SHA-256 | `55a98ff85641c58a37082b1df5f440d6c682a02c96afe94fee67fa837477fe77` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`reels`

The local intelligence engine detected
0 direct dependencies
and 2 consumers.

## 5. Dependencies

- None

## 6. Used By

- `reels/main.js`
- `reels/reels.bundle.js`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `createReel`
- `reel`
- `video`
- `progress`
- `bar`
- `overlay`
- `actions`
- `lastTap`
- `now`
- `likeBtn`
- `heart`

## 9. Exports

- `default/export`

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- **HIGH** — JavaScript Syntax Error: Unexpected token 'export'

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

`/storage/emulated/0/MINIGRAM1/reels/create.js`

It is NOT AI generated or rewritten.

```javascript
console.log("🎬 create.js loaded");

// ================================
// 🎬 CREATE REEL (FINAL PRO)
// ================================
function createReel(data = {}){

  // ================================
  // 🧱 ROOT
  // ================================
  const reel = document.createElement("div");
  reel.className = "reel";

  // ================================
  // 🎥 VIDEO
  // ================================
  const video = document.createElement("video");

  video.src = data.video || "";
  video.loop = true;
  video.muted = true;
  video.playsInline = true;
  video.autoplay = false;

  video.setAttribute("muted", "");
  video.setAttribute("playsinline", "");

  // 🔥 LOADING STATE
  video.classList.add("reelVideo", "loading");

  // 🎯 READY STATE SWITCH
  video.addEventListener("loadeddata", () => {
    video.classList.remove("loading");
    video.classList.add("ready");
  });

  reel.appendChild(video);

  // ================================
  // 🔝 PROGRESS BAR
  // ================================
  const progress = document.createElement("div");
  progress.className = "progressBar";

  const bar = document.createElement("div");
  bar.className = "bar";

  progress.appendChild(bar);
  reel.appendChild(progress);

  // ================================
  // 🎯 OVERLAY
  // ================================
  const overlay = document.createElement("div");
  overlay.className = "overlay";

  overlay.innerHTML = `
    <div class="reelUser">
      <span class="reelUserName">${data.user || "user"}</span>
      <button class="instaBtn">Follow</button>
    </div>

    <div class="reelCaption">
      ${data.caption || ""}
    </div>
  `;

  reel.appendChild(overlay);

  // ================================
  // ❤️ ACTIONS (RIGHT SIDE)
  // ================================
  const actions = document.createElement("div");
  actions.className = "reelActions";

  actions.innerHTML = `
    <div class="actionGroup like">
      <div class="iconCircle">
        <span class="material-symbols-rounded">favorite</span>
      </div>
      <div class="actionCount">${window.format?.(data.likes || 0)}</div>
    </div>

    <div class="actionGroup comment">
      <div class="iconCircle">💬</div>
      <div class="actionCount">${window.format?.(data.comments || 0)}</div>
    </div>

    <div class="actionGroup share">
      <div class="iconCircle">🔗</div>
      <div class="actionCount">Share</div>
    </div>
  `;

  reel.appendChild(actions);

  // ================================
  // ❤️ DOUBLE TAP LIKE
  // ================================
  let lastTap = 0;

  reel.addEventListener("click", (e) => {
    const now = Date.now();

    if(now - lastTap < 300){
      // ❤️ LIKE TRIGGER
      const likeBtn = reel.querySelector(".like");
      likeBtn?.classList.add("liked");

      // 💥 HEART ANIMATION
      const heart = document.createElement("div");
      heart.className = "likeAnimation";
      heart.innerHTML = "❤️";

      reel.appendChild(heart);

      setTimeout(() => heart.remove(), 600);
    }

    lastTap = now;
  });

  // ================================
  // 🎥 AUTO PLAY CONTROL (HOOK READY)
  // ================================
  reel.play = () => {
    video.play().catch(() => {});
    window.startProgress?.(reel, video);
  };

  reel.pause = () => {
    video.pause();
  };

  return reel;
}


// ================================
// 🌍 GLOBAL EXPOSE
// ================================
window.createReel = createReel;


// ================================
// 🔥 ESBUILD FIX (VERY IMPORTANT)
// ================================
export {};
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
