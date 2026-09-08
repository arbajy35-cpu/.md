# profile/profile.html

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `profile/profile.html` |
| Extension | `.html` |
| Bytes | 3831 |
| Lines | 133 |
| SHA-256 | `630a2bd36339074d14d411547b8e2b9e051c1e09667163a31b1a17a1e86925b7` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`profile`

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

`/storage/emulated/0/MINIGRAM1/profile/profile.html`

It is NOT AI generated or rewritten.

```html
<!-- ================= PROFILE PAGE WRAPPER ================= -->
<div class="profilePage">

  <!-- 🔥 UPGRADED PROFILE APPBAR -->
  <div class="appbar blank profileAppbar">

    <!-- LEFT -->
    <div class="left">
      <span class="usernameTop" id="usernameTop">
  Loading...
</span>

      <!-- dropdown -->
      <button class="iconBtn small">
        <svg viewBox="0 0 24 24" fill="none">
          <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>

      <span class="dot"></span>
    </div>

    <!-- RIGHT -->
    <div class="right">

      <!-- add -->
      <button class="iconBtn">
        <svg viewBox="0 0 24 24" fill="none">
          <rect x="3" y="3" width="18" height="18" rx="5" stroke="currentColor" stroke-width="2"/>
          <path d="M12 8V16M8 12H16" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </button>

      <!-- send -->
      <button class="iconBtn">
        <svg viewBox="0 0 24 24" fill="none">
          <path d="M22 2L11 13" stroke="currentColor" stroke-width="2"/>
          <path d="M22 2L15 22L11 13L2 9L22 2Z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/>
        </svg>
      </button>

      <!-- menu (OPEN SETTINGS) -->
<button class="iconBtn" onclick="openSettings()">
  <svg viewBox="0 0 24 24" fill="none">
    <path d="M4 6H20M4 12H20M4 18H20" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
  </svg>
</button>

    </div>

  </div>

  <!-- ================= PROFILE MODULE ================= -->
  <div class="profile">

    <!-- ===== HEADER ===== -->
    <div class="profile-header">

      <!-- AVATAR -->
      <div class="avatar" id="profilePic"></div>

      <!-- STATS -->
      <div class="stats">
        <div>
          <b id="posts">0</b>
          <span>posts</span>
        </div>
        <div>
          <b id="followers">0</b>
          <span>followers</span>
        </div>
        <div>
          <b id="following">0</b>
          <span>following</span>
        </div>
      </div>

    </div>

    <!-- ===== USER INFO ===== -->
    <div class="info">
      <div class="username" id="username"></div>
<div class="name" id="name"></div>
<div class="bio-text" id="bioText"></div>
    </div>

    <!-- ===== ACTION BUTTONS ===== -->
    <div class="actions">
     <button class="edit-btn actionBtn">
  <span>Edit Profile</span>
</button>

<button class="share-btn actionBtn">
  <span>Share</span>
</button>

<button class="icon-btn actionBtn">
  <i class="fa-solid fa-user-plus"></i>
</button>
    </div>

    <!-- ===== TABS ===== -->
    <div class="tabs">
      <i class="fa-solid fa-table-cells active" title="Posts"></i>
      <i class="fa-solid fa-clapperboard" title="Videos"></i>
      <i class="fa-regular fa-user" title="User Info"></i>
    </div>

    <!-- ===== POSTS GRID ===== -->
    <div class="posts" id="postsGrid">
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
    </div>

    <!-- ===== VIDEOS GRID ===== -->
    <div class="posts" id="videosGrid" style="display:none;">
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
      <div class="profileSkeleton"></div>
    </div>

    <!-- ===== USER TAB ===== -->
    <div id="userTab" style="display:none; padding:16px; color:#d0d0d0;">
      <p>Here you can show additional profile details, highlights, or other user info.</p>
    </div>

  </div>

</div>
```

---

Generated by MiniGram MD Intelligence V6.
