# main_js/boot/scriptLoader.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/scriptLoader.js` |
| Extension | `.js` |
| Size | 7074 bytes |
| Lines | 293 |
| SHA-256 | `a1746017089b85fa341ba2677be56cef4e413eb982690262abf6e576ebe713dc` |

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
main_js/boot/scriptLoader.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/scriptLoader.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 📜 MINIGRAM SCRIPT LOADER
// RACE-SAFE VERSION
//////////////////////////////////////////////////

function loadScript(
    src,
    force = false
){

    if(!src){

        return Promise.reject(
            new Error(
                "Missing script source"
            )
        );

    }


    //////////////////////////////////////////////////
    // FORCE RELOAD
    //////////////////////////////////////////////////

    if(force){

        const old =
            document.querySelector(
                `script[data-src="${src}"]`
            );

        old?.remove();

        window.__LOADED_SCRIPTS
            .delete(src);

        window.__LOADING_SCRIPTS
            .delete(src);

    }


    //////////////////////////////////////////////////
    // ALREADY LOADED
    //////////////////////////////////////////////////

    if(
        window.__LOADED_SCRIPTS
            .has(src)
    ){

        return Promise.resolve();

    }


    //////////////////////////////////////////////////
    // CURRENTLY LOADING
    //////////////////////////////////////////////////

    if(
        window.__LOADING_SCRIPTS
            .has(src)
    ){

        return window.__LOADING_SCRIPTS
            .get(src);

    }


    //////////////////////////////////////////////////
    // CREATE PROMISE
    //////////////////////////////////////////////////

    const promise =
        new Promise(
            (resolve,reject)=>{

                //////////////////////////////////////////////////
                // EXISTING SCRIPT
                //////////////////////////////////////////////////

                const existing =
                    document.querySelector(
                        `script[data-src="${src}"]`
                    );


                if(existing){

                    //////////////////////////////////////////////////
                    // ALREADY COMPLETED
                    //////////////////////////////////////////////////

                    if(
                        existing.dataset.loaded ===
                        "true"
                    ){

                        window.__LOADED_SCRIPTS
                            .set(src,true);

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        resolve();

                        return;

                    }


                    //////////////////////////////////////////////////
                    // EXISTING SCRIPT SUCCESS
                    //////////////////////////////////////////////////

                    const done = () => {

                        existing.dataset.loaded =
                            "true";

                        window.__LOADED_SCRIPTS
                            .set(src,true);

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        resolve();

                    };


                    //////////////////////////////////////////////////
                    // EXISTING SCRIPT ERROR
                    //////////////////////////////////////////////////

                    const fail = () => {

                        window.__LOADING_SCRIPTS
                            .delete(src);

                        reject(
                            new Error(
                                "Failed to load: " +
                                src
                            )
                        );

                    };


                    existing.addEventListener(
                        "load",
                        done,
                        {once:true}
                    );


                    existing.addEventListener(
                        "error",
                        fail,
                        {once:true}
                    );


                    return;

                }


                //////////////////////////////////////////////////
                // CREATE NEW SCRIPT
                //////////////////////////////////////////////////

                const s =
                    document.createElement(
                        "script"
                    );


                s.src =
                    src.includes("?")
                        ? src + "&v=1"
                        : src + "?v=1";


                s.dataset.src =
                    src;


                //////////////////////////////////////////////////
                // ASYNC
                //////////////////////////////////////////////////

                s.async = true;


                //////////////////////////////////////////////////
                // SUCCESS
                //////////////////////////////////////////////////

                s.onload = () => {

                    s.dataset.loaded =
                        "true";

                    window.__LOADED_SCRIPTS
                        .set(src,true);

                    window.__LOADING_SCRIPTS
                        .delete(src);

                    resolve();

                };


                //////////////////////////////////////////////////
                // ERROR
                //////////////////////////////////////////////////

                s.onerror = () => {

                    window.__LOADING_SCRIPTS
                        .delete(src);

                    reject(
                        new Error(
                            "Failed to load: " +
                            src
                        )
                    );

                };


                //////////////////////////////////////////////////
                // APPEND
                //////////////////////////////////////////////////

                (
                    document.head ||
                    document.body ||
                    document.documentElement
                ).appendChild(s);

            }
        );


    //////////////////////////////////////////////////
    // STORE PROMISE
    //////////////////////////////////////////////////

    window.__LOADING_SCRIPTS
        .set(
            src,
            promise
        );


    //////////////////////////////////////////////////
    // CLEANUP
    //////////////////////////////////////////////////

    promise.finally(()=>{

        if(
            window.__LOADING_SCRIPTS
                .get(src) === promise
        ){

            window.__LOADING_SCRIPTS
                .delete(src);

        }

    }).catch(()=>{});


    return promise;

}


//////////////////////////////////////////////////
// 🚀 PUBLIC BOOT LOADER
//////////////////////////////////////////////////

window.loadBootScript =
    loadScript;
```

---

Generated automatically.
