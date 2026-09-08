# fontawesome/scss/brands.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/brands.scss` |
| Extension | `.scss` |
| Size | 867 bytes |
| Lines | 31 |
| SHA-256 | `40a5b757efc973d236d992d85e61c6db9f71d5d64ddd4cc1b1a3bc9a7c5b49fe` |

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
fontawesome/scss/brands.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/brands.scss`

No AI rewriting was performed on the source code.

```scss
/*!
 * Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com
 * License - https://fontawesome.com/license/free (Icons: CC BY 4.0, Fonts: SIL OFL 1.1, Code: MIT License)
 * Copyright 2023 Fonticons, Inc.
 */
@import 'functions';
@import 'variables';

:root, :host {
  --#{$fa-css-prefix}-style-family-brands: 'Font Awesome 6 Brands';
  --#{$fa-css-prefix}-font-brands: normal 400 1em/1 'Font Awesome 6 Brands';
}

@font-face {
  font-family: 'Font Awesome 6 Brands';
  font-style: normal;
  font-weight: 400;
  font-display: $fa-font-display;
  src: url('#{$fa-font-path}/fa-brands-400.woff2') format('woff2'),
    url('#{$fa-font-path}/fa-brands-400.ttf') format('truetype');
}

.fab,
.#{$fa-css-prefix}-brands {
  font-weight: 400;
}

@each $name, $icon in $fa-brand-icons {
  .#{$fa-css-prefix}-#{$name}:before { content: unquote("\"#{ $icon }\""); }
}

```

---

Generated automatically.
