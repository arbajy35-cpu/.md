# main_js/boot/boot.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/boot.js` |
| Extension | `.js` |
| Size | 2976 bytes |
| Lines | 143 |
| SHA-256 | `2254267bd3d6efc23d85af48e2a6b0cfef79904b81000e9486e62ee75c3f733d` |

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
main_js/boot/boot.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/boot.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 🚀 MINIGRAM BOOT
// FAST + STABLE + SMOOTH FIRST PAINT
//
// ORCHESTRATOR
//////////////////////////////////////////////////

console.log(
    "🚀 MINIGRAM BOOT START"
);


//////////////////////////////////////////////////
// 🚀 START APP
//////////////////////////////////////////////////

function startApp(){

    //////////////////////////////////////////////////
    // SHELL
    //////////////////////////////////////////////////

    prepareInstantShell();


    //////////////////////////////////////////////////
    // HOME
    //////////////////////////////////////////////////

    startHome();

}


//////////////////////////////////////////////////
// 🚀 MAIN BOOT
//////////////////////////////////////////////////

async function boot(){

    try{

        //////////////////////////////////////////////////
        // INSTANT SKELETON
        //////////////////////////////////////////////////

        initInstantSkeleton();


        //////////////////////////////////////////////////
        // FIRST SHELL
        //////////////////////////////////////////////////

        prepareInstantShell();


        //////////////////////////////////////////////////
        // CRITICAL SYSTEMS
        //////////////////////////////////////////////////

        const authenticated =
            await loadCriticalBoot();


        //////////////////////////////////////////////////
        // AUTH FAILED
        //////////////////////////////////////////////////

        if(!authenticated){

            return;

        }


        //////////////////////////////////////////////////
        // HOME
        //////////////////////////////////////////////////

        startApp();


        //////////////////////////////////////////////////
        // HEAVY SYSTEMS
        // DELAYED UNTIL BROWSER IS IDLE
        //////////////////////////////////////////////////

        scheduleHeavySystems();


        //////////////////////////////////////////////////
        // CRITICAL BOOT COMPLETE
        //////////////////////////////////////////////////

        const bootTime =
            performance.now() -
            window.__MINIGRAM_T0;


        window.__MINIGRAM_TIMINGS
            .boot =
            bootTime;


        console.log(
            `🎉 CRITICAL BOOT COMPLETE: ${
                bootTime.toFixed(2)
            } ms`
        );


    }catch(e){

        console.error(
            "🔥 BOOT CRASH:",
            e
        );

    }

}


//////////////////////////////////////////////////
// 🚀 START
//////////////////////////////////////////////////

if(
    document.readyState ===
    "loading"
){

    document.addEventListener(
        "DOMContentLoaded",
        boot,
        {once:true}
    );

}else{

    boot();

}
```

---

Generated automatically.
