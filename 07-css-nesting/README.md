# Lesson 07 — CSS Nesting

Native CSS nesting arrived in 2023 and is now supported in all modern browsers. It lets you write CSS the way your brain already organizes components — visually grouped by component, not scattered across a file.

---

## The Syntax

Nest related rules inside their parent:

```css
.card {
  background: white;
  border-radius: 12px;
  padding: 24px;

  /* Child element */
  .card__title {
    font-size: 1.25rem;
    color: #1a1a1a;
  }

  /* Modifier variant */
  &.card--featured {
    background: #f0f0ff;
    border: 2px solid blue;
  }

  /* Pseudo-class */
  &:hover {
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }

  /* Media query — nested inside a component */
  @media (max-width: 600px) {
    padding: 16px;
  }
}
```

The `&` symbol refers to the parent selector. `.card &` means "when `.card` is a descendant of something."

---

## How It Compiles

Nesting is pure CSS — no build step required. The browser handles it natively. This is equivalent:

```css
/* Nested (what you write): */
.button {
  background: blue;
  &:hover { background: darkblue; }
}

/* Flat (what the browser sees): */
.button { background: blue; }
.button:hover { background: darkblue; }
```

---

## Nesting Combinators

```css
.nav {
  /* Direct child */
  > .nav__item { padding: 8px; }

  /* Adjacent sibling */
  + .nav__submenu { display: none; }

  /* General sibling */
  ~ .nav__divider { opacity: 0.2; }
}
```

---

## The `&` in Detail

```css
.button {
  /* & at the start — modifier on the same element */
  &.button--large { font-size: 1.25rem; }

  /* No & — child element (implicit &) */
  .button__icon { width: 20px; }

  /* & at the end — this element inside something else */
  .dark-mode & { background: #333; }
}
```

---

## When to Nest (and When Not To)

**Good for nesting:**
- Component modifiers (`.card--featured`)
- Component children (`.card__title`, `.card__body`)
- State variants (`:hover`, `:focus`, `:disabled`)
- Responsive tweaks inside a component (`@media`)

**Avoid:**
- Deep nesting past 2-3 levels — it becomes hard to read
- Nesting unrelated rules just because they're nearby
- Recreating entire HTML hierarchies in CSS

A good rule: if you'd flatten it when debugging, don't nest it.

---

## Exercise

Open `starter/index.html`. The CSS is a flat list of rules for a card, button, and form component.

**Goals:**
- [ ] Refactor the `.card` rules into a single nested block
- [ ] Nest the `.card__title`, `.card__body`, `.card__tag` inside `.card`
- [ ] Nest `.card--compact` and `.card--featured` modifier rules with `&`
- [ ] Nest hover and focus states with `&:hover`, `&:focus`
- [ ] Nest a responsive override using `@media` inside the component
- [ ] Do the same for `.button` and `.field`

---

## Next

[Lesson 08 — Container Queries](../08-container-queries/)
