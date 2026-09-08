# global_css/animations.css

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `global_css/animations.css` |
| Extension | `.css` |
| Size | 462 bytes |
| Lines | 19 |
| SHA-256 | `bca7db76fe0bdc0fe1745594a9f276270082d5aa9cd384304c1327d095469de2` |

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
global_css/animations.css
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

`/storage/emulated/0/MINIGRAM1/global_css/animations.css`

No AI rewriting was performed on the source code.

```css
@keyframes fadeIn{
  from{opacity:0; transform:translateY(10px);}
  to{opacity:1; transform:translateY(0);}
}

@keyframes heartPop{
  0%{transform:translate(-50%,-50%) scale(.3);opacity:0;}
  50%{transform:translate(-50%,-50%) scale(1.2);opacity:1;}
  100%{transform:translate(-50%,-50%) scale(1);opacity:0;}
}

@keyframes skeleton{
  0%{background-position:-200px 0;}
  100%{background-position:200px 0;}
}

::-webkit-scrollbar{
  width:0px;
}
```

---

Generated automatically.
