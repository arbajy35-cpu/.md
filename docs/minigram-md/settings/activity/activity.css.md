# settings/activity/activity.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `settings/activity/activity.css` |
| Extension | `.css` |
| Bytes | 4141 |
| Lines | 254 |
| SHA-256 | `43d309a291771c812598758d9aa5cda6215a5123732ecd2d26f408cd272df099` |
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
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `settings/activity/activity.html`

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

`/storage/emulated/0/MINIGRAM1/settings/activity/activity.css`

It is NOT AI generated or rewritten.

```css
/* ===== RESET ===== */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
}

:root{
  --bg:#000;
  --card:rgba(255,255,255,0.04);
  --border:rgba(255,255,255,0.06);
  --text:#fff;
  --muted:rgba(255,255,255,0.5);
  --soft:rgba(255,255,255,0.08);
}

body{
  background:var(--bg);
  color:var(--text);
  -webkit-font-smoothing:antialiased;
  overflow-x:hidden;
}

/* ===== CONTAINER ===== */
.container{
  max-width:500px;
  margin:auto;
}

/* ===== HEADER ===== */
.header{
  display:flex;
  align-items:center;
  gap:12px;
  padding:14px 16px;
  border-bottom:1px solid var(--border);
  backdrop-filter:blur(10px);
  position:sticky;
  top:0;
  background:rgba(0,0,0,0.7);
  z-index:10;
}

.header h1{
  font-size:17px;
  font-weight:600;
  letter-spacing:-0.2px;
}

/* ===== BACK BUTTON ===== */
.back{
  width:34px;
  height:34px;
  display:flex;
  align-items:center;
  justify-content:center;
  border-radius:50%;
  border:none;
  background:transparent;
  cursor:pointer;
  transition:0.2s ease;
}

.back svg{
  width:20px;
  height:20px;
}

.back:hover{
  background:var(--card);
}

.back:active{
  transform:scale(0.92);
  background:var(--soft);
}

/* ===== HERO ===== */
.hero{
  padding:28px 16px 20px;
}

.hero h2{
  font-size:22px;
  font-weight:700;
  line-height:1.3;
  letter-spacing:-0.3px;
  margin-bottom:8px;
}

.hero p{
  font-size:14px;
  color:var(--muted);
  line-height:1.5;
  max-width:90%;
}

/* ===== SECTION ===== */
.section{
  margin-top:18px;
}

.section h3{
  font-size:12.5px;
  font-weight:500;
  color:rgba(255,255,255,0.45);
  padding:0 16px 8px;
  letter-spacing:0.4px;
  text-transform:uppercase;
}

/* ===== ITEM ===== */
.item{
  display:flex;
  align-items:center;
  gap:12px;
  padding:14px 16px;
  border-top:1px solid rgba(255,255,255,0.04);
  cursor:pointer;
  position:relative;
  overflow:hidden;
  transition:background 0.15s ease, transform 0.1s ease;
}

.item:first-of-type{
  border-top:none;
}

/* glass hover feel */
.item:hover{
  background:rgba(255,255,255,0.035);
}

.item:active{
  transform:scale(0.98);
  background:rgba(255,255,255,0.07);
}

/* ===== LEFT ICON ===== */
.left{
  width:36px;
  height:36px;
  border-radius:50%;
  background:linear-gradient(
    180deg,
    rgba(255,255,255,0.06),
    rgba(255,255,255,0.02)
  );
  display:flex;
  align-items:center;
  justify-content:center;
  flex-shrink:0;
  transition:all 0.25s ease;
}

/* hover glow */
.item:hover .left{
  background:rgba(255,255,255,0.08);
  transform:scale(1.05);
}

/* ===== SVG ===== */
.left svg{
  width:18px;
  height:18px;
  stroke:#fff;
  opacity:0.95;
}

/* ===== TEXT ===== */
.item p{
  flex:1;
  font-size:15px;
  font-weight:500;
  letter-spacing:-0.1px;
}

/* ===== ARROW ===== */
.arrow{
  width:18px;
  height:18px;
  stroke:rgba(255,255,255,0.4);
  transition:all 0.2s ease;
}

.item:hover .arrow{
  transform:translateX(4px);
  stroke:rgba(255,255,255,0.75);
}

/* ===== RIPPLE EFFECT ===== */
.item::after{
  content:"";
  position:absolute;
  width:0;
  height:0;
  background:rgba(255,255,255,0.08);
  border-radius:50%;
  top:50%;
  left:50%;
  transform:translate(-50%, -50%);
  opacity:0;
  transition:0.4s;
}

.item:active::after{
  width:200px;
  height:200px;
  opacity:1;
  transition:0s;
}

/* ===== MICRO POLISH ===== */
.item,
.back{
  -webkit-tap-highlight-color:transparent;
}

/* smooth page entry */
body{
  animation:fadeIn 0.3s ease;
}

@keyframes fadeIn{
  from{
    opacity:0;
    transform:translateY(6px);
  }
  to{
    opacity:1;
    transform:translateY(0);
  }
}

/* subtle separators spacing */
.section + .section{
  margin-top:22px;
}

/* ===== SMALL DEVICES ===== */
@media(max-width:400px){
  .hero h2{
    font-size:20px;
  }

  .hero{
    padding:24px 14px 18px;
  }

  .item{
    padding:13px 14px;
  }
}
```

---

Generated by MiniGram MD Intelligence V6.
