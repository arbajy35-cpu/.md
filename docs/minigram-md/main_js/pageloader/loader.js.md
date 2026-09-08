# main_js/pageloader/loader.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/pageloader/loader.js` |
| Extension | `.js` |
| Bytes | 3936 |
| Lines | 215 |
| SHA-256 | `7152e231ee14a423f20841fa2faf697ad46040a188c5083ec86d774a4e81cec3` |
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

- `safeLoad`
- `loadPlugins`
- `page`
- `slowNetwork`

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

`/storage/emulated/0/MINIGRAM1/main_js/pageloader/loader.js`

It is NOT AI generated or rewritten.

```javascript
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
```

---

Generated by MiniGram MD Intelligence V6.
