# global_css/layout.css

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `global_css/layout.css` |
| Extension | `.css` |
| Size | 2432 bytes |
| Lines | 120 |
| SHA-256 | `773d6b5c7bf77dcf7e43ad909695da5633c4797203a1aa6cc60fda8b594d5218` |

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
global_css/layout.css
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

`/storage/emulated/0/MINIGRAM1/global_css/layout.css`

No AI rewriting was performed on the source code.

```css
/* ================= ROOT SYSTEM ================= */
:root{
  --icon-size: 24px;

  --color-base: rgba(255,255,255,0.85);
  --color-dim: rgba(255,255,255,0.55);
  --color-active: #ffffff;

  --gap: 16px;
  --divider: rgba(255,255,255,0.08);
  --bg: rgba(0,0,0,0.92);

  --radius: 14px;
}

/* ================= APP BAR ================= */
.appbar {
  position: sticky;
  top: 0;
  z-index: 1000;

  display: flex;
  align-items: center;
  justify-content: space-between;

  height: 59px;
  min-height: 59px;
  max-height: 59px;
  box-sizing: border-box;
  flex: 0 1 auto;

  padding: 12px 16px;

  background: var(--bg);
  backdrop-filter: blur(18px);

  border-bottom: 1px solid var(--divider);
}

/* ================= TITLE ================= */
.title{
  font-family: var(--font-title);
  font-size: 20px;
  font-weight: 600;
  letter-spacing: 0.3px;
  color: var(--color-active);
}

/* ================= ICON CONTAINER ================= */
.appbarIcons{
  display: flex;
  align-items: center;
  gap: var(--gap);
}

/* ================= ICON BASE SYSTEM ================= */
.appbarIcons span,
.navIcon,
.material-symbols-outlined{
  font-size: var(--icon-size);
  display: flex;
  align-items: center;
  justify-content: center;

  color: var(--color-base);
  transition: 0.2s ease;
  cursor: pointer;
}

/* ================= TAP FEEDBACK ================= */
.appbarIcons span:active,
.navIcon:active{
  transform: scale(0.82);
  opacity: 0.6;
}

/* ================= BOTTOM NAV ================= */
.bottomNav{
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;

  height: 56px;

  background: var(--bg);
  backdrop-filter: blur(16px);

  border-top: 1px solid var(--divider);

  display: flex;
  justify-content: space-around;
  align-items: center;
}

/* ================= NAV ICON ================= */
.navIcon{
  color: var(--color-dim);
  transition: 0.2s ease;
}

/* ACTIVE STATE */
.navIcon.active{
  color: var(--color-active);
  transform: scale(1.15);
  text-shadow: 0 0 8px rgba(255,255,255,0.25);
}

/* ================= STORY ================= */
.story{
  border-radius: 50%;
  box-shadow:
    0 0 8px rgba(0,255,150,0.25),
    0 0 20px rgba(0,255,150,0.08);
}

/* ================= GLOBAL TAP FIX ================= */
button, span, .navIcon{
  -webkit-tap-highlight-color: transparent;
}
```

---

Generated automatically.
