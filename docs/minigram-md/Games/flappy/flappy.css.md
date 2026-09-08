# Games/flappy/flappy.css

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `Games/flappy/flappy.css` |
| Extension | `.css` |
| Size | 873 bytes |
| Lines | 51 |
| SHA-256 | `dd4cdb21fa1c1a11797936c882d37435379e0811b3da3bc7b558ff716a82d343` |

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
Games/flappy/flappy.css
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

`/storage/emulated/0/MINIGRAM1/Games/flappy/flappy.css`

No AI rewriting was performed on the source code.

```css
body {
  margin: 0;
  background: linear-gradient(#70c5ce, #d0f5ff);
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: sans-serif;
}

#gameArea {
  position: relative;
  width: 320px;
  height: 520px;
  background: linear-gradient(#70c5ce, #bff2ff);
  overflow: hidden;
  border-radius: 10px;
  border: 2px solid #000;
  margin-top: 20px;
}

#bird {
  position: absolute;
  width: 32px;
  height: 32px;
  background: gold;
  border-radius: 50%;
  left: 60px;
  top: 200px;
  box-shadow: 0 3px 6px rgba(0,0,0,0.3);
}

.pipe {
  position: absolute;
  width: 52px;
  background: #1faa00;
  border: 2px solid #0b5e00;
}

#score {
  position: absolute;
  top: 10px;
  left: 10px;
  font-size: 22px;
  font-weight: bold;
}

#startBtn {
  margin-top: 12px;
  padding: 10px 18px;
  font-size: 16px;
}
```

---

Generated automatically.
