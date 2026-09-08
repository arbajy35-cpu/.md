# main_js/bundles/feed.bundle.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/bundles/feed.bundle.js` |
| Extension | `.js` |
| Bytes | 18843 |
| Lines | 686 |
| SHA-256 | `27e004df5a92e78ddf9aff8f1b62d1f9234f9e45be9a6b4446a059b476868b82` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`main_js`

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

- `setupFeedDelegation`
- `renderFeed`
- `fetchWithTimeout`
- `loadFeed`
- `createPost`
- `showEmptyFeed`
- `setData`
- `BATCH_SIZE`
- `FEED_DOM_LIMIT`
- `tapMap`
- `feed`
- `postEl`
- `postId`
- `btn`
- `img`
- `now`
- `lastTap`
- `likeBtn`
- `template`
- `start`
- `end`
- `batch`
- `fragment`
- `username`
- `avatar`
- `image`
- `caption`
- `likes`
- `comments`
- `time`
- `clone`
- `el`
- `avatarEl`
- `usernameEl`
- `likesEl`
- `commentsEl`
- `timeEl`
- `captionUser`
- `captionText`
- `likedKey`
- `old`
- `nextPage`
- `nearBottom`
- `from`
- `to`
- `postConfig`
- `data`
- `fallback`
- `div`
- `frag`

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

`/storage/emulated/0/MINIGRAM1/main_js/bundles/feed.bundle.js`

It is NOT AI generated or rewritten.

```javascript


/*
==================================================
🚀 MINIGRAM BUNDLE
FILE: feed.bundle.js
GENERATED: 2026-08-29T07:28:40.183Z
SOURCE FILES: 3
==================================================
*/



/* =================================================
   FILE: main_js/feedRenderer.js
   ================================================= */

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


/* =================================================
   END: main_js/feedRenderer.js
   ================================================= */



/* =================================================
   FILE: main_js/feedService.js
   ================================================= */

console.log("🔥 FEED SERVICE READY (STATE DRIVEN FINAL)");

//////////////////////////////////////////////////
// ⏱️ TIMEOUT WRAPPER
//////////////////////////////////////////////////

function fetchWithTimeout(promise, time = 5000){
  return Promise.race([
    promise,
    new Promise((_, reject)=>
      setTimeout(()=> reject(new Error("Timeout")), time)
    )
  ]);
}

//////////////////////////////////////////////////
// 🚀 LOAD FEED (STATE DRIVEN ARCHITECTURE)
//////////////////////////////////////////////////

async function loadFeed(){

  if(!window.STATE) return;
  if(STATE.LOADING || STATE.END) return;

  const feed = document.getElementById("feed");
  if(!feed) return;

  STATE.LOADING = true;
  window.showSkeleton?.();

  try{

    const from = STATE.PAGE * STATE.LIMIT;
    const to = from + STATE.LIMIT - 1;

    const postConfig =
      window.PAGE_CONFIG?.[window.CURRENT_PAGE]?.post;

    if(!postConfig?.enabled){
      STATE.LOADING = false;
      return;
    }

    const data = await fetchWithTimeout(
      window.POST_PLUGIN?.fetch(from, to),
      5000
    );

    //////////////////////////////////////////////////
    // ❌ NO DATA
    //////////////////////////////////////////////////

    if(!data?.length){

      STATE.END = true;

      if(STATE.PAGE === 0 && postConfig?.fallback){

        const fallback =
          window.POST_PLUGIN?.fallback?.() || [];

        // 💣 STATE UPDATE FIRST
        STATE.FEED.push(...fallback);

        // 💣 FULL RERENDER FROM STATE
        window.renderFeed?.(STATE.FEED, true);
      }

      return;
    }

    //////////////////////////////////////////////////
    // ✅ SUCCESS FLOW
    //////////////////////////////////////////////////

    // 💣 1. STATE UPDATE (SOURCE OF TRUTH)
    STATE.FEED.push(...data);

    // 💣 2. UI ALWAYS FROM STATE (NO PARTIAL DATA)
    window.renderFeed?.(STATE.FEED, true);

    STATE.PAGE++;

    console.log("✅ FEED LOADED:", data.length);

  }catch(err){

    console.error("❌ FEED ERROR:", err.message);

    const postConfig =
      window.PAGE_CONFIG?.[window.CURRENT_PAGE]?.post;

    if(STATE.PAGE === 0 && postConfig?.fallback){

      const fallback =
        window.POST_PLUGIN?.fallback?.() || [];

      STATE.FEED.push(...fallback);
      window.renderFeed?.(STATE.FEED, true);
    }

    window.toast?.("Offline mode");

  }finally{

    window.hideSkeleton?.();
    STATE.LOADING = false;
  }
}

//////////////////////////////////////////////////
// 🚀 CREATE POST (STATE DRIVEN)
//////////////////////////////////////////////////

async function createPost(){

  if(!window.supabaseClient){
    window.toast?.("Offline - cannot post");
    return;
  }

  const image = prompt("Enter image URL");
  if(!image) return;

  const caption = prompt("Caption") || "";
  const username = prompt("Username") || "user";

  window.toast?.("Uploading...");

  try{

    const { data, error } =
      await fetchWithTimeout(
        supabaseClient
          .from("minigram_feed")
          .insert([{
            image_url: image,
            caption,
            username,
            likes: 0,
            comments: 0,
            created_at: new Date().toISOString()
          }])
          .select()
          .single(),
        5000
      );

    if(error) throw error;

    window.toast?.("Uploaded");

    //////////////////////////////////////////////////
    // 💣 STATE FIRST, THEN UI
    //////////////////////////////////////////////////

    STATE.FEED.unshift(data);

    window.renderFeed?.(STATE.FEED, true);

  }catch(err){

    console.error("❌ CREATE POST ERROR:", err.message);
    window.toast?.("Failed (offline?)");

  }
}

//////////////////////////////////////////////////
// 📭 EMPTY FEED
//////////////////////////////////////////////////

function showEmptyFeed(){

  const feed = document.getElementById("feed");
  if(!feed) return;

  feed.innerHTML = `
    <div class="emptyFeed">
      <h3>No posts yet</h3>
      <p>Start by creating one 🚀</p>
    </div>
  `;
}

//////////////////////////////////////////////////
// 🌍 EXPORTS
//////////////////////////////////////////////////

window.loadFeed = loadFeed;
window.createPost = createPost;
window.showEmptyFeed = showEmptyFeed;

//////////////////////////////////////////////////
// 💀 ERROR LOG
//////////////////////////////////////////////////

window.addEventListener?.("error", e=>{
  console.log("💀 ERROR:", e.message);
});

/* =================================================
   END: main_js/feedService.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/virtualGrid.js
   ================================================= */

console.log(" virtualGrid loaded");

window.VirtualGrid = function(container){

  function createPost(post){

    const div = document.createElement("div");
    div.className = "post";

    const img = new Image();

    img.loading = "lazy";
    img.decoding = "async";

    img.src =
      post.image_url ||
      "https://via.placeholder.com/300";

    img.onerror = () => {
      img.src =
        "https://via.placeholder.com/300";
    };

    div.appendChild(img);

    return div;
  }

  function setData(list){

    const data = list || [];

    container.innerHTML = "";

    if(!data.length){

      container.innerHTML = `
        <div style="
          grid-column:1/-1;
          text-align:center;
          padding:40px 0;
          color:#888;
        ">
          No Posts Yet
        </div>
      `;

      return;
    }

    const frag =
      document.createDocumentFragment();

    data.forEach(post => {
      frag.appendChild(
        createPost(post)
      );
    });

    container.appendChild(frag);
  }

  return {
    setData
  };
};

window.addEventListener(
  "error",
  e => {
    console.log(
      " ERROR:",
      e.filename,
      e.message
    );
  }
);

/* =================================================
   END: main_js/pageloader/virtualGrid.js
   ================================================= */


```

---

Generated by MiniGram MD Intelligence V6.
