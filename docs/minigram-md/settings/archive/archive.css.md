# settings/archive/archive.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `settings/archive/archive.css` |
| Extension | `.css` |
| Bytes | 4511 |
| Lines | 270 |
| SHA-256 | `56b16ec6ad6507c65c67340c3bc8d7a2454f03470b9bb79b3dc4e294e7fe323d` |
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

`/storage/emulated/0/MINIGRAM1/settings/archive/archive.css`

It is NOT AI generated or rewritten.

```css
:root {
  --bg: #000;
  --card: rgba(255,255,255,0.04);
  --border: rgba(255,255,255,0.08);
  --text: #fff;
  --muted: rgba(255,255,255,0.6);
  --accent: #0095f6;
}

/* ===== RESET ===== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

/* ===== CONTAINER ===== */
.container {
  max-width: 500px;
  margin: auto;
  padding-bottom: 50px;
}

/* ===== HEADER ===== */
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 16px;
  backdrop-filter: blur(12px);
  background: rgba(0,0,0,0.5);
  border-bottom: 1px solid var(--border);
  position: sticky;
  top: 0;
  z-index: 10;
}

.header h2 {
  font-size: 17px;
  font-weight: 600;
  letter-spacing: 0.5px;
}

.back, .menu {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  cursor: pointer;
  border-radius: 50%;
  transition: 0.2s;
}

.back:hover, .menu:hover {
  background: rgba(255,255,255,0.07);
  transform: scale(1.2);
}

.back svg, .menu svg {
  width: 24px;
  height: 24px;
  fill: var(--text);
}

/* ===== TABS ===== */
.tabs {
  display: flex;
  position: relative;
  border-bottom: 1px solid var(--border);
  margin-top: 8px;
}

.tab {
  flex: 1;
  text-align: center;
  padding: 12px 0;
  font-size: 14px;
  color: var(--muted);
  cursor: pointer;
  transition: color 0.3s, transform 0.2s;
  position: relative;
  font-weight: 500;
}

.tab:hover {
  transform: scale(1.05);
}

.tab.active {
  color: var(--text);
  font-weight: 600;
}

/* ===== SMOOTH INDICATOR ===== */
.tabs::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 50%;
  height: 2px;
  background: var(--accent);
  border-radius: 1px;
  transition: 0.3s ease;
}

.tabs.posts-active::after {
  left: 50%;
}

/* ===== CONTENT ===== */
.content {
  padding-top: 20px;
  animation: fadeIn 0.5s ease;
}

/* ===== EMPTY STATE ===== */
.empty {
  text-align: center;
  padding: 30px 20px;
  animation: fadeIn 0.5s ease;
}

.icon {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  background: var(--card);
  border: 1px solid var(--border);
  backdrop-filter: blur(12px);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: auto;
  font-size: 28px;
  color: var(--muted);
  box-shadow: 0 0 25px rgba(255,255,255,0.05);
  transition: transform 0.3s;
}

.icon:hover {
  transform: scale(1.1);
}

.empty h3 {
  margin-top: 18px;
  font-size: 18px;
  font-weight: 600;
  letter-spacing: 0.3px;
}

.empty p {
  color: var(--muted);
  font-size: 13px;
  margin-top: 10px;
  line-height: 1.4;
}

/* ===== TAB CONTENT ===== */
.tab-content {
  display: none;
}

.tab-content.active {
  display: block;
}

/* ===== ARCHIVE ITEMS ===== */
.archive-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 0 10px 20px 10px;
}

.archive-item {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 12px 16px;
  display: flex;
  flex-direction: column;
  backdrop-filter: blur(12px);
  transition: transform 0.2s, box-shadow 0.2s;
  cursor: pointer;
}

.archive-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0,0,0,0.5);
}

.archive-item-title {
  font-weight: 600;
  font-size: 15px;
  color: var(--text);
}

.archive-item-type {
  font-size: 12px;
  color: var(--muted);
  margin-top: 4px;
  text-transform: capitalize;
}

/* ===== ANIMATION ===== */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* ===== RESPONSIVE ===== */
@media (max-width: 480px) {
  .container {
    padding: 0 10px;
  }

  .header h2 {
    font-size: 16px;
  }

  .tab {
    font-size: 13px;
    padding: 10px 0;
  }

  .icon {
    width: 60px;
    height: 60px;
  }

  .icon svg {
    width: 32px;
    height: 32px;
  }

  .empty h3 {
    font-size: 16px;
  }

  .empty p {
    font-size: 12px;
  }

  .archive-item {
    padding: 10px 14px;
    border-radius: 10px;
  }

  .archive-item-title {
    font-size: 14px;
  }

  .archive-item-type {
    font-size: 11px;
  }
}
```

---

Generated by MiniGram MD Intelligence V6.
