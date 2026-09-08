# auth.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `auth.js` |
| Extension | `.js` |
| Size | 950 bytes |
| Lines | 56 |
| SHA-256 | `6a242e00d9fabc8b42632a3aa778ff6fc8c553250567ebc953880f2218dc264d` |

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
auth.js
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

`/storage/emulated/0/MINIGRAM1/auth.js`

No AI rewriting was performed on the source code.

```javascript
// ================= AUTH CHECK =================

function checkAuth(){

let user = localStorage.getItem("minigram_user")

if(!user){

// show login page
loadPage("login.html")

// hide home feed
document.getElementById("homeSection").style.display = "none"

}

else{

showHome()

}

}


// ================= LOGIN SUCCESS =================

function loginSuccess(username){

localStorage.setItem("minigram_user", username)

document.getElementById("appContent").innerHTML = ""

showHome()

}


// ================= LOGOUT =================

function logout(){

localStorage.removeItem("minigram_user")

loadPage("login.html")

}


// ================= MAKE GLOBAL =================

window.loginSuccess = loginSuccess
window.logout = logout
window.checkAuth = checkAuth
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated automatically.
