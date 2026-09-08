# main_js/config_Loader.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/config_Loader.js` |
| Extension | `.js` |
| Bytes | 11163 |
| Lines | 580 |
| SHA-256 | `e86626d98e9d0f47ce3ad4bb1c446341fd15e604b1d311f8f4bd5fd02a2823c3` |
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
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `CRITICAL_ERRORS_REPORT.md`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `loadManifest`
- `loadConfigFile`
- `loadConfig`
- `res`
- `s`
- `task`
- `num`
- `important`
- `page`

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

`/storage/emulated/0/MINIGRAM1/main_js/config_Loader.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
// 🚀 CONFIG LOADER V2 (ULTRA OPTIMIZED)
//////////////////////////////////////////////////

console.log("🚀 CONFIG LOADER V2");

//////////////////////////////////////////////////
// 🌍 GLOBAL STORAGE
//////////////////////////////////////////////////

window.CONFIG_MANIFEST =
  window.CONFIG_MANIFEST || null;

window.PAGE_CONFIG =
  window.PAGE_CONFIG || {};

window.__LOADED_CONFIGS =
  window.__LOADED_CONFIGS || new Set();

window.__CONFIG_LOADING =
  window.__CONFIG_LOADING || new Map();

//////////////////////////////////////////////////
// 🚀 REGISTER CONFIG
//////////////////////////////////////////////////

window.registerPageConfig =
function(name, config){

  try{

    //////////////////////////////////////////////////
    // 🛡️ VALIDATE
    //////////////////////////////////////////////////

    if(!name || !config){

      console.warn(
        "⚠️ Invalid config"
      );

      return;

    }

    //////////////////////////////////////////////////
    // 💾 SAVE
    //////////////////////////////////////////////////

    window.PAGE_CONFIG[name] =
      config;

    //////////////////////////////////////////////////
    // 📦 TRACK
    //////////////////////////////////////////////////

    window.__LOADED_CONFIGS
      .add(name);

    console.log(
      `✅ Config Registered: ${name}`
    );

  }catch(e){

    console.error(
      "❌ registerPageConfig error:",
      e
    );

  }

};

//////////////////////////////////////////////////
// 📦 LOAD MANIFEST
//////////////////////////////////////////////////

async function loadManifest(){

  //////////////////////////////////////////////////
  // ♻️ CACHE HIT
  //////////////////////////////////////////////////

  if(window.CONFIG_MANIFEST){

    return window.CONFIG_MANIFEST;

  }

  try{

    //////////////////////////////////////////////////
    // 🌐 FETCH
    //////////////////////////////////////////////////

    const res =
      await fetch(
        "page_config/manifest.json"
      );

    //////////////////////////////////////////////////
    // ❌ FAIL
    //////////////////////////////////////////////////

    if(!res.ok){

      throw new Error(
        "Manifest fetch failed"
      );

    }

    //////////////////////////////////////////////////
    // 💾 SAVE
    //////////////////////////////////////////////////

    window.CONFIG_MANIFEST =
      await res.json();

    console.log(
      "✅ Manifest Loaded"
    );

    return window.CONFIG_MANIFEST;

  }catch(e){

    console.error(
      "❌ Manifest error:",
      e
    );

    //////////////////////////////////////////////////
    // 🛡️ FALLBACK
    //////////////////////////////////////////////////

    window.CONFIG_MANIFEST =
      {};

    return {};

  }

}

//////////////////////////////////////////////////
// 📜 LOAD CONFIG FILE
//////////////////////////////////////////////////

async function loadConfigFile(num){

  return new Promise(resolve=>{

    //////////////////////////////////////////////////
    // 🛡️ INVALID
    //////////////////////////////////////////////////

    if(!num){

      console.warn(
        "⚠️ Invalid config number"
      );

      resolve(false);

      return;

    }

    //////////////////////////////////////////////////
    // ♻️ SCRIPT CACHE
    //////////////////////////////////////////////////

    if(

      document.querySelector(

        `script[data-config="${num}"]`

      )

    ){

      console.log(
        `♻️ Config Cached: ${num}`
      );

      resolve(true);

      return;

    }

    //////////////////////////////////////////////////
    // 📜 SCRIPT
    //////////////////////////////////////////////////

    const s =
      document.createElement(
        "script"
      );

    //////////////////////////////////////////////////
    // 🚀 SRC
    //////////////////////////////////////////////////

    s.src =
      `page_config/${num}.js`;

    //////////////////////////////////////////////////
    // 📦 DATA
    //////////////////////////////////////////////////

    s.dataset.config =
      num;

    //////////////////////////////////////////////////
    // ⚡ ASYNC
    //////////////////////////////////////////////////

    s.async = true;

    //////////////////////////////////////////////////
    // ✅ SUCCESS
    //////////////////////////////////////////////////

    s.onload = ()=>{

      console.log(
        `✅ Config Loaded: ${num}`
      );

      resolve(true);

    };

    //////////////////////////////////////////////////
    // ❌ ERROR
    //////////////////////////////////////////////////

    s.onerror = ()=>{

      console.error(
        `❌ Config Failed: ${num}`
      );

      resolve(false);

    };

    //////////////////////////////////////////////////
    // 🚀 APPEND
    //////////////////////////////////////////////////

    document.head.appendChild(s);

  });

}

//////////////////////////////////////////////////
// 🚀 SMART CONFIG LOADER
//////////////////////////////////////////////////

async function loadConfig(page){

  try{

    //////////////////////////////////////////////////
    // 🛡️ INVALID
    //////////////////////////////////////////////////

    if(!page){

      return;

    }

    //////////////////////////////////////////////////
    // ♻️ ALREADY READY
    //////////////////////////////////////////////////

    if(window.PAGE_CONFIG?.[page]){

      console.log(
        `♻️ Config Ready: ${page}`
      );

      return;

    }

    //////////////////////////////////////////////////
    // ⏳ ALREADY LOADING
    //////////////////////////////////////////////////

    if(

      window.__CONFIG_LOADING
      .has(page)

    ){

      return await
        window.__CONFIG_LOADING
        .get(page);

    }

    //////////////////////////////////////////////////
    // 🚀 LOAD TASK
    //////////////////////////////////////////////////

    const task =
    (async()=>{

      //////////////////////////////////////////////////
      // 📦 MANIFEST
      //////////////////////////////////////////////////

      await loadManifest();

      //////////////////////////////////////////////////
      // 🔢 GET NUMBER
      //////////////////////////////////////////////////

      const num =

        window.CONFIG_MANIFEST?.[
          page
        ];

      //////////////////////////////////////////////////
      // ❌ NO CONFIG
      //////////////////////////////////////////////////

      if(!num){

        console.warn(
          `⚠️ No config: ${page}`
        );

        return;

      }

      //////////////////////////////////////////////////
      // 📜 LOAD FILE
      //////////////////////////////////////////////////

      await loadConfigFile(num);

      //////////////////////////////////////////////////
      // ✅ VERIFY
      //////////////////////////////////////////////////

      if(

        window.PAGE_CONFIG?.[
          page
        ]

      ){

        console.log(
          `✅ Config Ready: ${page}`
        );

      }else{

        console.warn(
          `⚠️ Config Missing: ${page}`
        );

      }

    })();

    //////////////////////////////////////////////////
    // 💾 SAVE TASK
    //////////////////////////////////////////////////

    window.__CONFIG_LOADING
      .set(page, task);

    //////////////////////////////////////////////////
    // ⏳ WAIT
    //////////////////////////////////////////////////

    await task;

    //////////////////////////////////////////////////
    // 🧹 CLEAN
    //////////////////////////////////////////////////

    window.__CONFIG_LOADING
      .delete(page);

  }catch(e){

    console.error(
      "❌ loadConfig error:",
      e
    );

  }

}

//////////////////////////////////////////////////
// 🧠 ENSURE PAGE CONFIG
//////////////////////////////////////////////////

window.ensurePageConfig =
async function(page){

  //////////////////////////////////////////////////
  // 🛡️ INVALID
  //////////////////////////////////////////////////

  if(!page){

    console.warn(
      "⚠️ Page missing"
    );

    return;

  }

  //////////////////////////////////////////////////
  // 🚀 TRUE LAZY LOAD
  //////////////////////////////////////////////////

  if(

    !window.PAGE_CONFIG?.[
      page
    ]

  ){

    await loadConfig(page);

  }else{

    console.log(
      `♻️ Config Already Loaded: ${page}`
    );

  }

};

//////////////////////////////////////////////////
// 🚀 PRELOAD IMPORTANT PAGES
//////////////////////////////////////////////////

window.preloadConfigs =
async function(){

  try{

    //////////////////////////////////////////////////
    // ⚡ ONLY IMPORTANT
    //////////////////////////////////////////////////

    const important = [

      "home",
      "profile",
      "search"

    ];

    //////////////////////////////////////////////////
    // 💤 IDLE LOAD
    //////////////////////////////////////////////////

    requestIdleCallback(
      async ()=>{

        for(const page of important){

          //////////////////////////////////////////////////
          // 🛡️ SKIP EXISTING
          //////////////////////////////////////////////////

          if(

            window.PAGE_CONFIG?.[
              page
            ]

          ) continue;

          //////////////////////////////////////////////////
          // 🚀 LOAD
          //////////////////////////////////////////////////

          await loadConfig(page);

        }

      }
    );

  }catch(e){

    console.error(
      "❌ preloadConfigs:",
      e
    );

  }

};

//////////////////////////////////////////////////
// 💀 ERROR LOGGER
//////////////////////////////////////////////////

if(

  !window.__CONFIG_ERROR_TRACKER

){

  window.__CONFIG_ERROR_TRACKER =
    true;

  window.addEventListener?.(

    "error",

    e => {

      console.log(

        "💀 CONFIG ERROR:",

        e.filename,

        e.message,

        "LINE:",

        e.lineno

      );

    }

  );

}

//////////////////////////////////////////////////
// 🔍 DEBUG
//////////////////////////////////////////////////

window.debugPageConfig =
function(page){

  console.log(
    "📦 PAGE CONFIG:",
    page,
    window.PAGE_CONFIG?.[page]
  );

};

//////////////////////////////////////////////////
// 🚀 READY
//////////////////////////////////////////////////

console.log(
  "🔥 CONFIG LOADER V2 READY"
);
```

---

Generated by MiniGram MD Intelligence V6.
