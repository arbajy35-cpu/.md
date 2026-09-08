# login/login.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `login/login.html` |
| Extension | `.html` |
| Size | 1234 bytes |
| Lines | 40 |
| SHA-256 | `93e7c3085396a075dc97013a685ba25106020cd1346d3dcce3912419dcff884e` |

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
login/login.html
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

`/storage/emulated/0/MINIGRAM1/login/login.html`

No AI rewriting was performed on the source code.

```html
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MiniGram Login</title>
<link rel="stylesheet" href="login.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
</head>
<body>

<div class="ripple-layer"></div>

<div class="login-container">
  <h1 class="logo">MiniGram</h1>

  <input type="text" id="username" placeholder="Phone number, email or username">

  <div class="password-box">
    <input type="password" id="password" placeholder="Password">
    <span id="togglePassword"><i class="fa-solid fa-eye-slash"></i></span>
  </div>

  <button id="loginBtn">Log in</button>

  <p class="forgot">Forgot your login details? Get help signing in.</p>

  <div class="or"><span></span><p>OR</p><span></span></div>

  <p class="signup">
    Don't have an account?
    <a href="/storage/emulated/0/MINIGRAM1/sighup/signup.html"><b>Sign up</b></a>
  </p>
</div>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2/dist/umd/supabase.min.js"></script>
<script src="../supabase.js"></script>
<script src="login.js"></script>
</body>
</html>
```

---

Generated automatically.
