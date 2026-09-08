# share/share.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `share/share.css` |
| Extension | `.css` |
| Bytes | 4619 |
| Lines | 249 |
| SHA-256 | `fedbc7025083dd36ec4f4cc47422cdc3a8de956a3dd315f8452455c48aec5253` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`share`

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

`/storage/emulated/0/MINIGRAM1/share/share.css`

It is NOT AI generated or rewritten.

```css
/* ============================= */
/* 🔒 ROOT */
/* ============================= */
#shareSheet {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.55);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s ease;
  z-index: 999;
}

#shareSheet.active {
  opacity: 1;
  pointer-events: auto;
}

/* ============================= */
/* 📦 SHEET */
/* ============================= */
#shareSheet .shareContent {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 68vh; /* 👈 default half */
  max-height: 94vh;
  background: #0c0c0c;
  border-radius: 30px 30px 0 0;
  padding: 10px 12px;
  transform: translateY(100%);
  transition: 
    transform 0.35s cubic-bezier(0.22,1,0.36,1),
    height 0.25s ease;
  display: flex;
  flex-direction: column;
}

#shareSheet.active .shareContent {
  transform: translateY(0);
}

/* 🔥 FULL MODE */
#shareSheet.full .shareContent {
  height: 94vh;
}

/* ============================= */
/* 🧲 DRAG */
/* ============================= */
#shareSheet .dragBar {
  width: 36px;
  height: 4px;
  background: #3a3a3a;
  border-radius: 20px;
  margin: 6px auto 10px;
}

/* ============================= */
/* 💬 INPUT */
/* ============================= */
#shareSheet .shareMsg {
  width: 100%;
  padding: 11px 14px;
  border-radius: 12px;
  border: none;
  background: #151515;
  color: #fff;
  font-size: 14px;
  margin-bottom: 8px;
}

/* ============================= */
/* 🔍 SEARCH */
/* ============================= */
#shareSheet .searchBox {
  display: flex;
  align-items: center;
  background: #151515;
  border-radius: 12px;
  padding: 9px 12px;
  margin-bottom: 10px;
}

#shareSheet .searchBox input {
  background: none;
  border: none;
  color: #fff;
  outline: none;
  margin-left: 8px;
  width: 100%;
  font-size: 14px;
}

#shareSheet .searchIcon {
  color: #777;
}

/* ============================= */
/* 📸 STORY */
/* ============================= */
#shareSheet .storyBox {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 4px;
  margin-bottom: 8px;
  border-bottom: 1px solid #1a1a1a;
}

#shareSheet .storyAvatar {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  overflow: hidden;
  position: relative;
}

#shareSheet .storyAvatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#shareSheet .plus {
  position: absolute;
  bottom: -2px;
  right: -2px;
  background: #0095f6;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  font-size: 11px;
  display: flex;
  align-items: center;
  justify-content: center;
}

#shareSheet .storyText {
  color: #0095f6;
  font-weight: 500;
  font-size: 14px;
}

#shareSheet .arrow {
  margin-left: auto;
  color: #666;
}

/* ============================= */
/* 📜 LIST */
/* ============================= */
#shareSheet #shareList {
  flex: 1;
  overflow-y: auto;
  padding-top: 4px;
  scroll-behavior: smooth;
}

/* hide scrollbar */
#shareSheet #shareList::-webkit-scrollbar {
  display: none;
}

/* ============================= */
/* 👤 USER */
/* ============================= */
#shareSheet .shareUser {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 6px;
  border-radius: 12px;
}

#shareSheet .shareUser:active {
  background: #141414;
}

/* LEFT */
#shareSheet .left {
  display: flex;
  align-items: center;
}

#shareSheet .avatar {
  width: 44px;
  height: 44px;
  border-radius: 50%;
}

#shareSheet .avatarWrap {
  position: relative;
}

#shareSheet .online {
  position: absolute;
  bottom: 3px;
  right: 3px;
  width: 8px;
  height: 8px;
  background: #00ff6a;
  border-radius: 50%;
  border: 2px solid #000;
}

/* TEXT */
#shareSheet .userInfo {
  margin-left: 10px;
}

#shareSheet .name {
  font-size: 13.5px;
  font-weight: 500;
  color: #fff;
}

#shareSheet .username {
  font-size: 11.5px;
  color: #777;
}

/* ============================= */
/* 🚀 BUTTON */
/* ============================= */
#shareSheet .sendBtn {
  background: #0095f6;
  border: none;
  padding: 6px 14px;
  border-radius: 8px;
  color: white;
  font-size: 12.5px;
  font-weight: 500;
}

#shareSheet .sendBtn:active {
  transform: scale(0.93);
}

#shareSheet .sendBtn.sent {
  background: #222;
}

/* ============================= */
/* ✨ FINAL TOUCH */
/* ============================= */
#shareSheet * {
  -webkit-tap-highlight-color: transparent;
}
```

---

Generated by MiniGram MD Intelligence V6.
