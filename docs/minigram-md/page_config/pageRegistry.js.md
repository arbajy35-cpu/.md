# page_config/pageRegistry.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `page_config/pageRegistry.js` |
| Extension | `.js` |
| Bytes | 8178 |
| Lines | 266 |
| SHA-256 | `fb4631b0146b8befd088aa75091ef9b504b9b5f35d58451af414b847249af674` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`page_config`

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

- `applyAutoPageScope`
- `hata`
- `styleTag`
- `manifest`
- `res`
- `fileId`
- `script`

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

`/storage/emulated/0/MINIGRAM1/page_config/pageRegistry.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
// 📦 PAGE REGISTRY (FINAL UPGRADE + AUTO SCOPE)
//////////////////////////////////////////////////

console.log(
  "🚀 pageRegistry.js loaded"
);

//////////////////////////////////////////////////
// 📦 GLOBAL PAGE CONFIG STORAGE
//////////////////////////////////////////////////

window.PAGE_CONFIG =
  window.PAGE_CONFIG || {};

window.__CURRENT_PAGE = null;
window.__PAGE_LIST = []; // manifest se fill hoga

//////////////////////////////////////////////////
// 🔥 AUTO PAGE SCOPE SYSTEM - 1 TIME SETUP
//////////////////////////////////////////////////

function applyAutoPageScope(pageName){

  try{
    if(!pageName) return;

    //////////////////////////////////////////////////
    // 🧹 OLD PAGE CLASS HATAO
    //////////////////////////////////////////////////

    if(window.__PAGE_LIST.length > 0){
      window.__PAGE_LIST.forEach(p => {
        document.body.classList.remove(p);
        document.body.classList.remove(`page-${p}`);
      });
    } else if(window.__CURRENT_PAGE){
      document.body.classList.remove(window.__CURRENT_PAGE);
      document.body.classList.remove(`page-${window.__CURRENT_PAGE}`);
    }

    //////////////////////////////////////////////////
    // ✨ NEW PAGE CLASS LAGAO -.home.page-home
    //////////////////////////////////////////////////

    document.body.classList.add(pageName); //.home
    document.body.classList.add(`page-${pageName}`); //.page-home
    document.body.setAttribute("data-page", pageName);

    window.__CURRENT_PAGE = pageName;

    //////////////////////////////////////////////////
    // 🛡️ AUTO ISOLATION CSS - CIRCLE BUG + FPS FIX
    //////////////////////////////////////////////////

    let styleTag = document.getElementById("__AUTO_SCOPE_FIX__");

    if(!styleTag){
      styleTag = document.createElement("style");
      styleTag.id = "__AUTO_SCOPE_FIX__";
      document.head.appendChild(styleTag);
    }

    styleTag.innerHTML = `
      /* 🔥 AUTO FIX FOR ALL PAGES - ${pageName} */
      [data-page="${pageName}"] { height: 100dvh; overflow-y: auto; }

      /* Post kabhi circle nahi banega */
     .${pageName}.post-image,
     .page-${pageName}.post-image,
      [data-page="${pageName}"].post-image {
        border-radius: 12px!important;
        width: 100%!important;
        height: auto!important;
        aspect-ratio: auto!important;
        object-fit: cover!important;
      }

      /* Story hamesha circle rahega */
     .${pageName}.story-avatar img,
     .page-${pageName}.story-avatar img {
        border-radius: 50%!important;
        aspect-ratio: 1/1!important;
        object-fit: cover!important;
      }

      /* FPS / CPU / Debug overlay hamesha hide */
      [data-page] [class*="FPS:"],
      [data-page] [class*="CPU:"],
     .fps-counter,.debug-overlay {
        display: none!important;
        opacity: 0!important;
        pointer-events: none!important;
      }
    `;

    console.log(
      `🔥 Auto Scope Applied:.${pageName} +.page-${pageName} + [data-page="${pageName}"]`
    );

  }catch(e){
    console.error("❌ applyAutoPageScope error:", e);
  }
}

//////////////////////////////////////////////////
// 🚀 REGISTER PAGE CONFIG (UPGRADED)
//////////////////////////////////////////////////

window.registerPageConfig =
function(name, config){

  try{

    //////////////////////////////////////////////////
    // 🛡️ VALIDATE
    //////////////////////////////////////////////////

    if(!name){
      console.warn("⚠️ Config name missing");
      return;
    }

    if(!config){
      console.warn(`⚠️ Config object missing: ${name}`);
      return;
    }

    //////////////////////////////////////////////////
    // 💾 SAVE CONFIG
    //////////////////////////////////////////////////

    window.PAGE_CONFIG[name] = config;

    // Page list me add karo taki purana class hata sake
    if(!window.__PAGE_LIST.includes(name)){
      window.__PAGE_LIST.push(name);
    }

    //////////////////////////////////////////////////
    // 🔥 AUTO SCOPE TRIGGER - YAHI MAIN HAI
    //////////////////////////////////////////////////

    // Agar ye current page hai ya pehla page hai to scope lagao
    if(!window.__CURRENT_PAGE || window.__CURRENT_PAGE === name){
      applyAutoPageScope(name);
    }

    //////////////////////////////////////////////////
    // ✅ SUCCESS
    //////////////////////////////////////////////////

    console.log(`✅ Config Registered: ${name} ->.${name}`);

  }catch(e){
    console.error("❌ registerPageConfig error:", e);
  }
};

//////////////////////////////////////////////////
// 🔄 SWITCH PAGE (MANIFEST SE AUTO)
//////////////////////////////////////////////////

window.switchPage = async function(pageName){

  try{
    if(!pageName) return;

    console.log(`🔄 Switching to: ${pageName}`);

    // Manifest se id nikalo
    let manifest = {};
    try{
      const res = await fetch("page_config/manifest.json", { cache: "no-store" });
      manifest = await res.json();
      window.__PAGE_LIST = Object.keys(manifest);
    }catch(err){
      console.warn("⚠️ Manifest not loaded, using local list");
    }

    const fileId = manifest[pageName];

    if(!fileId){
      console.warn(`⚠️ Page ${pageName} not found in manifest.json`);
      // Phir bhi scope laga do taki.classname ban jaye
      applyAutoPageScope(pageName);
      return;
    }

    //////////////////////////////////////////////////
    // 🔥 SCOPE PEHLE LAGAO
    //////////////////////////////////////////////////

    applyAutoPageScope(pageName);

    //////////////////////////////////////////////////
    // 📦 CONFIG LOAD KARO (agar load nahi hua)
    //////////////////////////////////////////////////

    if(!window.PAGE_CONFIG[pageName]){
      const script = document.createElement("script");
      script.src = `page_config/${fileId}.js?v=${Date.now()}`;
      script.onload = () => {
        console.log(`📦 ${pageName} config loaded: ${fileId}.js`);
        if(typeof window[`init${pageName.charAt(0).toUpperCase()+pageName.slice(1)}`] === "function"){
          window[`init${pageName.charAt(0).toUpperCase()+pageName.slice(1)}`]();
        }
      };
      document.head.appendChild(script);
    }

  }catch(e){
    console.error("❌ switchPage error:", e);
  }
};

//////////////////////////////////////////////////
// 🔍 GET CONFIG
//////////////////////////////////////////////////

window.getPageConfig = function(name){
  return (window.PAGE_CONFIG?.[name]);
};

//////////////////////////////////////////////////
// 📋 GET ALL CONFIGS
//////////////////////////////////////////////////

window.getAllPageConfigs = function(){
  return (window.PAGE_CONFIG || {});
};

//////////////////////////////////////////////////
// 🧪 DEBUG
//////////////////////////////////////////////////

window.debugPageConfig = function(name){
  console.log("📦 PAGE CONFIG:", name, window.PAGE_CONFIG?.[name]);
  console.log("📍 CURRENT PAGE:", window.__CURRENT_PAGE);
  console.log("📍 BODY CLASSES:", document.body.className);
};

//////////////////////////////////////////////////
// 🛡️ GLOBAL ERROR LOGGER
//////////////////////////////////////////////////

if(!window.__PAGE_REGISTRY_ERROR){
  window.__PAGE_REGISTRY_ERROR = true;
  window.addEventListener?.("error", e => {
    console.log("💀 PAGE REGISTRY ERROR:", e.filename, e.message, "LINE:", e.lineno);
  });
}

//////////////////////////////////////////////////
// 🎉 READY
//////////////////////////////////////////////////

console.log("🔥 PAGE REGISTRY READY + AUTO SCOPE READY");

// Pehli baar manifest load karke list bana lo
fetch("page_config/manifest.json", { cache: "no-store" })
 .then(r=>r.json())
 .then(m=>{
    window.__PAGE_LIST = Object.keys(m);
    console.log("📋 Pages from manifest:", window.__PAGE_LIST);
  }).catch(()=>{});
```

---

Generated by MiniGram MD Intelligence V6.
