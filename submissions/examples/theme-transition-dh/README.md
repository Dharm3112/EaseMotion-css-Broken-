# Smooth Theme Transition (Fade In/Out & Circular Reveal)

## What does this do?

This utility adds a premium, smooth-transitioning Dark and Light theme transition effect for background colors, text colors, and border colors when the theme is toggled. It features a circular reveal animation utilizing the modern View Transitions API, where the new mode expands outward in a circle from the bottom center to the top-right moon/sun icon.

## How is it used?

Apply the `.ease-theme-transition` class to the `body` or `html` container, and wrap your theme swap code inside `document.startViewTransition`:

```html
<!-- Apply transition utility to the body -->
<body class="ease-theme-transition">
  <!-- Interactive elements swap variables -->
</body>
```

```javascript
// Toggle state controller
themeToggleBtn.addEventListener("click", () => {
  const nextTheme =
    document.documentElement.getAttribute("data-theme") === "light"
      ? "dark"
      : "light";

  if (document.startViewTransition) {
    document.startViewTransition(() => {
      document.documentElement.setAttribute("data-theme", nextTheme);
    });
  } else {
    document.documentElement.setAttribute("data-theme", nextTheme);
  }
});
```

```css
/* Circular transition styles */
::view-transition-old(root),
::view-transition-new(root) {
  animation: none;
  mix-blend-mode: normal;
}

::view-transition-old(root) {
  z-index: 1;
}

::view-transition-new(root) {
  z-index: 9999;
  animation: clip-reveal 0.6s cubic-bezier(0.4, 0, 0.2, 1) both;
}

@keyframes clip-reveal {
  from {
    clip-path: circle(0% at 50% 100%);
  }
  to {
    clip-path: circle(150% at 50% 100%);
  }
}
```

## Why is it useful?

It perfectly matches the animation-first philosophy of EaseMotion CSS. Standard design systems often snap instantly during mode toggling. With this circular expansion, the interface morphs dynamically and performantly, leaving a beautiful impression on the user.
