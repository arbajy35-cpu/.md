# main_js/boot/skeleton.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/skeleton.js` |
| Extension | `.js` |
| Size | 2024 bytes |
| Lines | 99 |
| SHA-256 | `f43c4c33d9c06e459ca8430b0823038a0ce18f125081893f5898ca2ba82113f0` |

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
main_js/boot/skeleton.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/skeleton.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// ⚡ MINIGRAM INSTANT SKELETON
//////////////////////////////////////////////////

function initInstantSkeleton(){

    //////////////////////////////////////////////////
    // NEVER RECREATE
    //////////////////////////////////////////////////

    if(
        window.__INSTANT_SKELETON__
    ){

        return;

    }


    const main =
        document.getElementById(
            "mainContent"
        );


    if(!main){

        return;

    }


    //////////////////////////////////////////////////
    // STATE
    //////////////////////////////////////////////////

    window.__INSTANT_SKELETON__ =
        true;

    window.__INSTANT_SKELETON_ACTIVE__ =
        true;


    //////////////////////////////////////////////////
    // ONLY IF EMPTY
    //////////////////////////////////////////////////

    if(
        main.childElementCount === 0
    ){

        main.innerHTML = `

            <div
                id="instantSkeleton"
                class="instant-skeleton"
                aria-hidden="true"
            >

                <div class="skel-stories">

                    ${Array.from(
                        {length:5},
                        () => `
                            <div class="skel-story"></div>
                        `
                    ).join("")}

                </div>


                ${Array.from(
                    {length:2},
                    () => `

                        <div class="skel-post">

                            <div class="skel-user">

                                <div class="skel-avatar"></div>

                                <div class="skel-name"></div>

                            </div>

                            <div class="skel-media"></div>

                        </div>

                    `
                ).join("")}

            </div>

        `;

    }

}
```

---

Generated automatically.
