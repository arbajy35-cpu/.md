# fontawesome/scss/_rotated-flipped.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/_rotated-flipped.scss` |
| Extension | `.scss` |
| Size | 611 bytes |
| Lines | 32 |
| SHA-256 | `97a27a57f1c13026301cbe6038b1c608a070aef04661b9fc568a4c1fbc47543f` |

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
fontawesome/scss/_rotated-flipped.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/_rotated-flipped.scss`

No AI rewriting was performed on the source code.

```scss
// rotating + flipping icons
// -------------------------

.#{$fa-css-prefix}-rotate-90 {
  transform: rotate(90deg);
}

.#{$fa-css-prefix}-rotate-180 {
  transform: rotate(180deg);
}

.#{$fa-css-prefix}-rotate-270 {
  transform: rotate(270deg);
}

.#{$fa-css-prefix}-flip-horizontal {
  transform: scale(-1, 1);
}

.#{$fa-css-prefix}-flip-vertical {
  transform: scale(1, -1);
}

.#{$fa-css-prefix}-flip-both,
.#{$fa-css-prefix}-flip-horizontal.#{$fa-css-prefix}-flip-vertical { 
  transform: scale(-1, -1);
}

.#{$fa-css-prefix}-rotate-by {
  transform: rotate(var(--#{$fa-css-prefix}-rotate-angle, none));
}

```

---

Generated automatically.
