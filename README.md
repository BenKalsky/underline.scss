# underline.scss

### Medium-Like Underline (SCSS Mixin)

```scss
$background-color: white !default;
$link-color: black !default;
$link-color-active: black !default;
$link-underline-color: $link-color !default;
$link-underline-color-active: $link-color-active !default;
$link-underline-width: 1px !default;
$link-underline-offset: 2px !default;
$breaking-underlines: true !default;

@mixin underline($color: $link-underline-color, $weight: $link-underline-width, $offset: $link-underline-offset) {
  background-image: linear-gradient(to top, transparent, transparent $offset, $color $offset, $color ($offset + $weight), transparent ($offset + $weight));
}

a {
  color: $link-color;
  transition: 100ms ease;

  &:hover, &:focus {
    color: $link-color-active;
  }
}

a.underline {
  text-decoration: none;
  position: relative;

  @if $breaking-underlines {
    text-shadow: (-1px) -1px 0 $background-color, 1px -1px 0 $background-color, -1px 1px 0 $background-color, 1px 1px 0 $background-color;
  }

  @include underline($link-color);

  @media (-webkit-min-device-pixel-ratio: 1.5), (min-resolution: 144dpi) {
    @include underline($link-color, 0.5);
  }

  &:hover, &:focus {
    @include underline($link-color-active);

    @media (-webkit-min-device-pixel-ratio: 1.5), (min-resolution: 144dpi) {
      @include underline($link-color-active, 0.5);
    }
  }
}
```
