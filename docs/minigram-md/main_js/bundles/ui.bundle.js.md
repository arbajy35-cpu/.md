# main_js/bundles/ui.bundle.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/bundles/ui.bundle.js` |
| Extension | `.js` |
| Size | 8928 bytes |
| Lines | 469 |
| SHA-256 | `feccc9d31620721f2593a184fd56ee19abeeaace5068aed77e06f7df67b58df0` |

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
main_js/bundles/ui.bundle.js
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

`/storage/emulated/0/MINIGRAM1/main_js/bundles/ui.bundle.js`

No AI rewriting was performed on the source code.

```javascript


/*
==================================================
🚀 MINIGRAM BUNDLE
FILE: ui.bundle.js
GENERATED: 2026-08-29T07:28:40.128Z
SOURCE FILES: 3
==================================================
*/



/* =================================================
   FILE: main_js/ui.js
   ================================================= */

//////////////////////////////////////////////////
// 🎨 UI SYSTEM (CLEAN VERSION)
//////////////////////////////////////////////////

console.log(
  "🎨 ui.js loaded"
);

//////////////////////////////////////////////////
// 💬 CHAT NAVIGATION
//////////////////////////////////////////////////

window.openChat =
function(){

  //////////////////////////////////////////////////
  // 🚀 LOAD CHAT PAGE
  //////////////////////////////////////////////////

  window.loadPage?.(
    "chat"
  );

};

//////////////////////////////////////////////////
// 🔔 NOTIFICATIONS NAVIGATION
//////////////////////////////////////////////////

window.openNotifications =
function(){

  //////////////////////////////////////////////////
  // 🚀 LOAD NOTIFICATIONS PAGE
  //////////////////////////////////////////////////

  window.loadPage?.(
    "notifications"
  );

};

//////////////////////////////////////////////////
// 🧹 GLOBAL PAGE CLEANER
//////////////////////////////////////////////////

window.cleanupPage =
async function(){

  try{

    //////////////////////////////////////////////////
    // 📄 CURRENT PAGE
    //////////////////////////////////////////////////

    const page =
      window.CURRENT_PAGE;

    if(!page)
      return;

    //////////////////////////////////////////////////
    // 📦 DESTROY FUNCTION NAME
    //////////////////////////////////////////////////

    const destroyName =
      page + "Destroy";

    //////////////////////////////////////////////////
    // 📦 FUNCTION
    //////////////////////////////////////////////////

    const destroyFn =

      window.FUNCTIONS?.[
        destroyName
      ];

    //////////////////////////////////////////////////
    // 🚀 RUN DESTROY
    //////////////////////////////////////////////////

    if(
      typeof destroyFn ===
      "function"
    ){

      await destroyFn();

      console.log(
        `🧹 ${page} cleaned`
      );

    }

  }catch(e){

    console.error(
      "❌ cleanupPage error:",
      e
    );

  }

};

//////////////////////////////////////////////////
// 📱 SMALL UI HELPERS
//////////////////////////////////////////////////

window.safeHide =
function(id){

  const el =
    document.getElementById(id);

  if(el){

    el.style.display =
      "none";

  }

};

window.safeShow =
function(id){

  const el =
    document.getElementById(id);

  if(el){

    el.style.display =
      "";

  }

};

//////////////////////////////////////////////////
// 🛡️ GLOBAL ERROR LOGGER
//////////////////////////////////////////////////

if(
  !window.__UI_ERROR_TRACKER
){

  window.__UI_ERROR_TRACKER =
    true;

  window.addEventListener?.(

    "error",

    e => {

      console.log(

        "💀 ERROR IN FILE:",

        e.filename,

        e.message,

        "LINE:",

        e.lineno

      );

    }

  );

}

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log(
  "🔥 UI SYSTEM READY"
);

/* =================================================
   END: main_js/ui.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/navigation.js
   ================================================= */

window.initNavigation = function(){

  const homeBtn = document.getElementById("homeBtn");
  if(homeBtn){
    homeBtn.onclick = () => loadPage("home");
  }

  const searchBtn = document.getElementById("searchBtn");
  if (searchBtn) {
    searchBtn.onclick = () => loadPage("search");
  }

  const profileBtn = document.getElementById("profileBtn");
  if (profileBtn) {
    profileBtn.onclick = () => loadPage("profile");
  }

  const reelsBtn = document.getElementById("reelsBtn");
  if (reelsBtn) {
    reelsBtn.onclick = () => loadPage("reels");
  }

};
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));


/* =================================================
   END: main_js/pageloader/navigation.js
   ================================================= */



/* =================================================
   FILE: main_js/pageloader/loader.js
   ================================================= */

//////////////////////////////////////////////////
// 🚀 OPTIMIZED PLUGIN LOADER
//////////////////////////////////////////////////

console.log(
  "🚀 Optimized Plugin Loader Ready"
);

//////////////////////////////////////////////////
// 🌍 GLOBAL CACHE
//////////////////////////////////////////////////

window.__PLUGIN_CACHE =
window.__PLUGIN_CACHE || new Map();

window.__PLUGIN_LOADING =
window.__PLUGIN_LOADING || new Set();

//////////////////////////////////////////////////
// 📱 LOW-END DETECTION
//////////////////////////////////////////////////

window.IS_LOW_END =
  window.IS_LOW_END ||
  (
    navigator.deviceMemory &&
    navigator.deviceMemory <= 4
  );

//////////////////////////////////////////////////
// 🌐 NETWORK DETECTION
//////////////////////////////////////////////////

window.NETWORK_TYPE =
  navigator.connection
  ?.effectiveType ||
  "unknown";

//////////////////////////////////////////////////
// 🚀 SAFE LOAD SCRIPT
//////////////////////////////////////////////////

async function safeLoad(src, force = false){

  if(
    window.__PLUGIN_CACHE.has(src)
    &&
    !force
  ){
    console.log(
      "♻️ Plugin Cached:",
      src
    );
    return true;
  }

  if(
    window.__PLUGIN_LOADING.has(src)
  ){
    console.log(
      "⏳ Already Loading:",
      src
    );
    return true;
  }

  window.__PLUGIN_LOADING.add(src);

  try{
    await loadScript(
      src,
      force
    );
    window.__PLUGIN_CACHE
      .set(src, true);
    console.log(
      "✅ Plugin Loaded:",
      src
    );
    return true;
  }catch(e){
    console.error(
      "❌ Plugin Failed:",
      src
    );
    return false;
  }finally{
    window.__PLUGIN_LOADING
      .delete(src);
  }
}

//////////////////////////////////////////////////
// 🚀 LOAD PAGE PLUGINS
//////////////////////////////////////////////////

async function loadPlugins(config){

  try{

    if(!config){
      console.warn(
        "⚠️ No config"
      );
      return;
    }

    const page =
      config.name ||
      "unknown";

    console.log(
      "🚀 Plugin Load:",
      page
    );

    if(
      !config.post?.enabled
    ){
      console.log(
        "⚠️ Post Plugins Disabled"
      );
      return;
    }

    if(window.IS_LOW_END){
      console.log(
        "📱 LOW-END OPTIMIZATION ENABLED"
      );
    }

    const slowNetwork =
      window.NETWORK_TYPE ===
      "slow-2g" ||
      window.NETWORK_TYPE ===
      "2g";

    console.log(
      "🚀 Loading Post Core"
    );

    await window.loadJS([
      "page_config/plugins/post/post_optimizer.js",
      "page_config/plugins/post/post.js"
    ]);

    if(
      config.post?.realtime
      &&
      navigator.onLine
      &&
      !slowNetwork
      &&
      !window.IS_LOW_END
    ){

      console.log(
        "📡 Loading Realtime"
      );

      requestIdleCallback(
        async ()=>{
          await window.loadJS([
            "page_config/plugins/post/realtime_post.js"
          ]);
        }
      ); // <-- YE TERA FIX HAI, YEHI MISSING THA

      requestIdleCallback(
        async ()=>{
          try{
            if(
              page === "home"
            ){
              console.log(
                "🚀 Background Preload"
              );
            }
          }catch(e){
            console.error(
              "❌ Preload Error:",
              e
            );
          }
        }
      );
    }

    console.log(
      "✅ Plugins Ready:",
      page
    );

  }catch(err){
    console.error(
      "❌ Plugin Error:",
      err.message
    );
  }
}

//////////////////////////////////////////////////
// 🌍 GLOBAL EXPORT
//////////////////////////////////////////////////

window.loadPlugins =
loadPlugins;

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log(
  "🎉 Optimized Plugin System Ready"
);

/* =================================================
   END: main_js/pageloader/loader.js
   ================================================= */


```

---

Generated automatically.
