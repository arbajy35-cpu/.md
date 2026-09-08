# fontawesome/scss/regular.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/regular.scss` |
| Extension | `.scss` |
| Size | 750 bytes |
| Lines | 27 |
| SHA-256 | `5d2543b07cde6c0104b60596a6264d32b97a83ff8054e03aacec8e67ac9e6f6d` |

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
fontawesome/scss/regular.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/regular.scss`

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
  --#{$fa-css-prefix}-style-family-classic: '#{ $fa-style-family }';
  --#{$fa-css-prefix}-font-regular: normal 400 1em/1 '#{ $fa-style-family }';
}

@font-face {
  font-family: 'Font Awesome 6 Free';
  font-style: normal;
  font-weight: 400;
  font-display: $fa-font-display;
  src: url('#{$fa-font-path}/fa-regular-400.woff2') format('woff2'),
    url('#{$fa-font-path}/fa-regular-400.ttf') format('truetype');
}

.far,
.#{$fa-css-prefix}-regular {
  font-weight: 400;
}

```

---

Generated automatically.
