# stories/view/story_view.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `stories/view/story_view.js` |
| Extension | `.js` |
| Bytes | 5932 |
| Lines | 252 |
| SHA-256 | `e0a62035213cc128ec12d2b744344be8402d19757185b68ba735e4b91964550a` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`stories`

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

- `initStoryView`
- `preloadImages`
- `getStorySrc`
- `render`
- `createBars`
- `startTimer`
- `next`
- `prev`
- `addEvents`
- `removeEvents`
- `handleClick`
- `handleHoldStart`
- `handleHoldEnd`
- `close`
- `destroyStoryView`
- `index`
- `data`
- `duration`
- `container`
- `img`
- `story`
- `storyImg`
- `storyAvatar`
- `storyUser`
- `src`
- `temp`
- `el`
- `fills`
- `start`
- `progress`
- `x`
- `avatar`
- `user`
- `bars`

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

`/storage/emulated/0/MINIGRAM1/stories/view/story_view.js`

It is NOT AI generated or rewritten.

```javascript
//////////////////////////////////////////////////
//  STORY VIEW JS (FINAL STABLE + NO LEAK)
//////////////////////////////////////////////////

(function(){

let index = 0;
let data = [];
let duration = 5000;

//  GLOBAL TIMER (IMPORTANT)
window._storyTimer = null;

//  scoped container
let container = null;

//////////////////////////////////////////////////
// INIT
//////////////////////////////////////////////////
function initStoryView(){

  console.log(" story view opened");

  container = document.querySelector(".storyViewPage");

  data = window.STORY_DATA || [];
  index = window.STORY_INDEX || 0;

  if(!data.length){
    console.warn(" No stories found");
    return close();
  }

  preloadImages();
  addEvents();
  render();
}

//////////////////////////////////////////////////
// PRELOAD
//////////////////////////////////////////////////
function preloadImages(){
  data.forEach(story=>{
    const img = new Image();
    img.src = story.image || story.url || story.avatar;
  });
}

//////////////////////////////////////////////////
// SAFE SRC
//////////////////////////////////////////////////
function getStorySrc(story){
  return story.image || story.url || story.avatar || "";
}

//////////////////////////////////////////////////
// RENDER
//////////////////////////////////////////////////
function render(){

  const story = data[index];
  if(!story) return close();

  const storyImg = document.getElementById("storyImage");
  const storyAvatar = document.getElementById("storyAvatar");
  const storyUser = document.getElementById("storyUsername");

  const src = getStorySrc(story);

  if(!src){
    console.warn(" Missing image");
    return next();
  }

  if(storyImg){
    storyImg.style.opacity = "0";

    const temp = new Image();
    temp.src = src;

    temp.onload = ()=>{
      storyImg.src = src;
      storyImg.style.opacity = "1";
    };

    temp.onerror = ()=>{
      next();
    };
  }

  if(storyAvatar) storyAvatar.src = story.avatar;
  if(storyUser) storyUser.textContent = story.user;

  createBars();
  startTimer();
}

//////////////////////////////////////////////////
// PROGRESS
//////////////////////////////////////////////////
function createBars(){

  const el = document.getElementById("storyProgress");
  if(!el) return;

  el.innerHTML = data.map((_, i)=>`
    <div class="bar">
      <div class="fill" style="width:${i < index ? '100%' : '0%'}"></div>
    </div>
  `).join("");
}

//////////////////////////////////////////////////
// TIMER (FIXED)
//////////////////////////////////////////////////
function startTimer(){

  const fills = document.querySelectorAll(".fill");
  if(!fills.length) return;

  clearInterval(window._storyTimer);

  let start = Date.now();

  window._storyTimer = setInterval(()=>{

    let progress = ((Date.now() - start) / duration) * 100;

    if(fills[index]){
      fills[index].style.width = progress + "%";
    }

    if(progress >= 100){
      next();
    }

  }, 16);
}

//////////////////////////////////////////////////
// NEXT / PREV
//////////////////////////////////////////////////
function next(){
  clearInterval(window._storyTimer);
  index++;

  if(index >= data.length) return close();
  render();
}

function prev(){
  clearInterval(window._storyTimer);
  index = Math.max(0, index - 1);
  render();
}

//////////////////////////////////////////////////
// EVENTS (SCOPED)
//////////////////////////////////////////////////
function addEvents(){

  if(!container) return;

  container.addEventListener("click", handleClick);
  container.addEventListener("touchstart", handleHoldStart);
  container.addEventListener("touchend", handleHoldEnd);
}

function removeEvents(){

  if(!container) return;

  container.removeEventListener("click", handleClick);
  container.removeEventListener("touchstart", handleHoldStart);
  container.removeEventListener("touchend", handleHoldEnd);
}

//////////////////////////////////////////////////
// HANDLERS
//////////////////////////////////////////////////
function handleClick(e){

  if(e.target.closest(".storyTop") || e.target.closest(".storyBottom")) return;

  const x = e.clientX;

  if(x < window.innerWidth / 2){
    prev();
  }else{
    next();
  }
}

function handleHoldStart(){
  clearInterval(window._storyTimer);
}

function handleHoldEnd(){
  startTimer();
}

//////////////////////////////////////////////////
// CLOSE
//////////////////////////////////////////////////
function close(){
  destroyStoryView();

  if(typeof loadPage === "function"){
    loadPage("home");
  }else{
    history.back();
  }
}

//////////////////////////////////////////////////
// CLEANUP (FINAL FIX)
//////////////////////////////////////////////////
function destroyStoryView(){

  console.log(" destroyStoryView");

  clearInterval(window._storyTimer);
  window._storyTimer = null;

  removeEvents();

  const img = document.getElementById("storyImage");
  const avatar = document.getElementById("storyAvatar");
  const user = document.getElementById("storyUsername");
  const bars = document.getElementById("storyProgress");

  if(img) img.src = "";
  if(avatar) avatar.src = "";
  if(user) user.textContent = "";
  if(bars) bars.innerHTML = "";

  container = null;
}

//////////////////////////////////////////////////
// EXPORT (IMPORTANT FOR LOADER)
//////////////////////////////////////////////////
window.FUNCTIONS = window.FUNCTIONS || {};

window.FUNCTIONS.initStoryView = initStoryView;

//  NAME MATCH WITH PAGE_CONFIG.destroy
window.FUNCTIONS.storyDestroy = destroyStoryView;

})();
window.addEventListener && window.addEventListener("error", e => console.log("💀 ERROR IN FILE:", e.filename, e.message));

```

---

Generated by MiniGram MD Intelligence V6.
