# login/login.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `login/login.js` |
| Extension | `.js` |
| Size | 2990 bytes |
| Lines | 222 |
| SHA-256 | `f24d9f905a5587e17cf7443a6139cb0fefc6af2185070992e8d83ebd439a892e` |

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
login/login.js
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

`/storage/emulated/0/MINIGRAM1/login/login.js`

No AI rewriting was performed on the source code.

```javascript
// ---------------- PASSWORD TOGGLE ----------------

const toggle = document.getElementById("togglePassword");
const pass = document.getElementById("password");

if (toggle && pass) {

toggle.addEventListener("click", () => {

pass.type =
  pass.type === "password"
  ? "text"
  : "password";

toggle
  .querySelector("i")
  ?.classList.toggle("fa-eye");

toggle
  .querySelector("i")
  ?.classList.toggle("fa-eye-slash");

});

}

// ---------------- DEBUG ----------------

alert(
"window.supabaseClient = " +
typeof window.supabaseClient
);

alert(
"window.supabase = " +
typeof window.supabase
);

// ---------------- LOGIN ----------------

const loginBtn =
document.getElementById("loginBtn");

loginBtn?.addEventListener(
"click",
async () => {

try {

  alert("Login Started");

  const client =
    window.supabaseClient;

  alert(
    "CLIENT: " +
    typeof client
  );

  alert(
    "AUTH: " +
    typeof client?.auth
  );

  if (!client) {

    alert(
      "Supabase Client Missing"
    );

    return;

  }

  const email =
    document
    .getElementById("username")
    .value
    .trim();

  const password =
    document
    .getElementById("password")
    .value
    .trim();

  if (!email || !password) {

    alert(
      "Please enter email and password"
    );

    return;

  }

  loginBtn.disabled = true;
  loginBtn.textContent =
    "Logging In...";

  alert("Before Supabase");

  const {
    data,
    error
  } =
  await client.auth.signInWithPassword({

    email,
    password

  });

  alert("After Supabase");

  if (error) {

    alert(
      "LOGIN ERROR:\n" +
      error.message
    );

    loginBtn.disabled = false;
    loginBtn.textContent = "Login";

    return;

  }

  alert(
    "Welcome " +
    data.user.email
  );

  window.location.href =
    "../index.html";

} catch (err) {

  alert(
    "CRASH:\n" +
    err.message
  );

  console.error(err);

  loginBtn.disabled = false;
  loginBtn.textContent = "Login";

}

}
);

// ---------------- ENTER KEY ----------------

document.addEventListener(
"keydown",
(e) => {

if (e.key === "Enter") {

  e.preventDefault();

  loginBtn?.click();

}

}
);

// ---------------- RIPPLE EFFECT ----------------

document.addEventListener(
"click",
function(e){

const rippleLayer =
  document.querySelector(
    ".ripple-layer"
  );

if(!rippleLayer) return;

const ripple =
  document.createElement("span");

ripple.className =
  "ripple";

ripple.style.left =
  e.clientX + "px";

ripple.style.top =
  e.clientY + "px";

rippleLayer.appendChild(
  ripple
);

setTimeout(
  () => ripple.remove(),
  1000
);

}
);

// ---------------- ERROR LOGGER ----------------

window.addEventListener?.(
"error",
e => {

console.log(
  " ERROR IN FILE:",
  e.filename,
  e.message
);

}
);
```

---

Generated automatically.
