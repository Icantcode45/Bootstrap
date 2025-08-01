---
layout: docs
title: CSS variables
description: Use Bootstrap's CSS custom properties for fast and forward-looking design and development.
group: customize
toc: true
---

Bootstrap includes many [CSS custom properties (variables)](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) in its compiled CSS for real-time customization without the need to recompile Sass. These provide easy access to commonly used values like our theme colors, breakpoints, and primary font stacks when working in your browser's inspector, a code sandbox, or general prototyping.

**All our custom properties are prefixed with `bs-`** to avoid conflicts with third party CSS.

## Root variables

Here are the variables we include (note that the `:root` is required) that can be accessed anywhere Bootstrap's CSS is loaded. They're located in our `_root.scss` file and included in our compiled dist files.

### Default

These CSS variables are available everywhere, regardless of color mode.

### Dark mode

These variables are scoped to our built-in dark mode.

## Component variables

Bootstrap 5 is increasingly making use of custom properties as local variables for various components. This way we reduce our compiled CSS, ensure styles aren't inherited in places like nested tables, and allow some basic restyling and extending of Bootstrap components after Sass compilation.

Have a look at our table documentation for some [insight into how we're using CSS variables]({{< docsref "/content/tables#how-do-the-variants-and-accented-tables-work" >}}). Our [navbars also use CSS variables]({{< docsref "/components/navbar#css" >}}) as of v5.2.0. We're also using CSS variables across our grids—primarily for gutters the [new opt-in CSS grid]({{< docsref "/layout/css-grid" >}})—with more component usage coming in the future.

Whenever possible, we'll assign CSS variables at the base component level (e.g., `.navbar` for navbar and its sub-components). This reduces guessing on where and how to customize, and allows for easy modifications by our team in future updates.

## Prefix

Most CSS variables use a prefix to avoid collisions with your own codebase. This prefix is in addition to the `--` that's required on every CSS variable.

Customize the prefix via the `$prefix` Sass variable. By default, it's set to `bs-` (note the trailing dash).

## Examples

CSS variables offer similar flexibility to Sass's variables, but without the need for compilation before being served to the browser. For example, here we're resetting our page's font and link styles with CSS variables.

```css
body {
  font: 1rem/1.5 var(--bs-font-sans-serif);
}
a {
  color: var(--bs-blue);
}
```

## Focus variables

{{< added-in "5.3.0" >}}

Bootstrap provides custom `:focus` styles using a combination of Sass and CSS variables that can be optionally added to specific components and elements. We do not yet globally override all `:focus` styles.

In our Sass, we set default values that can be customized before compiling.

{{< scss-docs name="focus-ring-variables" file="scss/_variables.scss" >}}

Those variables are then reassigned to `:root` level CSS variables that can be customized in real-time, including with options for `x` and `y` offsets (which default to their fallback value of `0`).

{{< scss-docs name="root-focus-variables" file="scss/_root.scss" >}}

## Grid breakpoints

While we include our grid breakpoints as CSS variables (except for `xs`), be aware that **CSS variables do not work in media queries**. This is by design in the CSS spec for variables, but may change in coming years with support for `env()` variables. Check out [this Stack Overflow answer](https://stackoverflow.com/a/47212942) for some helpful links. In the meantime, you can use these variables in other CSS situations, as well as in your JavaScript.
