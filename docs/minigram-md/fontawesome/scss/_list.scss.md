# fontawesome/scss/_list.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/_list.scss` |
| Extension | `.scss` |
| Size | 447 bytes |
| Lines | 19 |
| SHA-256 | `21ff30ef1e9d26d276155e8f87b1f81e14cceb14c19ed8a8566ac7e547935aaa` |

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
fontawesome/scss/_list.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/_list.scss`

No AI rewriting was performed on the source code.

```scss
// icons in a list
// -------------------------

.#{$fa-css-prefix}-ul {
  list-style-type: none;
  margin-left: var(--#{$fa-css-prefix}-li-margin, #{$fa-li-margin});
  padding-left: 0;

  > li { position: relative; }
}

.#{$fa-css-prefix}-li {
  left: calc(var(--#{$fa-css-prefix}-li-width, #{$fa-li-width}) * -1);
  position: absolute;
  text-align: center;
  width: var(--#{$fa-css-prefix}-li-width, #{$fa-li-width});
  line-height: inherit;
}

```

---

Generated automatically.
