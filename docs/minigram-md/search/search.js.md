# search/search.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `search/search.js` |
| Extension | `.js` |
| Bytes | 8402 |
| Lines | 331 |
| SHA-256 | `522e8f2a5b23bf2db7c920d297a1e0c07546b77fe3a555fc141053859bfc3d82` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`search`

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

- `getExploreGrid`
- `getSearchBar`
- `getDemoImages`
- `showSkeleton`
- `removeSkeleton`
- `openPost`
- `closePost`
- `renderItems`
- `loadMorePosts`
- `searchUsers`
- `handleScroll`
- `initScroll`
- `initSearchPage`
- `page`
- `loading`
- `hasMore`
- `limit`
- `MAX_PAGES`
- `exploreGrid`
- `fragment`
- `i`
- `div`
- `viewer`
- `img`
- `name`
- `baseIndex`
- `index`
- `pressTimer`
- `input`
- `results`
- `text`
- `user`
- `searchBar`
- `nearBottom`
- `grid`
- `pageContainer`

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

`/storage/emulated/0/MINIGRAM1/search/search.js`

It is NOT AI generated or rewritten.

```javascript
/* ========================================= */
/* 🔥 PRE-PAINT HARD FIX */
/* ========================================= */

document.documentElement.style.background = "#0b0b0b";
document.body.style.background = "#0b0b0b";

/* ========================================= */
/* ⚙️ STATE */
/* ========================================= */

let page = 0;
let loading = false;
let hasMore = true;

const limit = 18;
const MAX_PAGES = 5;

/* ========================================= */
/* 🧠 SAFE ELEMENT GETTERS */
/* ========================================= */

function getExploreGrid() {
  return document.getElementById("exploreGrid");
}

function getSearchBar() {
  return document.querySelector(".searchBar");
}

/* ========================================= */
/* 🧪 DEMO IMAGES */
/* ========================================= */

function getDemoImages(count = 18) {
  return Array.from({ length: count }, (_, i) => ({
    image_url: `https://picsum.photos/500?random=${i + Math.random()}`,
    username: `demo_${i}`
  }));
}

/* ========================================= */
/* 🧊 SKELETON */
/* ========================================= */

function showSkeleton(count = 9) {
  const exploreGrid = getExploreGrid();
  if (!exploreGrid) return;

  if (exploreGrid.querySelector(".skeleton")) return;

  const fragment = document.createDocumentFragment();

  for (let i = 0; i < count; i++) {
    const div = document.createElement("div");
    div.className = "gridItem skeleton";
    fragment.appendChild(div);
  }

  exploreGrid.appendChild(fragment);
}

function removeSkeleton() {
  document.querySelectorAll(".skeleton").forEach(el => el.remove());
}

/* ========================================= */
/* 🔥 POST VIEW */
/* ========================================= */

function openPost(data) {
  const viewer = document.getElementById("postViewer");
  const img = document.getElementById("postImage");
  const name = document.getElementById("postUsername");

  if (!viewer || !img || !name) return;

  img.src = data.image_url;
  name.innerText = data.username || "user";

  viewer.classList.add("active");
}

function closePost() {
  document.getElementById("postViewer")?.classList.remove("active");
}

window.closePost = closePost;

/* ========================================= */
/* 🔥 RENDER ITEMS (FIXED - NO REPAINT HACK) */
/* ========================================= */

function renderItems(items = [], append = false) {
  const exploreGrid = getExploreGrid();
  if (!exploreGrid) return;

  if (!append) exploreGrid.innerHTML = "";

  const fragment = document.createDocumentFragment();
  const baseIndex = exploreGrid.children.length;

  items.forEach((item, i) => {
    const index = baseIndex + i;

    const div = document.createElement("div");
    div.className = "gridItem";

    if (index % 9 === 2 || index % 9 === 5) {
      div.classList.add("big");
    }

    const img = document.createElement("img");
    img.loading = "lazy";
    img.decoding = "async";
    img.src = item.image_url || "https://via.placeholder.com/400x400";

    img.onload = () => img.classList.add("loaded");
    img.onerror = () => {
      img.src = "https://via.placeholder.com/400x400?text=Image";
    };

    let pressTimer;

    div.addEventListener("touchstart", () => {
      img.style.transform = "scale(1.08)";
      pressTimer = setTimeout(() => openPost(item), 500);
    }, { passive: true });

    div.addEventListener("touchend", () => {
      img.style.transform = "scale(1)";
      clearTimeout(pressTimer);
    }, { passive: true });

    div.addEventListener("touchmove", () => {
      clearTimeout(pressTimer);
      img.style.transform = "scale(1)";
    }, { passive: true });

    div.appendChild(img);
    fragment.appendChild(div);
  });

  exploreGrid.appendChild(fragment);

  console.log("🔥 GRID CHILDREN:", exploreGrid.children.length);
}

/* ========================================= */
/* 🌐 LOAD POSTS */
/* ========================================= */

async function loadMorePosts() {
  if (loading || !hasMore) return;

  const exploreGrid = getExploreGrid();
  if (!exploreGrid) return;

  loading = true;
  showSkeleton(6);

  try {
    if (!window.supabaseClient) throw new Error("Supabase missing");

    const { data, error } = await window.supabaseClient
      .from("minigram_feed")
      .select("id, image_url, username")
      .range(page * limit, (page + 1) * limit - 1);

    if (error || !data || data.length === 0) throw new Error("DB FAIL");

    renderItems(data, true);
    page++;

  } catch (err) {
    console.warn("⚠️ Demo fallback", err);

    renderItems(getDemoImages(limit), true);
    page++;

  } finally {
    removeSkeleton();

    if (page >= MAX_PAGES) hasMore = false;

    loading = false;
  }
}

/* ========================================= */
/* 🔍 SEARCH USERS */
/* ========================================= */

async function searchUsers() {
  const input = document.getElementById("searchInput");
  const results = document.getElementById("searchResults");

  if (!input || !results) return;

  const text = input.value.trim();

  if (text === "") {
    results.innerHTML = "";
    return;
  }

  try {
    const { data, error } = await window.supabaseClient
      .from("minigram_feed")
      .select("*")
      .ilike("username", `%${text}%`)
      .limit(20);

    if (error || !data) throw new Error();

    results.innerHTML = "";

    data.forEach(post => {
      const user = document.createElement("div");
      user.className = "searchUser";

      user.innerHTML = `
        <img src="${post.avatar_url || "https://i.pravatar.cc/150"}">
        <span>${post.username}</span>
      `;

      results.appendChild(user);
    });

  } catch (err) {
    results.innerHTML = "";

    for (let i = 0; i < 5; i++) {
      const user = document.createElement("div");
      user.className = "searchUser";

      user.innerHTML = `
        <img src="https://i.pravatar.cc/150?img=${i}">
        <span>User_${i}</span>
      `;

      results.appendChild(user);
    }
  }
}

window.searchUsers = searchUsers;

/* ========================================= */
/* 📜 SCROLL (FIXED - WINDOW BASED) */
/* ========================================= */

function handleScroll() {
  const searchBar = getSearchBar();

  const nearBottom =
    window.scrollY + window.innerHeight >=
    document.body.scrollHeight - 600;

  if (nearBottom) {
    loadMorePosts();
  }

  if (searchBar) {
    if (window.scrollY > 20) {
      searchBar.classList.add("scrolled");
    } else {
      searchBar.classList.remove("scrolled");
    }
  }
}

/* ========================================= */
/* 🚀 INIT SCROLL (FIXED) */
/* ========================================= */

function initScroll() {
  if (window.__SEARCH_SCROLL_INIT) return;

  window.__SEARCH_SCROLL_INIT = true;

  window.addEventListener("scroll", handleScroll, { passive: true });
}

/* ========================================= */
/* 🚀 INIT SEARCH PAGE */
/* ========================================= */

function initSearchPage() {
  requestAnimationFrame(() => {
    const grid = getExploreGrid();
    if (!grid) return;

    initScroll();

    const searchBar = getSearchBar();
    if (searchBar) searchBar.style.opacity = "1";

    const pageContainer = document.querySelector(".searchPage");
    pageContainer?.classList.remove("searching");

    page = 0;
    loading = false;
    hasMore = true;

    /* ✅ ONLY ONCE REPAINT FIX (IMPORTANT) */
    grid.innerHTML = "";

    grid.style.display = "none";
    void grid.offsetHeight;
    grid.style.display = "grid";

    loadMorePosts();

    console.log("🚀 Search Ready");
  });
}

/* ========================================= */
/* 🚀 START */
/* ========================================= */

initSearchPage();

/* ========================================= */
/* 💀 GLOBAL ERROR */
/* ========================================= */

window.addEventListener?.("error", e => {
  console.log("💀 SEARCH ERROR:", e.filename, e.message, "LINE:", e.lineno);
});
```

---

Generated by MiniGram MD Intelligence V6.
