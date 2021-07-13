# Sapper SEO-optimized template

Fully-preconfigured Sapper template for get 100-score on google-page-speed and acceleration of development.
I use this template for landing pages and high-performance projects, but it's easy to customize for any task.

## Roadmap

- [x] Aliases
- [x] ESLint + Prettier
- [x] Image-minimizing preconfigured
- [x] PNG -> WEBP configured
- [ ] Lazy-loading images
- [x] Base UI-elements ready for customizing
- [x] SVG icons preconfigured
- [x] SCSS mixins for adding custom fonts
- [x] Normalize.scss
- [x] PostCss preconfigured
- [x] Mixins for viewport usage
- [ ] Tests

## Usage

Click the button "Use this template" on the top of repository. Or just clone it and gelete .git folder :) 
I'll make it more comfortable in the future!

## Aliases

Use preconfigured aliases:

```
@ -> src
@ui -> src/components/ui
@consts -> src/consts
@styles -> src/styles
@directives -> src/directives
```

For customizing, check `/rollup.config.js`

## Image-minimizing && PNG -> WEBP configured

For minifying your image, save it into `/src/images`. If you don't want to process images, save it to `/static` folder.
Save `png` and `jpeg` here and custom plugin will generate `webp`, `png`, `jpeg` kit for use by Svelte component (`@ui/Image.svelte`).
For customize plugin config, see `/plugins/optimizeImages.js`.

## Base UI-elements ready for customizing

Use components:

- Menu burger
- Button

## SVG icons preconfigured

Save your SVG icons into `/src/icons`, it will processed into svg bundle, which can be used by `@ui/Icon.svelte`

In folder:

```
- src/icons
-- heart.svg
```

In Svelte component:

```
<script>
import Icon from '@ui/Icon.svelte';
</script>

<div class="heart-icon">
  <Icon name="heart" />
</div>

<style lang="scss">
.heart-icon {
  :global(svg) {
    fill: #000 // Configure svg parameters by css. You can use transitions or animations and change all css properties.
  }
}
</style>
```

## SCSS mixins for adding custom fonts

1. Add font in multiple formats into `/static/fonts/`;
2. Use font-mixins placed in `/src/styles/_fonts.scss` for add custom fonts.
   Usage:

```
@include font-face(
  MuseoSansCyrl,
  '/fonts/MuseoSansCyrl-Bold', // font link
  700, // weight
  normal, // style
  woff2 woff eot ttf // formats of font files
);
```

## PostCss preconfigured

See config file in `/config/postcss.config.js`

## Mixins for viewport usage

Use `@directives/inViewport.js` for adding custom animations and other logic by enter in viewPort.
Usage for adding class:

```
<script>
import { viewClass } from '@directives/inViewport';
</script>

<div class="block" use:viewClass>
</div>

<style lang="scss">
.block {
  transition: opacity ease .3s;
  opacity: 0;
  &.animate { // this class will be added when element reachs viewport;
    opacity: 1; // change css-properties for animating;
    /* I prefer to do this in separated file (@styles/animation.scss), but this is a matter of taste. */
  }
}
```

Usage for handling function:

```
<script>
import { viewport } from '@directives/inViewport';
function doSomething() {
  // do something...
}
</script>

<div class="block" use:viewport on:enterViewport={doSomething}>
</div>
```

## Contributing

I love contributions! I will happily accept your pull request! Your ideas might come in handy.
If you find grammar errors, please correct me!

## Used by this sites:
- http://niqitosiq.ru
- http://assol.jaex.ru

If you used this template, please make pull request with link for it!
