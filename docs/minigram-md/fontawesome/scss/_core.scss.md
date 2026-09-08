# fontawesome/scss/_core.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/_core.scss` |
| Extension | `.scss` |
| Size | 872 bytes |
| Lines | 44 |
| SHA-256 | `84c58c440041bcae5266f7b5c1cf10360ac09aac66f5725c8f4f88d00ac3446e` |

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
fontawesome/scss/_core.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/_core.scss`

No AI rewriting was performed on the source code.

```scss
// base icon class definition
// -------------------------

.#{$fa-css-prefix} {
  font-family: var(--#{$fa-css-prefix}-style-family, '#{$fa-style-family}');
  font-weight: var(--#{$fa-css-prefix}-style, #{$fa-style});
}

.#{$fa-css-prefix},
.#{$fa-css-prefix}-classic,
.#{$fa-css-prefix}-sharp,
.fas,
.#{$fa-css-prefix}-solid,
.far,
.#{$fa-css-prefix}-regular,
.fab,
.#{$fa-css-prefix}-brands {
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  display: var(--#{$fa-css-prefix}-display, #{$fa-display});
  font-style: normal;
  font-variant: normal;
  line-height: 1;
  text-rendering: auto;
}

.fas,
.#{$fa-css-prefix}-classic,
.#{$fa-css-prefix}-solid,
.far,
.#{$fa-css-prefix}-regular {
  font-family: 'Font Awesome 6 Free';
}

.fab,
.#{$fa-css-prefix}-brands {
  font-family: 'Font Awesome 6 Brands';
}


%fa-icon {
  @include fa-icon;
}

```

---

Generated automatically.
