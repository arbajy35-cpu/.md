# profile/profile.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `profile/profile.js` |
| Extension | `.js` |
| Bytes | 4675 |
| Lines | 195 |
| SHA-256 | `7230df08df51c7ff10c20ac034f688b323aff4e1a8ef53ffaaa24a6e8ebff278` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`profile`

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

- `waitForDom`
- `setActiveTab`
- `switchTab`
- `currentUser`
- `isInitialized`
- `usernameTopEl`
- `postsGrid`
- `usernameEl`
- `grid`
- `i`
- `tabs`
- `finalData`
- `res`

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

`/storage/emulated/0/MINIGRAM1/profile/profile.js`

It is NOT AI generated or rewritten.

```javascript

console.log("✅ profile.js loaded");

// ================================
// GLOBAL STATE
// ================================
let currentUser = null;
let isInitialized = false;
let usernameTopEl;
let postsGrid, videosGrid, userTab;
let usernameEl, nameEl, bioEl, postsEl, followersEl, followingEl, avatarEl;

// 🔥 VIRTUAL GRID
let grid = null;


// ================================
// WAIT DOM
// ================================
function waitForDom(){
  return new Promise(res=>{
    const i = setInterval(()=>{
      if(document.getElementById("postsGrid")){
        clearInterval(i);
        res();
      }
    },50);
  });
}


// ================================
// TABS SYSTEM
// ================================
function setActiveTab(index){
  const tabs = document.querySelectorAll(".tabs i");
  tabs.forEach((tab,i)=>{
    tab.classList.toggle("active", i === index);
  });
}

function switchTab(index){

  if(!postsGrid || !videosGrid || !userTab) return;

  setActiveTab(index);

  postsGrid.style.display =
  index === 0 ? "grid" : "none";
  videosGrid.style.display = index === 1 ? "grid" : "none";
  userTab.style.display = index === 2 ? "block" : "none";

  window.scrollTo({top:0});
}

window.switchTab = switchTab;


// ================================
// 🔥 INIT PROFILE (FINAL)
// ================================
window.initProfile = async function(){

  console.log("⚡ initProfile called");

  await waitForDom();

  postsGrid = document.getElementById("postsGrid");
videosGrid = document.getElementById("videosGrid");
userTab = document.getElementById("userTab");

usernameEl =
document.getElementById("username");

usernameTopEl =
document.getElementById("usernameTop");

nameEl =
document.getElementById("name");

postsEl =
document.getElementById("posts");

  if(!isInitialized){
    isInitialized = true;
  }

  // 🔥 IMPORTANT
  switchTab(0);

  // 🔥 ALWAYS INIT GRID (NO DEPEND ON AUTH)
  setTimeout(async () => {

    grid = new window.VirtualGrid(postsGrid);

    let finalData = [];

    try {

      // ================================
      // AUTH TRY
      // ================================
      const res = await supabaseClient.auth.getUser();

      if(res && res.data && res.data.user){
        currentUser = res.data.user;
        console.log("✅ User found");
       
       const { data: profile, error: profileError } =
  await supabaseClient
    .from("profiles")
.select("*")
.eq("id", currentUser.id)
.single();
    
    console.log("PROFILE:", profile);
console.log("PROFILE ERROR:", profileError);

if (!profileError && profile) {

  console.log("✅ Profile loaded", profile);

  if (usernameEl)
    usernameEl.textContent = profile.username || "";

  if (nameEl)
    nameEl.textContent = profile.fullname || "";

if (usernameTopEl)
  usernameTopEl.textContent = profile.username || "";
  
}

        // ================================
        // FETCH POSTS
        // ================================
        const { data, error } =
          await supabaseClient
            .from("minigram_feed")
            .select("*")
            .eq("user_id", currentUser.id)
            .order("created_at",{ascending:false})
            .limit(50);
        
        console.log("POSTS:", data);
console.log("POST ERROR:", error);

        if(!error && data && data.length){
          finalData = data;
          console.log("✅ Real posts:", data.length);
        }

      } else {
        console.warn("⚠️ No user (using fake data)");
      }

    } catch(err){
      console.error("❌ Auth failed → using fake data", err);
    }

    // ================================
    // 💣 FALLBACK (MOST IMPORTANT)
    // ================================
    if(!finalData.length){

      finalData = Array.from({length: 30}).map((_,i)=>({
        image_url: "https://picsum.photos/300?random=" + i
      }));

      console.log("🔥 Fake data loaded");
    }

    // ================================
    // 🚀 FINAL RENDER
    // ================================
    grid.setData(finalData);

  }, 200);
};


// ================================
// 🧹 DESTROY
// ================================
window.FUNCTIONS = window.FUNCTIONS || {};

window.FUNCTIONS.profileDestroy = function(){

  console.log("🧹 profile cleaned");

  if(postsGrid) postsGrid.innerHTML = "";
  grid = null;
};
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
