# main_js/boot/home.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/home.js` |
| Extension | `.js` |
| Size | 1993 bytes |
| Lines | 86 |
| SHA-256 | `8504636730aac94712c14112c27053adfe7a5c82956c7d8bc90184093afb2813` |

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
main_js/boot/home.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/home.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 🏠 MINIGRAM HOME START
//////////////////////////////////////////////////

function startHome(){

    //////////////////////////////////////////////////
    // HOME IS CRITICAL
    //////////////////////////////////////////////////

    Promise.resolve().then(async()=>{

        try{

            //////////////////////////////////////////////////
            // CONFIG
            //////////////////////////////////////////////////

            if(
                typeof window.ensurePageConfig ===
                "function"
            ){

                await window.ensurePageConfig(
                    "home"
                );

            }


            //////////////////////////////////////////////////
            // LOAD HOME
            //////////////////////////////////////////////////

            if(
                typeof window.loadPage ===
                "function"
            ){

                await window.loadPage(
                    "home",
                    false
                );


                //////////////////////////////////////////////////
                // HOME READY TIMING
                //////////////////////////////////////////////////

                const homeTime =
                    performance.now() -
                    window.__MINIGRAM_T0;


                window.__MINIGRAM_TIMINGS
                    .home =
                    homeTime;


                console.log(
                    `🏠 HOME / FEED READY: ${
                        homeTime.toFixed(2)
                    } ms`
                );


            }else{

                console.error(
                    "❌ loadPage missing"
                );

            }

        }catch(e){

            console.error(
                "❌ HOME LOAD FAIL:",
                e
            );

        }

    });

}
```

---

Generated automatically.
