# main_js/comments.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `main_js/comments.js` |
| Extension | `.js` |
| Size | 523 bytes |
| Lines | 38 |
| SHA-256 | `48a0847f2482ee53828cee944f9c98a8160a19e1738e971d3d75d146cf8536aa` |

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
main_js/comments.js
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

`/storage/emulated/0/MINIGRAM1/main_js/comments.js`

No AI rewriting was performed on the source code.

```javascript
window.commentPost = function(postId){

  const commentsEl =

    document.getElementById(
      "comments-" + postId
    );

  if(!commentsEl) return;

  let count =

    parseInt(
      commentsEl.dataset.comments || "0"
    ) || 0;

  count++;

  commentsEl.dataset.comments =
    count;

  commentsEl.textContent =
    count + " comments";

  const post =

    window.STATE?.FEED?.find(
      p => p.id === postId
    );

  if(post){

    post.comments_count =
      count;

  }

};
```

---

Generated automatically.
