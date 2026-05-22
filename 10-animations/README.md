# Lesson 10 — Animations & Transitions

Motion is a design material. This lesson covers how to write CSS animations that feel intentional, not gratuitous — and how to respect users who prefer reduced motion.

---

## Transitions (State Changes)

A `transition` smoothly interpolates a property between two states:

```css
.button {
  background: blue;
  transform: scale(1);
  transition: background 0.2s ease, transform 0.15s ease;
}

.button:hover {
  background: darkblue;
  transform: scale(1.02);
}
```

**Transition properties:**

| Property | What it does |
|----------|-------------|
| `transition-property` | Which CSS property to animate (`all` is tempting but avoid it) |
| `transition-duration` | How long (e.g. `200ms`, `0.2s`) |
| `transition-timing-function` | The easing curve |
| `transition-delay` | Wait before starting |

**Common easing values:**

```css
transition-timing-function:
  ease          /* fast start, slow end (default) */
  ease-in       /* slow start, fast end */
  ease-out      /* fast start, slow end */
  ease-in-out   /* slow start AND end */
  linear        /* constant speed — rarely right for UI */
  cubic-bezier(0.34, 1.56, 0.64, 1) /* custom — for spring-like effects */
```

---

## Animations (Keyframed Sequences)

When you need more than A→B, use `@keyframes`:

```css
@keyframes slide-up {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.card {
  animation: slide-up 0.3s ease-out both;
}
```

**`animation` shorthand order:**
```
animation: name duration timing-function delay iteration-count direction fill-mode;
```

**`fill-mode`:**
- `both` — apply `from` styles before the animation starts, `to` styles after it ends. Almost always what you want.
- `forwards` — keep the final state after the animation ends.
- `backwards` — apply the initial state during the delay.

---

## Staggered Animations

Delay each child slightly for a cascade effect:

```css
.list-item {
  animation: slide-up 0.3s ease-out both;
}

.list-item:nth-child(1) { animation-delay: 0ms; }
.list-item:nth-child(2) { animation-delay: 60ms; }
.list-item:nth-child(3) { animation-delay: 120ms; }

/* Or with custom properties: */
.list-item { animation-delay: calc(var(--i, 0) * 60ms); }
```

---

## Scroll-Triggered Animations

Modern CSS can trigger animations on scroll with `@keyframes` + `animation-timeline`:

```css
@keyframes fade-in {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

.section {
  animation: fade-in linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 30%;
}
```

No JavaScript intersection observer needed.

---

## `prefers-reduced-motion` — Non-Negotiable

Some users have vestibular disorders or motion sensitivity. Always wrap animations in a motion check:

```css
/* Define animations freely */
.button {
  transition: transform 0.2s ease;
}

/* Then disable or reduce them for users who prefer it */
@media (prefers-reduced-motion: reduce) {
  .button {
    transition: none;
  }

  /* Or keep subtle fade but remove movement: */
  .card {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

This isn't optional. It's accessibility and good design.

---

## What to Animate (and What Not To)

**Good to animate:**
- `opacity`
- `transform` (translate, scale, rotate)
- `clip-path`
- `filter` (blur, brightness)

**Avoid animating** (causes layout recalculation, janky performance):
- `width`, `height`
- `margin`, `padding`
- `top`, `left`
- `font-size`

When in doubt: **opacity + transform** can achieve almost any motion effect.

---

## Exercise

Open `starter/index.html`. You'll find a static UI with buttons, cards, and a notification.

**Goals:**
- [ ] Add a `transition` to buttons for hover and active states
- [ ] Write a `slide-up` keyframe animation for cards entering the page
- [ ] Stagger the card animations using `animation-delay`
- [ ] Build a CSS spinner using `@keyframes rotate` and `animation: rotate 1s linear infinite`
- [ ] Add a `prefers-reduced-motion` block that disables all animations
- [ ] **Bonus:** Implement a scroll-driven fade-in using `animation-timeline: view()`

---

## Next

[Lesson 11 — Final Project](../11-final-project/)
