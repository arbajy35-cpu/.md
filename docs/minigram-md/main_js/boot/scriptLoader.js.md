# main_js/boot/scriptLoader.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/boot/scriptLoader.js` |
| Extension | `.js` |
| Bytes | 7074 |
| Lines | 293 |
| SHA-256 | `a1746017089b85fa341ba2677be56cef4e413eb982690262abf6e576ebe713dc` |
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

- `loadScript`
- `old`
- `promise`
- `existing`
- `done`
- `fail`
- `s`

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

`/storage/emulated/0/MINIGRAM1/main_js/boot/scriptLoader.js`

It is NOT AI generated or rewritten.

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

Generated by MiniGram MD Intelligence V6.
