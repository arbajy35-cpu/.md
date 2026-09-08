# fontawesome/scss/_stacked.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/_stacked.scss` |
| Extension | `.scss` |
| Size | 633 bytes |
| Lines | 33 |
| SHA-256 | `09c7d146ce7d2b50c17c457047d5fb7291af7a7a60d0c88c736a0524ba3f3acb` |

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
fontawesome/scss/_stacked.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/_stacked.scss`

No AI rewriting was performed on the source code.

```scss
// stacking icons
// -------------------------

.#{$fa-css-prefix}-stack {
  display: inline-block;
  height: 2em;
  line-height: 2em;
  position: relative;
  vertical-align: $fa-stack-vertical-align;
  width: $fa-stack-width;
}

.#{$fa-css-prefix}-stack-1x,
.#{$fa-css-prefix}-stack-2x {
  left: 0;
  position: absolute;
  text-align: center;
  width: 100%;
  z-index: var(--#{$fa-css-prefix}-stack-z-index, #{$fa-stack-z-index});
}

.#{$fa-css-prefix}-stack-1x {
  line-height: inherit;
}

.#{$fa-css-prefix}-stack-2x {
  font-size: 2em;
}

.#{$fa-css-prefix}-inverse {
  color: var(--#{$fa-css-prefix}-inverse, #{$fa-inverse});
}

```

---

Generated automatically.
