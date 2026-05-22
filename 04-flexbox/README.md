# Lesson 04 — Flexbox

Flexbox is for **one-dimensional layout** — arranging items in a row or a column. It's the right tool for nav bars, button groups, form rows, card internals, and any time you need to align things.

---

## The Two Roles

When you write `display: flex`, one element becomes the **flex container**. Its direct children become **flex items**.

```css
.nav {
  display: flex;          /* .nav is the container */
  gap: 16px;
  align-items: center;
}

/* .nav's children are the items — no extra CSS needed to participate */
```

---

## The Main Axis and Cross Axis

Flexbox has two axes. The `flex-direction` determines which is which.

```css
flex-direction: row;          /* main axis → horizontal (default) */
flex-direction: column;       /* main axis ↓ vertical */
flex-direction: row-reverse;  /* main axis ← horizontal, reversed */
```

**Alignment properties:**

| Property | Controls | Axis |
|----------|----------|------|
| `justify-content` | Spacing along the main axis | → or ↓ |
| `align-items` | Alignment on the cross axis | ↓ or → |
| `gap` | Space between items | both |

```css
.container {
  display: flex;
  justify-content: space-between; /* push items to ends */
  align-items: center;            /* vertically center them */
  gap: 16px;
}
```

---

## Common `justify-content` Values

```css
justify-content: flex-start;    /* pack to start (default) */
justify-content: flex-end;      /* pack to end */
justify-content: center;        /* center */
justify-content: space-between; /* first at start, last at end, rest evenly spaced */
justify-content: space-around;  /* equal space around each item */
justify-content: space-evenly;  /* equal space between and around items */
```

---

## Item-Level Controls

These go on the **items**, not the container:

```css
.item {
  flex: 1;           /* grow to fill available space */
  flex: 0 0 200px;   /* fixed 200px, don't grow or shrink */
  align-self: flex-end; /* override the container's align-items */
  order: -1;         /* move this item first visually */
}
```

`flex: 1` is the shorthand for `flex-grow: 1; flex-shrink: 1; flex-basis: 0`. It means: *share the available space equally.*

---

## Wrapping

```css
.container {
  display: flex;
  flex-wrap: wrap;  /* items wrap to a new row when they don't fit */
  gap: 16px;
}

.item {
  flex: 1 1 200px;  /* grow, shrink, and start at 200px wide */
  /* Result: as many items per row as fit at 200px, all equal width */
}
```

This is the simplest responsive grid — no media queries needed.

---

## Centering Anything

The most useful thing Flexbox does:

```css
.center-both {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

A `height` or `min-height` is needed for vertical centering to work.

---

## Flexbox vs Grid

Use Flexbox when:
- You have a **row or column** of items
- Items should size themselves based on their content
- You need wrapping behavior

Use Grid (Lesson 05) when:
- You have **rows AND columns** simultaneously
- You need precise placement
- You're laying out a whole page or large section

---

## Exercise

Open `starter/index.html`.

**Goals:**
- [ ] Use Flexbox to build a nav with logo on the left, links on the right
- [ ] Use `gap` and `align-items` to space and align the nav links
- [ ] Build a horizontal "stats" row with 4 equal-width cards using `flex: 1`
- [ ] Create a button group where buttons stay inline and have a consistent gap
- [ ] Center a hero text block both vertically and horizontally using `display: flex`
- [ ] Build a wrapping card row that fits as many `240px` cards per row as possible using `flex-wrap`
- [ ] **Bonus:** Use `order` to visually reorder items without changing the HTML

---

## Next

[Lesson 05 — Grid](../05-grid/)
