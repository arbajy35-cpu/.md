# main_js/boot/auth.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/boot/auth.js` |
| Extension | `.js` |
| Size | 2431 bytes |
| Lines | 124 |
| SHA-256 | `83a46e91bbab1768cac4c7d5abcdb2889aae62b82410e7c4a0fe51800d5b11c2` |

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
main_js/boot/auth.js
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

`/storage/emulated/0/MINIGRAM1/main_js/boot/auth.js`

No AI rewriting was performed on the source code.

```javascript
//////////////////////////////////////////////////
// 🔐 MINIGRAM AUTH
//////////////////////////////////////////////////

async function checkAuth(){

    const client =
        window.supabaseClient ||
        window.db;


    //////////////////////////////////////////////////
    // CLIENT CHECK
    //////////////////////////////////////////////////

    if(!client){

        console.error(
            "❌ SUPABASE CLIENT NOT FOUND"
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }


    //////////////////////////////////////////////////
    // AUTH API CHECK
    //////////////////////////////////////////////////

    if(
        !client.auth ||
        typeof client.auth.getSession !==
        "function"
    ){

        console.error(
            "❌ SUPABASE AUTH API NOT AVAILABLE"
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }


    //////////////////////////////////////////////////
    // SESSION
    //////////////////////////////////////////////////

    try{

        const {
            data,
            error
        } =
            await client.auth.getSession();


        //////////////////////////////////////////////////
        // ERROR
        //////////////////////////////////////////////////

        if(error){

            console.error(
                "❌ AUTH SESSION ERROR:",
                error
            );

            window.location.replace(
                "signup/signup.html"
            );

            return false;

        }


        //////////////////////////////////////////////////
        // NO SESSION
        //////////////////////////////////////////////////

        if(!data?.session){

            window.location.replace(
                "login/login.html"
            );

            return false;

        }


        //////////////////////////////////////////////////
        // AUTHENTICATED
        //////////////////////////////////////////////////

        return true;


    }catch(e){

        console.error(
            "🔥 AUTH CHECK FAILED:",
            e
        );

        window.location.replace(
            "signup/signup.html"
        );

        return false;

    }

}
```

---

Generated automatically.
