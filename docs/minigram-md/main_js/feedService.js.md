# main_js/feedService.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/feedService.js` |
| Extension | `.js` |
| Bytes | 4674 |
| Lines | 200 |
| SHA-256 | `7d7b09960fa8694fa4462b0879affb58e6a5d766479620c96f0c1c3e3f04550c` |
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

- `fetchWithTimeout`
- `loadFeed`
- `createPost`
- `showEmptyFeed`
- `feed`
- `from`
- `to`
- `postConfig`
- `data`
- `fallback`
- `image`
- `caption`
- `username`

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

`/storage/emulated/0/MINIGRAM1/main_js/feedService.js`

It is NOT AI generated or rewritten.

```javascript
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
```

---

Generated by MiniGram MD Intelligence V6.
