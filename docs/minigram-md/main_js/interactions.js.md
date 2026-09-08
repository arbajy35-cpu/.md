# main_js/interactions.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `main_js/interactions.js` |
| Extension | `.js` |
| Bytes | 6983 |
| Lines | 386 |
| SHA-256 | `4d7be203deead3e83995fe57f2a2e20a4ecbc604c670d88c909fec07d09550fa` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`main_js`

The local intelligence engine detected
0 direct dependencies
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `CRITICAL_ERRORS_REPORT.md`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `animateHeart`
- `commentPost`
- `sharePost`
- `savePost`
- `openChat`
- `container`
- `heart`
- `commentsEl`
- `count`
- `likesEl`
- `key`
- `currentLikes`
- `alreadyLiked`
- `newLikes`
- `post`

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

`/storage/emulated/0/MINIGRAM1/main_js/interactions.js`

It is NOT AI generated or rewritten.

```javascript
// ================================
// HEART ANIMATION
// ================================

function animateHeart(img){

  const container = img.parentElement;

  const heart = document.createElement("div");

  heart.className = "heart";
  heart.innerText = "❤";

  container.appendChild(heart);

  setTimeout(()=>heart.remove(), 600);

}

// ================================
// COMMENT
// ================================

function commentPost(postId){

  const commentsEl =
    document.getElementById(
      "comments-" + postId
    );

  if(!commentsEl){
    return;
  }

  let count =

    parseInt(
      commentsEl.dataset.comments || "0"
    ) || 0;

  count++;

  commentsEl.dataset.comments =
    count;

  commentsEl.textContent =
    count + " comments";

  toast("Comment added");
}

// ================================
// SHARE
// ================================

function sharePost(url){

  navigator.clipboard.writeText(url);

  toast("Link copied");

}

// ================================
// SAVE
// ================================

function savePost(id){

  toast("Saved");

}

// ================================
// OPEN CHAT
// ================================

function openChat(){

  window.location.href =
    "chat.html";

}

//////////////////////////////////////////////////
// ❤️ SMART TOGGLE LIKE SYSTEM V4
//////////////////////////////////////////////////

window.__LIKE_LOCKS =
window.__LIKE_LOCKS || {};

window.likePost = async function(

  btn,
  postId

){

  try{

    //////////////////////////////////////////////////
    // 🛑 SPAM LOCK
    //////////////////////////////////////////////////

    if(
      window.__LIKE_LOCKS[postId]
    ){

      return;

    }

    window.__LIKE_LOCKS[postId] =
      true;

    //////////////////////////////////////////////////
    // ❤️ LIKE ELEMENT
    //////////////////////////////////////////////////

    const likesEl =

      document.getElementById(
        "likes-" + postId
      );

    if(!likesEl){

      return;

    }

    //////////////////////////////////////////////////
    // 📦 STORAGE KEY
    //////////////////////////////////////////////////

    const key =
      "liked_" + postId;

    //////////////////////////////////////////////////
    // ❤️ CURRENT COUNT
    //////////////////////////////////////////////////

    let currentLikes =

      parseInt(

        likesEl.dataset.likes ||
        "0"

      ) || 0;

    //////////////////////////////////////////////////
    // ❤️ STORAGE STATE
    //////////////////////////////////////////////////

    const alreadyLiked =

      localStorage.getItem(
        key
      ) === "true";

    //////////////////////////////////////////////////
    // ❤️ NEW COUNT
    //////////////////////////////////////////////////

    let newLikes =
      currentLikes;

    //////////////////////////////////////////////////
    // 💔 DISLIKE
    //////////////////////////////////////////////////

    if(alreadyLiked){

      newLikes = Math.max(
        0,
        currentLikes - 1
      );

      //////////////////////////////////////////////////
      // 💾 STORAGE
      //////////////////////////////////////////////////

      localStorage.removeItem(
        key
      );

      //////////////////////////////////////////////////
      // 🎨 BUTTON
      //////////////////////////////////////////////////

      btn?.classList.remove(
        "liked"
      );

    }

    //////////////////////////////////////////////////
    // ❤️ LIKE
    //////////////////////////////////////////////////

    else{

      newLikes =
        currentLikes + 1;

      //////////////////////////////////////////////////
      // 💾 STORAGE
      //////////////////////////////////////////////////

      localStorage.setItem(
        key,
        "true"
      );

      //////////////////////////////////////////////////
      // 🎨 BUTTON
      //////////////////////////////////////////////////

      btn?.classList.add(
        "liked"
      );

    }

    //////////////////////////////////////////////////
    // 🚀 FAST UI UPDATE
    //////////////////////////////////////////////////

    likesEl.dataset.likes =
      newLikes;

    likesEl.textContent =
      newLikes + " likes";

    //////////////////////////////////////////////////
    // 🚀 UPDATE LOCAL STATE
    //////////////////////////////////////////////////

    if(
      window.STATE?.FEED
    ){

      const post =

        window.STATE.FEED.find(
          p => p.id === postId
        );

      if(post){

        post.likes_count =
          newLikes;

        post.likes =
          newLikes;

      }

    }

    //////////////////////////////////////////////////
    // 🚀 SUPABASE UPDATE
    //////////////////////////////////////////////////

    const { error } =

      await supabaseClient

      .from("minigram_feed")

      .update({

        likes_count:
          newLikes

      })

      .eq(
        "id",
        postId
      );

    //////////////////////////////////////////////////
    // ❌ ERROR
    //////////////////////////////////////////////////

    if(error){

      console.error(error);

      //////////////////////////////////////////////////
      // ↩️ REVERT UI
      //////////////////////////////////////////////////

      likesEl.dataset.likes =
        currentLikes;

      likesEl.textContent =
        currentLikes + " likes";

      //////////////////////////////////////////////////
      // ↩️ REVERT STORAGE
      //////////////////////////////////////////////////

      if(alreadyLiked){

        localStorage.setItem(
          key,
          "true"
        );

        btn?.classList.add(
          "liked"
        );

      }else{

        localStorage.removeItem(
          key
        );

        btn?.classList.remove(
          "liked"
        );

      }

    }

  }catch(err){

    console.error(err);

  }finally{

    //////////////////////////////////////////////////
    // 🔓 UNLOCK
    //////////////////////////////////////////////////

    delete window
      .__LIKE_LOCKS[postId];

  }

};

// ================================
// GLOBAL EXPORT
// ================================

window.animateHeart =
  animateHeart;

window.likePost =
  window.likePost;

window.commentPost =
  commentPost;

window.sharePost =
  sharePost;

window.savePost =
  savePost;

window.openChat =
  openChat;

window.addEventListener &&

window.addEventListener(

  "error",

  e => console.log(

    "💀 ERROR IN FILE:",

    e.filename,

    e.message

  )

);
```

---

Generated by MiniGram MD Intelligence V6.
