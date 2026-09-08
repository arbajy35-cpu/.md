# Games/void/void_js/commands.js

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/void/void_js/commands.js` |
| Extension | `.js` |
| Size | 1833 bytes |
| Lines | 158 |
| SHA-256 | `e3ae70ee7ef0bce37b7f8308ec6aa57fffc6663ad50c7b13c1d92955cc2b4f0c` |

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
Games/void/void_js/commands.js
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

`/storage/emulated/0/MINIGRAM1/Games/void/void_js/commands.js`

No AI rewriting was performed on the source code.

```javascript
function runCommand(cmd){

//////////////////////////////////////////////////
// LS
//////////////////////////////////////////////////

if(cmd==="ls"){

const items =
filesystem[currentPath];

if(items){

items.forEach(item=>{

addLine(item);

});

}

return;

}

//////////////////////////////////////////////////
// PWD
//////////////////////////////////////////////////

if(cmd==="pwd"){

addLine(currentPath);

return;

}

//////////////////////////////////////////////////
// CD
//////////////////////////////////////////////////

if(cmd.startsWith("cd ")){

const folder =
cmd.replace("cd ","").trim();

if(folder===".."){

const parts =
currentPath.split("/");

parts.pop();

currentPath =
parts.join("/");

updatePrompt();

return;

}

const newPath =
currentPath + "/" + folder;

if(filesystem[newPath]){

currentPath =
newPath;

updatePrompt();

}
else{

addLine(
"directory not found",
"error"
);

}

return;

}

//////////////////////////////////////////////////
// NANO
//////////////////////////////////////////////////

if(cmd.startsWith("nano ")){

const file =
cmd.replace("nano ","").trim();

if(fileContents[file]){

openNano(file);

}
else{

addLine(
"file not found",
"error"
);

}

return;

}

//////////////////////////////////////////////////
// CLEAR
//////////////////////////////////////////////////

if(cmd==="clear"){

document
.querySelectorAll(".line")
.forEach(el=>el.remove());

return;

}

addLine(
"unknown command",
"error"
);

}

input.addEventListener(
"keydown",
e=>{

if(e.key==="Enter"){

const cmd =
input.value.trim();

if(!cmd) return;

addLine(
symbol.innerText + " " + cmd,
"command"
);

runCommand(cmd);

input.value="";

}

}
);
```

---

Generated automatically.
