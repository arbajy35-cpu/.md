# Games/carrom/carrom_mode/med.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/med.css` |
| Extension | `.css` |
| Bytes | 4660 |
| Lines | 252 |
| SHA-256 | `21b2b0d928b40ff2cf5bf3291cb759668cdcab6044b1edb902b2aa743bd4d29c` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`Games`

The local intelligence engine detected
0 direct dependencies
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `Games/carrom/carrom_mode/med.html`

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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.css`

It is NOT AI generated or rewritten.

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
  min-height: 100vh;
  color: #fff;
  overflow-x: hidden;
}

.game-mode-container {
  max-width: 450px;
  margin: 0 auto;
  padding: 20px;
  min-height: 100vh;
}

/* Header */
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 30px;
  animation: slideDown 0.6s ease-out;
}

.header h2 {
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 2px;
  color: #facc15;
}

.icon-btn {
  width: 45px;
  height: 45px;
  border-radius: 12px;
  background: rgba(255,255,255,0.1);
  border: none;
  color: #fff;
  font-size: 24px;
  cursor: pointer;
  backdrop-filter: blur(10px);
  transition: all 0.3s;
}

.icon-btn:active {
  transform: scale(0.9);
  background: rgba(255,255,255,0.2);
}

/* Profile Card */
.profile-card {
  display: flex;
  align-items: center;
  gap: 10px;
  background: rgba(255,255,255,0.1);
  padding: 8px 12px;
  border-radius: 15px;
  backdrop-filter: blur(10px);
  cursor: pointer;
  transition: all 0.3s;
}

.profile-card:active {
  transform: scale(0.95);
  background: rgba(255,255,255,0.15);
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #facc15;
}

.profile-info {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.username {
  font-size: 12px;
  font-weight: 600;
  color: #fff;
}

.coins {
  font-size: 11px;
  color: #facc15;
}

/* Mode Cards */
.modes-grid {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 30px;
  animation: slideUp 0.6s ease-out 0.2s both;
}

.mode-card {
  background: linear-gradient(135deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
  border: 2px solid rgba(255,255,255,0.1);
  border-radius: 20px;
  padding: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
}

.mode-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
  transition: left 0.5s;
}

.mode-card:active::before {
  left: 100%;
}

.mode-card:active {
  transform: scale(0.98);
  border-color: #facc15;
}

.freestyle {
  background: linear-gradient(135deg, rgba(34,197,94,0.2), rgba(16,185,129,0.1));
  border-color: rgba(34,197,94,0.3);
}

.classic {
  background: linear-gradient(135deg, rgba(59,130,246,0.2), rgba(37,99,235,0.1));
  border-color: rgba(59,130,246,0.3);
}

.tournament {
  background: linear-gradient(135deg, rgba(245,158,11,0.2), rgba(217,119,6,0.1));
  border-color: rgba(245,158,11,0.3);
}

.mode-icon {
  font-size: 48px;
  margin-bottom: 12px;
}

.mode-card h3 {
  font-size: 22px;
  font-weight: 800;
  margin-bottom: 8px;
  letter-spacing: 1px;
}

.mode-card p {
  font-size: 13px;
  color: rgba(255,255,255,0.7);
  line-height: 1.5;
}

.mode-badge {
  position: absolute;
  top: 20px;
  right: 20px;
  background: #facc15;
  color: #1e293b;
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
}

.tournament .mode-badge {
  background: linear-gradient(135deg, #f59e0b, #d97706);
}

/* Stats Bar */
.stats-bar {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
  animation: fadeIn 0.8s ease-out 0.4s both;
}

.stat-item {
  background: rgba(255,255,255,0.08);
  border-radius: 15px;
  padding: 18px 10px;
  text-align: center;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.1);
}

.stat-value {
  display: block;
  font-size: 24px;
  font-weight: 800;
  color: #facc15;
  margin-bottom: 5px;
}

.stat-label {
  font-size: 11px;
  color: rgba(255,255,255,0.6);
  letter-spacing: 1px;
}

/* Animations */
@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@media (max-width: 380px) {
  .mode-card h3 { font-size: 20px; }
  .mode-icon { font-size: 40px; }
}
```

---

Generated by MiniGram MD Intelligence V6.
