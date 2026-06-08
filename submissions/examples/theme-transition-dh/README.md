# Smooth Theme Transition (Fade In/Out)

## What does this do?

This utility adds a smooth, transitioning Dark and Light theme transition effect for background colors, text colors, and border colors when the theme is toggled. It prevents the abrupt color snaps and creates a softer, more premium visual experience.

## How is it used?

Apply the `.ease-theme-transition` class to the `body` or `html` container. Any subsequent theme token modifications will smoothly morph:

```html
<!-- Apply transition utility to the body -->
<body class="ease-theme-transition">
  <!-- Interactive elements swap variables -->
</body>
```

```css
/* Transition rule defined on body and all its children */
.ease-theme-transition,
.ease-theme-transition * {
  transition:
    background-color 0.4s cubic-bezier(0.4, 0, 0.2, 1),
    color 0.4s cubic-bezier(0.4, 0, 0.2, 1),
    border-color 0.4s cubic-bezier(0.4, 0, 0.2, 1),
    box-shadow 0.4s cubic-bezier(0.4, 0, 0.2, 1),
    text-shadow 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
```

## Why is it useful?

It perfectly matches the animation-first philosophy of EaseMotion CSS. Standard design systems often snap instantly during mode toggling. With this composable transition class, every element updates gracefully, giving the user interface a cohesive and premium feel.
