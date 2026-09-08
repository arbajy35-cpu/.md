# settings/accounts/accounts.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `settings/accounts/accounts.css` |
| Extension | `.css` |
| Bytes | 3786 |
| Lines | 245 |
| SHA-256 | `ee06c2fdaf716146b72819c5bf6c6da046656bbdc906b7371efbfe60856901cc` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`settings`

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

- None

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

`/storage/emulated/0/MINIGRAM1/settings/accounts/accounts.css`

It is NOT AI generated or rewritten.

```css
/* RESET */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

body{
  background:#050505;
  color:#fff;
}

/* PAGE */
.accountsPage{
  padding-bottom:50px;
}

/* ================= HEADER ================= */
.accountsHeader{
  height:64px;
  display:flex;
  align-items:center;
  justify-content:space-between;

  padding:0 16px;

  position:sticky;
  top:0;
  z-index:100;

  background:linear-gradient(to bottom, rgba(0,0,0,0.95), rgba(0,0,0,0.6));
  backdrop-filter:blur(20px);

  border-bottom:1px solid rgba(255,255,255,0.08);
}

/* CLOSE BUTTON */
.closeBtn{
  width:42px;
  height:42px;

  border:none;
  border-radius:50%;

  background:rgba(255,255,255,0.08);

  display:flex;
  align-items:center;
  justify-content:center;

  transition:0.25s;
}

.closeBtn svg{
  width:20px;
  height:20px;
  stroke:#fff;
}

.closeBtn:active{
  transform:scale(0.8);
  background:rgba(255,255,255,0.2);
}

/* LOGO */
.metaLogo{
  font-weight:700;
  font-size:16px;
  letter-spacing:1px;

  background:linear-gradient(90deg,#fff,#aaa);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

/* ================= TOP ================= */
.accountsTop{
  padding:26px 18px 12px;
}

.accountsTop h1{
  font-size:28px;
  font-weight:800;
  letter-spacing:-0.5px;
}

.accountsTop p{
  margin-top:6px;
  font-size:14px;
  color:#9a9a9a;
  line-height:1.5;
}

/* ================= CARD ================= */
.card{
  margin:14px 12px;
  border-radius:20px;

  background:linear-gradient(
    145deg,
    rgba(30,30,30,0.9),
    rgba(15,15,15,0.9)
  );

  border:1px solid rgba(255,255,255,0.05);

  overflow:hidden;

  /* 🔥 DEPTH + GLOW */
  box-shadow:
    0 10px 30px rgba(0,0,0,0.8),
    inset 0 1px rgba(255,255,255,0.05);
}

/* ================= PROFILE ================= */
.profileCard{
  display:flex;
  justify-content:space-between;
  align-items:center;

  padding:18px;

  transition:0.25s;
}

.profileCard:active{
  transform:scale(0.97);
  background:rgba(255,255,255,0.05);
}

.profileLeft{
  display:flex;
  align-items:center;
  gap:14px;
}

/* AVATAR STACK */
.avatars{
  display:flex;
}

.avatars img{
  width:44px;
  height:44px;

  border-radius:50%;
  border:2px solid #050505;

  margin-left:-12px;

  object-fit:cover;

  transition:0.3s;
}

.avatars img:hover{
  transform:scale(1.1);
}

.avatars img:first-child{
  margin-left:0;
}

/* TEXT */
.title{
  font-size:15px;
  font-weight:600;
}

.sub{
  font-size:12px;
  color:#8e8e93;
  margin-top:3px;
}

/* ================= ITEMS ================= */
.item{
  display:flex;
  justify-content:space-between;
  align-items:center;

  padding:16px 18px;

  font-size:15px;

  position:relative;

  transition:0.25s;
}

/* DIVIDER */
.item::after{
  content:"";
  position:absolute;
  bottom:0;
  left:18px;
  right:0;
  height:1px;

  background:rgba(255,255,255,0.06);
}

.item:last-child::after{
  display:none;
}

/* 🔥 HOVER GLOW */
.item:hover{
  background:rgba(255,255,255,0.03);
}

/* PRESS */
.item:active{
  transform:scale(0.96);
  background:rgba(255,255,255,0.08);
}

/* ================= ARROW ================= */
.arrowIcon{
  width:18px;
  height:18px;

  stroke:#aaa;
  fill:none;
  stroke-width:2;

  transition:0.25s;
}

.item:active .arrowIcon,
.profileCard:active .arrowIcon{
  transform:translateX(6px);
}

/* ================= EXTRA ================= */
html{
  scroll-behavior:smooth;
}

.item,
.profileCard,
.closeBtn{
  will-change:transform;
}
```

---

Generated by MiniGram MD Intelligence V6.
