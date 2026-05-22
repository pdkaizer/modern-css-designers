# Lesson 06 — Cascade Layers

Cascade layers solve one of the most frustrating problems in CSS: specificity wars. They let you organize CSS by *intent* and decide the override order explicitly.

---

## The Problem They Solve

You've got a design system with a base button style. A component overrides it. A utility class overrides that. Then someone adds `!important` because "nothing was working."

The real issue: when everything shares the same specificity space, order becomes fragile and `!important` becomes a crutch.

---

## Declaring Layers

```css
/* Declare the order first — lowest priority to highest */
@layer reset, base, components, utilities;
```

This one line establishes the entire hierarchy. Everything in `utilities` beats everything in `components`, regardless of selector specificity.

---

## Using Layers

```css
@layer reset {
  * { box-sizing: border-box; margin: 0; padding: 0; }
}

@layer base {
  body { font-family: system-ui; }
  h1 { font-size: 2rem; }
}

@layer components {
  .button {
    background: blue;
    padding: 12px 24px;
    border-radius: 8px;
  }
}

@layer utilities {
  .mt-0 { margin-top: 0; }
  .text-center { text-align: center; }
}
```

Now `.mt-0` will always win over `.button` styles, even if `.button` has higher specificity. The layer wins.

---

## The Specificity Surprise

Within a layer, specificity still applies. But a **low-specificity rule in a higher layer** beats a **high-specificity rule in a lower layer**:

```css
@layer base, components;

@layer base {
  .card .card__title { color: black; } /* specificity: 20 */
}

@layer components {
  p { color: red; } /* specificity: 1 — but it's in a higher layer */
}
/* .card__title inside .card will be red — the layer wins */
```

This is powerful. It means you can write simple, low-specificity utility rules that reliably override complex component styles.

---

## Unlayered CSS

Any CSS **not** in a layer is treated as if it's in the highest-priority implicit layer — it beats everything. This is useful for one-off overrides or third-party style patches.

---

## A Recommended Layer Order

```css
@layer tokens, reset, base, layout, components, patterns, utilities;
```

| Layer | Contains |
|-------|---------|
| `tokens` | CSS custom properties |
| `reset` | Box model, browser default removal |
| `base` | Body, typographic defaults |
| `layout` | Page-level grid/flex |
| `components` | UI component styles |
| `patterns` | Multi-component compositions |
| `utilities` | Single-purpose overrides |

---

## Exercise

Open `starter/index.html`. The file has CSS mixed together with specificity conflicts and some `!important` hacks.

**Goals:**
- [ ] Declare a layer order at the top of the `<style>` block
- [ ] Assign every existing rule into the appropriate layer
- [ ] Remove all `!important` declarations — fix specificity through layers instead
- [ ] Add a utilities layer with `.text-center`, `.mt-0`, and `.visually-hidden`
- [ ] Prove it works: a utility class should override a component style without needing `!important`

---

## Next

[Lesson 07 — CSS Nesting](../07-css-nesting/)
