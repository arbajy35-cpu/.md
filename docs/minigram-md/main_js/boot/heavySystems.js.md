# main_js/boot/heavySystems.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/boot/heavySystems.js` |
| Extension | `.js` |
| Bytes | 7539 |
| Lines | 398 |
| SHA-256 | `1f106abd137f9f5010d0996404fc53718ffa8c0029caa7a6cb81766085ef9314` |
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

- `loadHeavyScript`
- `isSlowNetwork`
- `loadAdaptiveBundle`
- `loadRealtimeSystems`
- `loadFPSMonitor`
- `scheduleHeavySystems`
- `type`
- `start`

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

`/storage/emulated/0/MINIGRAM1/main_js/boot/heavySystems.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
//  MINIGRAM HEAVY SYSTEMS V2
// IDLE + BUNDLE FIRST
//
// IMPORTANT:
// Heavy systems MUST NOT block critical boot.
//
// CRITICAL:
// - No PageLoader dependency here
// - No duplicate loading
// - Bundle-first
// - Slow network protection
// - Idle loading
// - Safe failure
//////////////////////////////////////////////////


console.log(
    " HEAVY SYSTEMS V2 READY"
);


//////////////////////////////////////////////////
//  STATE
//////////////////////////////////////////////////

window.__HEAVY_SYSTEMS_STARTED__ =
    !!window.__HEAVY_SYSTEMS_STARTED__;


window.__HEAVY_SYSTEMS_READY__ =
    !!window.__HEAVY_SYSTEMS_READY__;


window.__HEAVY_SYSTEMS_PROMISE__ =
    window.__HEAVY_SYSTEMS_PROMISE__ || null;


//////////////////////////////////////////////////
//  SAFE SCRIPT LOADER
//////////////////////////////////////////////////

function loadHeavyScript(src){

    if(
        typeof window.loadScript !==
        "function"
    ){

        return Promise.reject(
            new Error(
                "loadScript() unavailable"
            )
        );

    }


    return window.loadScript(src);

}


//////////////////////////////////////////////////
//  NETWORK CHECK
//////////////////////////////////////////////////

function isSlowNetwork(){

    const type =
        window.NETWORK_TYPE;


    return (
        type === "slow-2g" ||
        type === "2g"
    );

}


//////////////////////////////////////////////////
//  LOAD ADAPTIVE
//////////////////////////////////////////////////

async function loadAdaptiveBundle(){

    if(
        window.__ADAPTIVE_BUNDLE_READY__
    ){

        return true;

    }


    await loadHeavyScript(
        "main_js/bundles/adaptive.bundle.js"
    );


    window.__ADAPTIVE_BUNDLE_READY__ =
        true;


    console.log(
        " ADAPTIVE BUNDLE READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  REALTIME
//////////////////////////////////////////////////

async function loadRealtimeSystems(){

    if(
        window.__REALTIME_SYSTEM_READY__
    ){

        return true;

    }


    if(
        !navigator.onLine
    ){

        console.log(
            " REALTIME SKIPPED: OFFLINE"
        );

        return false;

    }


    if(
        isSlowNetwork()
    ){

        console.log(
            " REALTIME SKIPPED: SLOW NETWORK"
        );

        return false;

    }


    await Promise.all([

        loadHeavyScript(
            "main_js/realtime.js"
        ),

        loadHeavyScript(
            "main_js/pageloader/realtime.js"
        )

    ]);


    window.__REALTIME_SYSTEM_READY__ =
        true;


    console.log(
        " REALTIME SYSTEM READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  FPS MONITOR
//////////////////////////////////////////////////

async function loadFPSMonitor(){

    if(
        !window.DEBUG_MODE
    ){

        return false;

    }


    if(
        window.__FPS_MONITOR_READY__
    ){

        return true;

    }


    await loadHeavyScript(
        "main_js/debug/fpsMonitor.js"
    );


    window.__FPS_MONITOR_READY__ =
        true;


    console.log(
        " FPS MONITOR READY"
    );


    return true;

}


//////////////////////////////////////////////////
//  START HEAVY SYSTEMS
//////////////////////////////////////////////////

function scheduleHeavySystems(){

    //////////////////////////////////////////////////
    // DUPLICATE PROTECTION
    //////////////////////////////////////////////////

    if(
        window.__HEAVY_SYSTEMS_PROMISE__
    ){

        return window.__HEAVY_SYSTEMS_PROMISE__;

    }


    //////////////////////////////////////////////////
    // ALREADY STARTED
    //////////////////////////////////////////////////

    if(
        window.__HEAVY_SYSTEMS_STARTED__
    ){

        return Promise.resolve(
            true
        );

    }


    window.__HEAVY_SYSTEMS_STARTED__ =
        true;


    //////////////////////////////////////////////////
    // IDLE SCHEDULER
    //////////////////////////////////////////////////

    const start =
        () => {

            window.__HEAVY_SYSTEMS_PROMISE__ =
                (async()=>{

                    try{

                        console.log(
                            " HEAVY SYSTEMS START"
                        );


                        //////////////////////////////////////////////////
                        // ADAPTIVE
                        //////////////////////////////////////////////////

                        await loadAdaptiveBundle();


                        //////////////////////////////////////////////////
                        // DEBUG FPS
                        //////////////////////////////////////////////////

                        await loadFPSMonitor();


                        //////////////////////////////////////////////////
                        // REALTIME
                        //////////////////////////////////////////////////

                        await loadRealtimeSystems();


                        //////////////////////////////////////////////////
                        // READY
                        //////////////////////////////////////////////////

                        window.__HEAVY_SYSTEMS_READY__ =
                            true;


                        console.log(
                            " HEAVY SYSTEMS READY"
                        );


                        return true;


                    }catch(error){

                        console.error(
                            " HEAVY SYSTEM ERROR:",
                            error
                        );


                        //////////////////////////////////////////////////
                        // IMPORTANT:
                        // Heavy system failure MUST NOT
                        // break the application.
                        //////////////////////////////////////////////////

                        return false;

                    }

                })();


            return window.__HEAVY_SYSTEMS_PROMISE__;

        };


    //////////////////////////////////////////////////
    // REQUEST IDLE CALLBACK
    //////////////////////////////////////////////////

    if(
        typeof window.requestIdleCallback ===
        "function"
    ){

        requestIdleCallback(
            start,
            {
                timeout:3000
            }
        );

    }else{

        setTimeout(
            start,
            100
        );

    }


    return window.__HEAVY_SYSTEMS_PROMISE__;

}


//////////////////////////////////////////////////
//  PUBLIC API
//////////////////////////////////////////////////

window.scheduleHeavySystems =
    scheduleHeavySystems;


//////////////////////////////////////////////////
//  READY
//////////////////////////////////////////////////

console.log(
    " Heavy Systems V2: Bundle First"
);

console.log(
    " Heavy Systems: Idle Loading"
);

console.log(
    " Heavy Systems: Failure Safe"
);
```

---

Generated by MiniGram MD Intelligence V6.
