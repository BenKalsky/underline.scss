---
layout: page
title: The Mixin
---

UNDERLINE.SCSS is a carefully crafted, pixel-perfect, medium-like underline, inspired by [Marcin Wichary's post - Crafting link underlines on Medium](https://medium.design/crafting-link-underlines-on-medium-7c03a9274f9#.jhvfwlt8q).

### Settings:
```scss
$text-color: black !default;
$text-color-active: rgba($text-color, .8) !default;
$underline-color: $text-color !default;
$underline-color-active: $text-color-active !default;
$background-color: white !default;
$underline-width: 1px !default;
$underline-offset: 2px !default;
$breaking-underlines: true !default;
```

### The Mixin:
```scss
@mixin underline($color: $underline-color, $weight: $underline-width, $offset: $underline-offset) {
  background-image: linear-gradient(to top, transparent, transparent $offset, $color $offset, $color ($offset + $weight), transparent ($offset + $weight));
}
```

### Usage:
```scss
a {
  color: $text-color;
  transition: .2s;
  text-decoration: none;
  position: relative;

  @if $breaking-underlines {
    text-shadow: (-1px) -1px 0 $background-color, 1px -1px 0 $background-color, -1px 1px 0 $background-color, 1px 1px 0 $background-color;
  }

  @include underline($text-color);

  @media (-webkit-min-device-pixel-ratio: 1.5), (min-resolution: 144dpi) {
    @include underline($text-color, .5);
  }

  &:hover, &:focus {
    color: $text-color-active;
    text-decoration: none;

    @include underline($text-color-active);

    @media (-webkit-min-device-pixel-ratio: 1.5), (min-resolution: 144dpi) {
      @include underline($text-color-active, .5);
    }
  }
}
```

<3

