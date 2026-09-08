# stories/stories.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `stories/stories.js` |
| Extension | `.js` |
| Bytes | 9494 |
| Lines | 439 |
| SHA-256 | `3335c95e37a3e0e9128b6cbf651c5c50506b187085fe77dfcab9c82b544269d8` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`stories`

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

- `getStoriesContainer`
- `createStoryItem`
- `item`
- `ring`
- `img`
- `user`
- `container`
- `fragment`
- `story`
- `el`

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

`/storage/emulated/0/MINIGRAM1/stories/stories.js`

It is NOT AI generated or rewritten.

```javascript
console.log("📖 stories.js loaded");

//////////////////////////////////////////////////
// 🌍 GLOBAL DATA (SAFE)
//////////////////////////////////////////////////

window.storiesData =
  window.storiesData || [

    {
      user: "Mahesh",
      avatar:
        "https://i.pravatar.cc/150?img=1"
    },

    {
      user: "Rohit",
      avatar:
        "https://i.pravatar.cc/150?img=2"
    },

    {
      user: "GamingPro",
      avatar:
        "https://i.pravatar.cc/150?img=3"
    },

    {
      user: "DevX",
      avatar:
        "https://i.pravatar.cc/150?img=4"
    }

  ];

//////////////////////////////////////////////////
// 🛡️ GLOBAL INIT STATE
//////////////////////////////////////////////////

window.STORIES_INITIALIZED = false;

//////////////////////////////////////////////////
// 📦 GET CONTAINER (SMART)
//////////////////////////////////////////////////

function getStoriesContainer(){

  return (
    document.getElementById(
      "storiesWrapper"
    )
    ||
    document.getElementById(
      "stories"
    )
    ||
    document.getElementById(
      "storiesContainer"
    )
  );
}

//////////////////////////////////////////////////
// 🎨 CREATE STORY ITEM
//////////////////////////////////////////////////

function createStoryItem(
  story,
  index
){

  const item =
    document.createElement("div");

  item.className =
    "storyItem";

  //////////////////////////////////////////////////
  // 🎨 RING
  //////////////////////////////////////////////////

  const ring =
    document.createElement("div");

  ring.className =
    "storyRing";

  //////////////////////////////////////////////////
  // 🖼️ IMAGE
  //////////////////////////////////////////////////

  const img =
    document.createElement("img");

  img.src =
    story.avatar;

  img.loading =
    "lazy";

  img.draggable =
    false;

  //////////////////////////////////////////////////
  // 👤 USERNAME
  //////////////////////////////////////////////////

  const user =
    document.createElement("div");

  user.className =
    "storyUser";

  user.textContent =
    story.user;

  //////////////////////////////////////////////////
  // 📦 BUILD
  //////////////////////////////////////////////////

  ring.appendChild(img);

  item.appendChild(ring);

  item.appendChild(user);

  //////////////////////////////////////////////////
  // 👆 CLICK EVENT
  //////////////////////////////////////////////////

  item.addEventListener(
    "click",
    () => {

      window.openStory(index);

    }
  );

  return item;
}

//////////////////////////////////////////////////
// 🎨 RENDER STORIES
//////////////////////////////////////////////////

window.renderStories =
  function(){

    const container =
      getStoriesContainer();

    //////////////////////////////////////////////////
    // ❌ NO CONTAINER
    //////////////////////////////////////////////////

    if(!container){

      console.warn(
        "⚠️ stories container not found"
      );

      return;
    }

    //////////////////////////////////////////////////
    // 🧹 HARD RESET
    //////////////////////////////////////////////////

    container.replaceChildren();

    //////////////////////////////////////////////////
    // 📦 FRAGMENT
    //////////////////////////////////////////////////

    const fragment =
      document
     .createDocumentFragment();

    //////////////////////////////////////////////////
    // 🔥 BUILD ITEMS
    //////////////////////////////////////////////////

    window.storiesData
     .forEach((story, index)=>{

        if(!story) return;

        const item =
          createStoryItem(
            story,
            index
          );

        fragment
         .appendChild(item);

      });

    //////////////////////////////////////////////////
    // 🚀 FAST APPEND
    //////////////////////////////////////////////////

    container
     .appendChild(fragment);

    //////////////////////////////////////////////////
    // 🔥 FORCE VISIBLE
    //////////////////////////////////////////////////

    container.style.display =
      "";

    container.style.visibility =
      "visible";

    container.style.opacity =
      "1";

    //////////////////////////////////////////////////
    // 🔥 RESET BAD CACHE STATE
    //////////////////////////////////////////////////

    delete container.dataset.loaded;

    //////////////////////////////////////////////////
    // ✅ SAVE STATE
    //////////////////////////////////////////////////

    window.STORIES_INITIALIZED =
      true;

    console.log(
      "📖 Stories rendered:",
      window.storiesData.length
    );
};

//////////////////////////////////////////////////
// 🚀 OPEN STORY
//////////////////////////////////////////////////

window.openStory =
  function(index){

    const story =
      window.storiesData?.[index];

    if(!story) return;

    //////////////////////////////////////////////////
    // 🌍 PASS DATA
    //////////////////////////////////////////////////

    window.STORY_INDEX =
      index;

    window.STORY_DATA =
      window.storiesData;

    //////////////////////////////////////////////////
    // 🚀 OPEN PAGE
    //////////////////////////////////////////////////

    if(
      typeof loadPage ===
      "function"
    ){

      loadPage(
        "story_view"
      );

    }else{

      console.warn(
        "⚠️ loadPage not found"
      );
    }
};

//////////////////////////////////////////////////
// ⚡ INIT STORIES
//////////////////////////////////////////////////

window.initStories =
  function(){

    console.log(
      "⚡ initStories called"
    );

    //////////////////////////////////////////////////
    // 🛡️ FORCE REINIT
    //////////////////////////////////////////////////

    window.STORIES_INITIALIZED =
      false;

    //////////////////////////////////////////////////
    // 📦 GET CONTAINER
    //////////////////////////////////////////////////

    const container =
      getStoriesContainer();

    //////////////////////////////////////////////////
    // ❌ NO DOM
    //////////////////////////////////////////////////

    if(!container){

      console.warn(
        "⚠️ initStories skipped (no DOM)"
      );

      return;
    }

    //////////////////////////////////////////////////
    // 🧹 FORCE CLEAN
    //////////////////////////////////////////////////

    container.replaceChildren();

    //////////////////////////////////////////////////
    // 🔥 FORCE VISIBLE
    //////////////////////////////////////////////////

    container.style.display =
      "";

    container.style.visibility =
      "visible";

    container.style.opacity =
      "1";

    //////////////////////////////////////////////////
    // ❌ REMOVE OLD CACHE FLAGS
    //////////////////////////////////////////////////

    delete container.dataset.loaded;

    //////////////////////////////////////////////////
    // 🎨 RENDER
    //////////////////////////////////////////////////

    window.renderStories();

    console.log(
      "✅ Stories Init Complete"
    );
};

//////////////////////////////////////////////////
// 🔥 STORIES INIT - NEW STANDARD
//////////////////////////////////////////////////

window.storiesInit = async function() {
  console.log("📱 storiesInit called");
  
  //////////////////////////////////////////////////
  // 🚀 CALL INIT STORIES
  //////////////////////////////////////////////////
  
  if (typeof window.initStories === "function") {
    window.initStories();
  } else {
    console.warn("⚠️ initStories not found");
  }
};

//////////////////////////////////////////////////
// 🧠 SAFE INIT
//////////////////////////////////////////////////

window.safeInitStories =
  function(){

    const el =
      getStoriesContainer();

    if(
      el &&
      typeof
      window.initStories ===
      "function"
    ){

      //////////////////////////////////////////////////
      // 🚀 NEXT FRAME INIT
      //////////////////////////////////////////////////

      requestAnimationFrame(
        () => {

          window.initStories();

        }
      );

    }else{

      console.warn(
        "⚠️ stories not ready"
      );
    }
};

//////////////////////////////////////////////////
// 📝 REGISTER FUNCTIONS
//////////////////////////////////////////////////

window.FUNCTIONS = window.FUNCTIONS || {};
window.FUNCTIONS.storiesInit = window.storiesInit;
window.FUNCTIONS.initStories = window.initStories;

//////////////////////////////////////////////////
// 🌍 GLOBAL EXPORT
//////////////////////////////////////////////////

window.storiesInit = window.storiesInit;

//////////////////////////////////////////////////
// 💀 ERROR LOGGER
//////////////////////////////////////////////////

window.addEventListener &&
window.addEventListener(
  "error",
  e => console.log(
    "💀 ERROR IN FILE:",
    e.filename,
    e.message
  )
);

console.log("✅ stories.js ready - storiesInit registered");
```

---

Generated by MiniGram MD Intelligence V6.
