# home/home.html

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `home/home.html` |
| Extension | `.html` |
| Size | 3457 bytes |
| Lines | 186 |
| SHA-256 | `1d8f66c46ce4a76a45179cba6cbb570bcd7c89d412ddcff7d27f8d6d9af996e4` |

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
home/home.html
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

`/storage/emulated/0/MINIGRAM1/home/home.html`

No AI rewriting was performed on the source code.

```html
<!-- ================================================= -->
<!--  HOME ROOT -->
<!-- ================================================= -->

<div id="homeRoot">

  <!-- ================= STORIES ================= -->

  <div class="storiesSection">

    <div
      id="storiesWrapper"
      class="storiesWrapper">
    </div>

  </div>

  <!-- ================= FEED ================= -->

  <div
    id="feed"
    class="feed">
  </div>

  <!-- ADD THIS -->
  <div id="scrollAnchor"></div>

</div>

<!-- ================================================= -->
<!--  POST TEMPLATE -->
<!-- ================================================= -->

<template id="postTemplate">

  <div class="post">

    <!-- ================= HEADER ================= -->

    <div class="postHeader">

      <div class="postHeaderLeft">

        <img
          class="avatar"
          loading="lazy"
          alt="avatar">

        <div class="username"></div>

      </div>

      <button class="glassBtn small">

        <svg
          viewBox="0 0 24 24"
          width="20"
          height="20"
          fill="none">

          <circle cx="5" cy="12" r="1.5"></circle>
          <circle cx="12" cy="12" r="1.5"></circle>
          <circle cx="19" cy="12" r="1.5"></circle>

        </svg>

      </button>

    </div>


    <!-- ================= IMAGE ================= -->

    <div class="postImageContainer">

      <img
        class="postImage"
        loading="lazy"
        alt="post">

      <div class="heartPop"></div>

    </div>


    <!-- ================= ACTIONS ================= -->

   <div class="postActions">

  <div class="postActionsLeft">

    <button
      class="glassBtn like likeBtn">
    </button>

    <button
      class="glassBtn comment commentBtn">
    </button>

    <button
      class="glassBtn share shareBtn">
    </button>

  </div>

  <button
    class="glassBtn save saveBtn">
  </button>

</div>


    <!-- ================= META ================= -->

    <div class="postLikes"></div>
    
    <div class="postComments"></div> 
    
    <div class="postCaption">

      <b class="captionUser"></b>

      <span class="captionText"></span>

    </div>

    <div class="postTime"></div>

  </div>

</template>


<!-- ================================================= -->
<!--  COMMENT ROOT -->
<!-- ================================================= -->

<div id="commentSheet"></div>


<!-- ================================================= -->
<!--  SHARE ROOT -->
<!-- ================================================= -->

<div id="shareSheet"></div>


<!-- ================================================= -->
<!--  CONNECT BUTTONS -->
<!-- ================================================= -->

<script>

document.addEventListener("click", (e) => {

  //////////////////////////////////////////////////
  //  COMMENT
  //////////////////////////////////////////////////

  if (e.target.closest(".commentBtn")) {

    if (window.openComments) {

      window.openComments();

    }

  }

  //////////////////////////////////////////////////
  //  SHARE
  //////////////////////////////////////////////////

  if (e.target.closest(".shareBtn")) {

    if (window.openShare) {

      window.openShare();

    }

  }

});

</script>
```

---

Generated automatically.
