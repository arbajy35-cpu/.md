# Games/carrom/carrom_home.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_home.css` |
| Extension | `.css` |
| Bytes | 4662 |
| Lines | 256 |
| SHA-256 | `b9b0263bf280e6df319bd1f2429502001507d0c13eddab2dec69e61f91ab7643` |
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

- `Games/carrom/carrom_home.html`

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

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_home.css`

It is NOT AI generated or rewritten.

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  overflow-x: hidden;
  width: 100%;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
  min-height: 100vh;
  min-height: 100dvh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 0;
}

.bg-coins {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(circle at 20% 30%, rgba(255,255,255,0.05) 0%, transparent 50%),
    radial-gradient(circle at 80% 70%, rgba(255,255,255,0.05) 0%, transparent 50%);
  z-index: 1;
  pointer-events: none;
}

.home-container {
  width: 100%;
  max-width: 400px;
  padding: 20px;
  position: relative;
  z-index: 2;
  margin: 0 auto;
}

.logo {
  text-align: center;
  margin-bottom: 50px;
  animation: slideDown 0.8s ease-out;
}

.striker-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, #ff6b35, #f7931e);
  border-radius: 50%;
  margin: 0 auto 20px;
  box-shadow: 0 10px 30px rgba(255, 107, 53, 0.4);
  position: relative;
  animation: bounce 2s infinite;
}

.striker-icon::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 50px;
  height: 50px;
  background: rgba(255,255,255,0.3);
  border-radius: 50%;
}

.logo h1 {
  font-size: 48px;
  font-weight: 800;
  color: #fff;
  letter-spacing: 2px;
  text-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.logo h1 span {
  color: #facc15;
}

.tagline {
  color: rgba(255,255,255,0.8);
  font-size: 14px;
  letter-spacing: 3px;
  margin-top: 5px;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 15px;
  animation: slideUp 0.8s ease-out 0.2s both;
  width: 100%;
}

button {
  border: none;
  border-radius: 15px;
  padding: 18px 30px;
  font-size: 16px;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
  width: 100%;
}

.btn-primary {
  background: linear-gradient(135deg, #ff6b35, #f7931e);
  color: white;
  font-size: 18px;
  padding: 20px 30px;
}

.btn-primary:active {
  transform: scale(0.95);
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}

.btn-secondary {
  background: rgba(255,255,255,0.15);
  color: white;
  backdrop-filter: blur(10px);
}

.btn-secondary:active {
  background: rgba(255,255,255,0.25);
  transform: scale(0.98);
}

.icon {
  font-size: 22px;
}

.modal {
  display: none;
  position: fixed;
  z-index: 100;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.7);
  backdrop-filter: blur(5px);
  animation: fadeIn 0.3s;
}

.modal-content {
  background: linear-gradient(135deg, #2a5298, #1e3c72);
  margin: 15% auto;
  padding: 30px;
  border-radius: 20px;
  width: 90%;
  max-width: 350px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  animation: slideUp 0.4s;
  position: relative;
}

.modal-content h2 {
  color: #facc15;
  margin-bottom: 20px;
  text-align: center;
}

.close {
  color: #fff;
  position: absolute;
  right: 20px;
  top: 15px;
  font-size: 32px;
  font-weight: bold;
  cursor: pointer;
}

.close:active {
  color: #facc15;
}

.rules {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.rule-item {
  background: rgba(255,255,255,0.1);
  padding: 12px;
  border-radius: 10px;
  color: #fff;
  font-size: 13px;
  line-height: 1.6;
}

.rule-item strong {
  color: #facc15;
}

.footer {
  text-align: center;
  margin-top: 40px;
  color: rgba(255,255,255,0.5);
  font-size: 12px;
  animation: fadeIn 1s ease-out 0.5s both;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-50px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(50px);
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

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@media (max-width: 380px) {
  .logo h1 { font-size: 40px; }
  button { padding: 16px 25px; font-size: 15px; }
  .home-container { padding: 15px; }
}
```

---

Generated by MiniGram MD Intelligence V6.
