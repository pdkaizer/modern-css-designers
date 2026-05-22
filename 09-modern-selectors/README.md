# Lesson 09 — Modern Selectors

CSS selectors have evolved dramatically. This lesson covers the selectors that eliminate entire categories of JavaScript and enable layout logic you couldn't write before.

---

## `:is()` — Match Any of These

Before, targeting multiple selectors meant repetition:

```css
/* Old way */
header a:hover,
nav a:hover,
footer a:hover { color: blue; }
```

With `:is()`, you collapse it:

```css
:is(header, nav, footer) a:hover { color: blue; }
```

Specificity is determined by the **most specific argument** in `:is()`.

---

## `:where()` — Zero Specificity `:is()`

`:where()` works identically to `:is()`, but with **zero specificity**. This makes it perfect for base/reset styles that are easy to override:

```css
/* This has zero specificity — easy to override */
:where(h1, h2, h3, h4) {
  line-height: 1.2;
  font-weight: 700;
}
```

Use `:is()` when you want specificity to apply normally.
Use `:where()` for resets and defaults you expect to be overridden.

---

## `:has()` — The "Parent Selector" (and more)

This is the one designers have wanted for 20 years. `:has()` selects an element *based on its descendants or siblings*.

**Select a card that contains an image:**
```css
.card:has(img) {
  display: grid;
  grid-template-columns: 200px 1fr;
}
```

**Style a label when its associated input is checked:**
```css
label:has(input:checked) {
  font-weight: bold;
  color: green;
}
```

**Select a form section that has invalid inputs:**
```css
.field:has(:invalid) {
  border-color: red;
}
```

**Layout-aware: different grid if there are 3+ items:**
```css
.grid:has(.item:nth-child(3)) {
  grid-template-columns: repeat(3, 1fr);
}
```

`:has()` used to require JavaScript. Now it's pure CSS.

---

## `:not()` — Modern Exclusion

The old `:not()` only accepted a single simple selector. The modern version accepts full selector lists:

```css
/* Style all buttons except disabled ones and ghost variants */
.button:not(:disabled, .button--ghost) {
  background: var(--color-brand);
}
```

---

## Logical Combinations

These selectors compose:

```css
/* An article that has an image AND doesn't have a .no-feature class */
article:has(img):not(.no-feature) {
  /* featured layout */
}

/* Headings that are NOT inside an aside or footer */
:is(h2, h3):not(aside *, footer *) {
  margin-top: 2em;
}
```

---

## Exercise

Open `starter/index.html`. It contains a form, a card grid, and a navigation component.

**Goals:**
- [ ] Use `:is()` to target headings in multiple regions with one rule
- [ ] Use `:where()` to write resettable base styles for form elements
- [ ] Use `:has()` to style a form field wrapper differently when its input `:focus`es
- [ ] Use `:has()` to change a card's layout when it contains an `<img>`
- [ ] Use `:not()` to exclude `.disabled` items from a hover style
- [ ] **Bonus:** Use `:has(input:checked)` to build a CSS-only toggle UI

---

## Next

[Lesson 10 — Animations & Transitions](../10-animations/)
