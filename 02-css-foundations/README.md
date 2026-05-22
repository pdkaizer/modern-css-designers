# Lesson 02 — CSS Foundations

With semantic HTML in place, it's time to style it. This lesson covers three concepts that everything else in CSS builds on: **selectors**, **the box model**, and **the cascade**.

---

## How CSS Works

CSS connects **rules** to **elements**. Every rule has two parts:

```css
h1 {               /* selector — what to target */
  color: blue;     /* declaration — what to change */
  font-size: 2rem; /* another declaration */
}
```

The browser reads HTML top-to-bottom, applies all matching CSS rules, and paints the result.

---

## Selectors

| Selector | Targets | Example |
|----------|---------|---------|
| Element | All of that tag | `p { }` |
| Class | Elements with that class | `.card { }` |
| ID | The one element with that ID | `#header { }` |
| Descendant | B inside A | `nav a { }` |
| Direct child | B directly inside A | `ul > li { }` |
| Pseudo-class | Element in a state | `a:hover { }`, `li:first-child { }` |
| Pseudo-element | Part of an element | `p::first-line { }` |

**In practice:** use classes (`.name`) for almost everything. Avoid ID selectors for styling.

---

## The Box Model

Every element is a box. Each box has four layers, from inside out:

```
┌─────────────────────────────────┐
│            margin               │
│   ┌─────────────────────────┐   │
│   │         border          │   │
│   │  ┌───────────────────┐  │   │
│   │  │      padding      │  │   │
│   │  │  ┌─────────────┐  │  │   │
│   │  │  │   content   │  │  │   │
│   │  │  └─────────────┘  │  │   │
│   │  └───────────────────┘  │   │
│   └─────────────────────────┘   │
└─────────────────────────────────┘
```

- **Content** — the text or image
- **Padding** — space inside the border
- **Border** — a line around the padding
- **Margin** — space outside the border

**The `box-sizing` fix** (always include this):

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

By default, `width` doesn't include padding or border — which is confusing. `border-box` makes `width` mean the *total* visible width. This is how Figma works.

---

## The Cascade

When two rules target the same element, the browser decides which wins. The cascade has three layers:

**1. Specificity — more specific rules win**

```
Inline styles          > 1000 points
ID selectors (#id)     > 100 points
Class selectors (.cls) > 10 points
Element selectors (p)  > 1 point
```

`.card h2` wins over `h2` because it scores higher (10 + 1 vs 1).

**2. Source order — later rules win** (when specificity is equal)

**3. `!important`** — overrides everything. Avoid it; it creates debt.

---

## Units

| Unit | Relative to | Use for |
|------|-------------|---------|
| `px` | Pixels (fixed) | Borders, shadows, small details |
| `rem` | Root font size (usually 16px) | Typography, spacing |
| `em` | Parent font size | Component-relative sizing |
| `%` | Parent element | Widths, fluid values |
| `vw` / `vh` | Viewport width / height | Full-bleed layouts |
| `ch` | Width of "0" character | Ideal line lengths |

**Rule of thumb:** Use `rem` for most things. It scales with user font preferences.

---

## Exercise

Open `starter/index.html`. It's the semantic HTML page from Lesson 01, unstyled.

**Goals:**
- [ ] Add `box-sizing: border-box` to the reset
- [ ] Style the `body` — font family, max-width centered with margin auto, comfortable padding
- [ ] Style the heading hierarchy — different `font-size` and `color` for `h1`, `h2`, `h3`
- [ ] Add `padding` to the card and give it a `background`, `border-radius`, and `box-shadow`
- [ ] Style `button` — background color, border-radius, padding, a `:hover` state with a color change
- [ ] Style `nav` links — horizontal with `flexbox`, remove underline
- [ ] Style `footer` — smaller text, muted color, `border-top`

---

## Next

[Lesson 03 — Custom Properties](../03-custom-properties/)
