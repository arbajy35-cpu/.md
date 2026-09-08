# main_js/feedRenderer.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/feedRenderer.js` |
| Extension | `.js` |
| Size | 11813 bytes |
| Lines | 364 |
| SHA-256 | `afdd156b06cfe55a9ab3cbc4ac3a7a6e3437560bd9f63ed51dd29717d8cbcd74` |

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
main_js/feedRenderer.js
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

`/storage/emulated/0/MINIGRAM1/main_js/feedRenderer.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 🚀 FEED RENDERER V4 - MERGED ULTIMATE VERSION
// Features: Event Delegation + Memory Management
// Fixes: 500 Listeners → 1 Listener, Zero Memory Leak
//////////////////////////////////////////////////

console.log("🚀 FEED RENDERER V4 MERGED LOADED");

//////////////////////////////////////////////////
// 📦 CONFIG
//////////////////////////////////////////////////

const BATCH_SIZE = window.IS_LOW_END ? 5 : 10;
const FEED_DOM_LIMIT = window.IS_LOW_END ? 10 : 30;

//////////////////////////////////////////////////
// 🌍 GLOBAL STATE
//////////////////////////////////////////////////

window.FEED_RENDER_STATE = window.FEED_RENDER_STATE || {
  posts: [],
  page: 0,
  loading: false,
  ended: false
};

//////////////////////////////////////////////////
// 🎯 DOUBLE TAP TRACKER (Memory Safe)
//////////////////////////////////////////////////

const tapMap = new Map(); // postId -> lastTapTime

//////////////////////////////////////////////////
// 🎯 EVENT DELEGATION - SINGLE LISTENER SETUP
//////////////////////////////////////////////////

(function setupFeedDelegation() {
  const feed = document.getElementById("feed");
  
  // Prevent duplicate setup
  if (!feed || feed.dataset.delegated === "true") return;
  feed.dataset.delegated = "true";

  feed.addEventListener("click", (e) => {
    const postEl = e.target.closest(".post");
    if (!postEl) return;
    
    const postId = postEl.id.replace("post-", "");
    if (!postId) return;

    // ❤️ LIKE BUTTON
    if (e.target.closest(".likeBtn")) {
      const btn = postEl.querySelector(".likeBtn");
      window.likePost?.(btn, postId);
      return;
    }

    // 💬 COMMENT BUTTON
    if (e.target.closest(".commentBtn")) {
      window.openComments?.(postId);
      return;
    }

    // 📤 SHARE BUTTON
    if (e.target.closest(".shareBtn")) {
      const img = postEl.querySelector(".postImage");
      window.sharePost?.(img?.src || img?.dataset?.id);
      return;
    }

    // 💾 SAVE BUTTON
    if (e.target.closest(".saveBtn")) {
      window.savePost?.(postId);
      return;
    }

    // 🖼️ DOUBLE TAP LIKE ON IMAGE
    if (e.target.closest(".postImage")) {
      const now = Date.now();
      const lastTap = tapMap.get(postId) || 0;
      
      if (now - lastTap < 300) {
        const img = postEl.querySelector(".postImage");
        window.animateHeart?.(img);
        const likeBtn = postEl.querySelector(".likeBtn");
        window.likePost?.(likeBtn, postId);
      }
      
      tapMap.set(postId, now);
    }
  }, { passive: true });

  console.log("✅ Feed Delegation Active - 1 Listener for all posts");
})();

//////////////////////////////////////////////////
// 🚀 MAIN RENDER FEED
//////////////////////////////////////////////////

function renderFeed(posts = [], append = true, page = 0) {
  //////////////////////////////////////////////////
  // 📦 GET ELEMENTS
  //////////////////////////////////////////////////

  const feed = document.getElementById("feed");
  const template = document.getElementById("postTemplate");

  //////////////////////////////////////////////////
  // 🛑 SAFETY CHECKS
  //////////////////////////////////////////////////

  if (!feed || !template) {
    console.error("❌ feed/template missing");
    return;
  }

  if (!Array.isArray(posts)) {
    console.error("❌ posts must be an array");
    return;
  }

  //////////////////////////////////////////////////
  // 🧹 REMOVE EMPTY STATE
  //////////////////////////////////////////////////

  document.getElementById("emptyFeed")?.remove();

  //////////////////////////////////////////////////
  // 📦 BATCH CALCULATION
  //////////////////////////////////////////////////

  const start = page * BATCH_SIZE;
  const end = start + BATCH_SIZE;
  const batch = posts.slice(start, end);

  //////////////////////////////////////////////////
  // 🛑 NO POSTS IN BATCH
  //////////////////////////////////////////////////

  if (!batch.length) {
    window.FEED_RENDER_STATE.ended = true;
    console.log("⚠️ No more posts to load");
    return;
  }

  //////////////////////////////////////////////////
  // 🚀 CREATE DOCUMENT FRAGMENT
  //////////////////////////////////////////////////

  const fragment = document.createDocumentFragment();

  //////////////////////////////////////////////////
  // 🚀 RENDER EACH POST
  //////////////////////////////////////////////////

  batch.forEach(post => {
    //////////////////////////////////////////////////
    // 🛡️ VALIDATION
    //////////////////////////////////////////////////

    if (!post || !post.id) return;

    //////////////////////////////////////////////////
    // ♻️ DUPLICATE CHECK
    //////////////////////////////////////////////////

    if (document.getElementById("post-" + post.id)) return;

    //////////////////////////////////////////////////
    // 📊 EXTRACT POST DATA
    //////////////////////////////////////////////////

    const username = post.username || "user";
    const avatar = post.avatar_url || `https://i.pravatar.cc/150?u=${encodeURIComponent(username)}`;
    const image = post.image_url || "";
    const caption = post.caption || "";
    const likes = Number(post.likes_count ?? post.likes ?? 0);
    const comments = Number(post.comments_count ?? post.comments ?? 0);
    const time = (typeof window.formatTime === "function" && post.created_at)
      ? window.formatTime(post.created_at)
      : "";

    //////////////////////////////////////////////////
    // 📄 CLONE TEMPLATE
    //////////////////////////////////////////////////

    const clone = template.content.cloneNode(true);
    const el = clone.querySelector(".post");

    if (!el) return;

    //////////////////////////////////////////////////
    // 🆔 SET POST ID & DATA
    //////////////////////////////////////////////////

    el.id = "post-" + post.id;
    el.dataset.id = post.id; // Important for delegation

    //////////////////////////////////////////////////
    // ⚡ CACHE FREQUENTLY USED ELEMENTS
    //////////////////////////////////////////////////

    const avatarEl = clone.querySelector(".avatar");
    const usernameEl = clone.querySelector(".username");
    const img = clone.querySelector(".postImage");
    const likesEl = clone.querySelector(".postLikes");
    const commentsEl = clone.querySelector(".postComments");
    const timeEl = clone.querySelector(".postTime");
    const captionUser = clone.querySelector(".postCaption b");
    const captionText = clone.querySelector(".captionText");
    const likeBtn = clone.querySelector(".likeBtn");

    //////////////////////////////////////////////////
    // ❤️ RESTORE LIKED STATE FROM STORAGE
    //////////////////////////////////////////////////

    const likedKey = "liked_" + post.id;
    if (localStorage.getItem(likedKey) === "true") {
      likeBtn?.classList.add("liked");
    }

    //////////////////////////////////////////////////
    // 👤 SET USER DATA
    //////////////////////////////////////////////////

    if (avatarEl) avatarEl.src = avatar;
    if (usernameEl) usernameEl.textContent = username;

    //////////////////////////////////////////////////
    // 🖼️ SET IMAGE
    //////////////////////////////////////////////////

    if (img) {
      img.loading = "lazy";
      img.decoding = "async";
      img.src = image;
      img.dataset.id = post.id;

      img.onload = () => {
        img.classList.remove("loading");
        img.classList.add("loaded");
      };

      img.onerror = () => {
        img.src = "https://via.placeholder.com/400x400?text=No+Image";
      };
    }

    //////////////////////////////////////////////////
    // ❤️ SET LIKES
    //////////////////////////////////////////////////

    if (likesEl) {
      likesEl.textContent = likes + " likes";
      likesEl.dataset.likes = likes;
      likesEl.id = "likes-" + post.id;
    }

    //////////////////////////////////////////////////
    // 💬 SET COMMENTS
    //////////////////////////////////////////////////

    if (commentsEl) {
      commentsEl.textContent = comments + " comments";
      commentsEl.dataset.comments = comments;
      commentsEl.id = "comments-" + post.id;
    }

    //////////////////////////////////////////////////
    // 🕒 SET TIME
    //////////////////////////////////////////////////

    if (timeEl) timeEl.textContent = time;

    //////////////////////////////////////////////////
    // 📝 SET CAPTION
    //////////////////////////////////////////////////

    if (captionUser) captionUser.textContent = username;
    if (captionText) captionText.textContent = caption;

    //////////////////////////////////////////////////
    // 🚀 ADD TO FRAGMENT (NO LISTENERS HERE!)
    //////////////////////////////////////////////////

    append ? fragment.appendChild(clone) : fragment.prepend(clone);
  });

  //////////////////////////////////////////////////
  // 🚀 SINGLE DOM INSERT WITH BATCHING
  //////////////////////////////////////////////////

  requestAnimationFrame(() => {
    append ? feed.appendChild(fragment) : feed.prepend(fragment);

    //////////////////////////////////////////////////
    // 🧹 AUTO CLEANUP - MEMORY MANAGEMENT
    //////////////////////////////////////////////////

    while (feed.children.length > FEED_DOM_LIMIT) {
      const old = feed.firstElementChild;
      if (old) {
        // Clean up tap tracker memory
        const postId = old.id.replace("post-", "");
        tapMap.delete(postId);
        feed.removeChild(old);
      }
    }
  });

  //////////////////////////////////////////////////
  // 📊 UPDATE STATE
  //////////////////////////////////////////////////

  window.FEED_RENDER_STATE.page = page;
  console.log("✅ Batch Rendered | Page:", page, "| Posts:", batch.length);
}

//////////////////////////////////////////////////
// 🚀 LOAD MORE FEED
//////////////////////////////////////////////////

window.loadMoreFeed = function () {
  if (window.FEED_RENDER_STATE.ended || window.FEED_RENDER_STATE.loading) return;

  window.FEED_RENDER_STATE.loading = true;
  const nextPage = window.FEED_RENDER_STATE.page + 1;

  // Use requestIdleCallback if available, fallback to setTimeout
  (window.requestIdleCallback || ((cb) => setTimeout(cb, 0)))(() => {
    renderFeed(window.FEED_RENDER_STATE.posts, true, nextPage);
    window.FEED_RENDER_STATE.loading = false;
  });
};

//////////////////////////////////////////////////
// 🚀 INFINITE SCROLL SETUP
//////////////////////////////////////////////////

window.initFeedInfiniteScroll = function () {
  // Remove previous listener
  window.removeEventListener("scroll", window.__FEED_SCROLL_HANDLER);

  window.__FEED_SCROLL_HANDLER = function () {
    const nearBottom = window.innerHeight + window.scrollY >= document.body.offsetHeight - 1200;
    if (nearBottom) window.loadMoreFeed?.();
  };

  window.addEventListener("scroll", window.__FEED_SCROLL_HANDLER, { passive: true });
  console.log("✅ Infinite Scroll Initialized");
};

//////////////////////////////////////////////////
// 🌍 GLOBAL EXPORT
//////////////////////////////////////////////////

window.renderFeed = renderFeed;

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log("🎉 FEED RENDERER V4 READY - 1 Listener, 0 Leaks, Ultra Stable");

```

---

Generated automatically.
