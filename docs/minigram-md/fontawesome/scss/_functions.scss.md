# fontawesome/scss/_functions.scss

> MiniGram MD Intelligence V5

## File Information

| Property | Value |
|---|---|
| Source | `fontawesome/scss/_functions.scss` |
| Extension | `.scss` |
| Size | 2115 bytes |
| Lines | 58 |
| SHA-256 | `c2bd4a045bc07d0b92563259ccf877bdfa18fb0c6ccefd446f8176bf5ca06973` |

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
fontawesome/scss/_functions.scss
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

`/storage/emulated/0/MINIGRAM1/fontawesome/scss/_functions.scss`

No AI rewriting was performed on the source code.

```scss
// functions
// --------------------------

// fa-content: convenience function used to set content property
@function fa-content($fa-var) {
  @return unquote("\"#{ $fa-var }\"");
}

// fa-divide: Originally obtained from the Bootstrap https://github.com/twbs/bootstrap
//
// Licensed under: The MIT License (MIT)
//
// Copyright (c) 2011-2021 Twitter, Inc.
// Copyright (c) 2011-2021 The Bootstrap Authors
//
// Permission is hereby granted, free of charge, to any person obtaining a copy
// of this software and associated documentation files (the "Software"), to deal
// in the Software without restriction, including without limitation the rights
// to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
// copies of the Software, and to permit persons to whom the Software is
// furnished to do so, subject to the following conditions:
//
// The above copyright notice and this permission notice shall be included in
// all copies or substantial portions of the Software.
//
// THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
// IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
// FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
// AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
// LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
// OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
// THE SOFTWARE.

@function fa-divide($dividend, $divisor, $precision: 10) {
  $sign: if($dividend > 0 and $divisor > 0, 1, -1);
  $dividend: abs($dividend);
  $divisor: abs($divisor);
  $quotient: 0;
  $remainder: $dividend;
  @if $dividend == 0 {
    @return 0;
  }
  @if $divisor == 0 {
    @error "Cannot divide by 0";
  }
  @if $divisor == 1 {
    @return $dividend;
  }
  @while $remainder >= $divisor {
    $quotient: $quotient + 1;
    $remainder: $remainder - $divisor;
  }
  @if $remainder > 0 and $precision > 0 {
    $remainder: fa-divide($remainder * 10, $divisor, $precision - 1) * .1;
  }
  @return ($quotient + $remainder) * $sign;
}

```

---

Generated automatically.
