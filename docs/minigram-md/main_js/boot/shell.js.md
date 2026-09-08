# main_js/boot/shell.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/shell.js` |
| Extension | `.js` |
| Size | 2831 bytes |
| Lines | 145 |
| SHA-256 | `6ccef573ee847a96c4c75ae85569a49e91b8a9bc42a456cfc1b6ee4b0534c6b3` |

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
main_js/boot/shell.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/shell.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// ⚡ MINIGRAM SHELL
//////////////////////////////////////////////////

let SHELL_READY =
    false;


//////////////////////////////////////////////////
// 🚀 PREPARE INSTANT SHELL
//////////////////////////////////////////////////

function prepareInstantShell(){

    //////////////////////////////////////////////////
    // PREVENT DUPLICATE WORK
    //////////////////////////////////////////////////

    if(SHELL_READY){

        return;

    }


    const appbar =
        document.getElementById(
            "appbar"
        );

    const nav =
        document.getElementById(
            "bottomNav"
        );

    const main =
        document.getElementById(
            "mainContent"
        );


    //////////////////////////////////////////////////
    // SHOW APP SHELL
    //////////////////////////////////////////////////

    appbar?.classList.remove(
        "hidden"
    );

    nav?.classList.remove(
        "hidden"
    );


    //////////////////////////////////////////////////
    // STABLE MAIN VISIBILITY
    //////////////////////////////////////////////////

    if(main){

        main.style.visibility =
            "visible";

        main.style.opacity =
            "1";

    }


    //////////////////////////////////////////////////
    // ICONS
    //////////////////////////////////////////////////

    try{

        window.initIcons?.();

    }catch(e){}


    //////////////////////////////////////////////////
    // REMOVE GLOBAL LOADER
    //////////////////////////////////////////////////

    document
        .getElementById(
            "loader"
        )
        ?.remove();


    SHELL_READY =
        true;


    //////////////////////////////////////////////////
    // SHELL TIMING
    //////////////////////////////////////////////////

    const shellTime =
        performance.now() -
        window.__MINIGRAM_T0;


    window.__MINIGRAM_TIMINGS
        .shell =
        shellTime;


    console.log(
        `⚡ FIRST UI SHELL READY: ${
            shellTime.toFixed(2)
        } ms`
    );


    //////////////////////////////////////////////////
    // ACTUAL NEXT FRAME
    //////////////////////////////////////////////////

    requestAnimationFrame(()=>{

        requestAnimationFrame(()=>{

            const painted =
                performance.now() -
                window.__MINIGRAM_T0;


            window.__MINIGRAM_TIMINGS
                .firstPaint =
                painted;


            console.log(
                `🎨 FIRST UI FRAME: ${
                    painted.toFixed(2)
                } ms`
            );

        });

    });

}
```

---

Generated automatically.
