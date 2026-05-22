# Lesson 05 — CSS Grid

Grid is for **two-dimensional layout** — rows and columns at the same time. It's the right tool for page layouts, dashboards, galleries, and any component that needs both axes controlled.

---

## Defining a Grid

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* three equal columns */
  gap: 24px;
}
```

`1fr` means "one fraction of the available space." Three `1fr` columns split the space into thirds.

---

## Shorthand and `repeat()`

```css
grid-template-columns: repeat(3, 1fr);        /* same as 1fr 1fr 1fr */
grid-template-columns: repeat(4, 1fr);        /* four equal columns */
grid-template-columns: 240px 1fr;             /* fixed sidebar + flexible main */
grid-template-columns: 240px 1fr 300px;       /* sidebar + main + rail */
```

---

## `auto-fill` and `auto-fit` — Responsive Without Media Queries

```css
grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
```

This says: *"create as many columns as fit, each at least 240px wide."*

- `auto-fill` — fills the row with as many columns as possible (empty columns remain)
- `auto-fit` — same, but empty columns collapse (items stretch to fill the row)

This is the most powerful responsive layout pattern in CSS.

---

## Placing Items

By default, items flow automatically. You can override this:

```css
.item {
  grid-column: 1 / 3;    /* span from column line 1 to 3 (2 columns wide) */
  grid-row: 2 / 4;       /* span from row line 2 to 4 (2 rows tall) */

  /* Shorthand with span: */
  grid-column: span 2;   /* span 2 columns from wherever it lands */
}
```

---

## Named Grid Areas

The most readable way to define a layout:

```css
.page {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main main"
    "footer footer footer";
  grid-template-columns: 240px 1fr 1fr;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
}

header { grid-area: header; }
.sidebar { grid-area: sidebar; }
main { grid-area: main; }
footer { grid-area: footer; }
```

The visual ASCII art of `grid-template-areas` matches what the layout looks like. Changing the layout is as simple as rearranging the strings.

---

## Alignment

```css
.container {
  justify-items: center;   /* horizontal alignment of items in their cells */
  align-items: center;     /* vertical alignment of items in their cells */
  justify-content: center; /* horizontal alignment of the grid itself */
  align-content: center;   /* vertical alignment of the grid itself */
}

/* Per-item overrides: */
.item {
  justify-self: end;
  align-self: start;
}
```

---

## `subgrid` — Column Alignment Across Cards

Modern Grid supports `subgrid` — let a child element participate in the parent grid's tracks:

```css
.card {
  display: grid;
  grid-template-rows: subgrid;
  grid-row: span 3; /* card spans 3 rows in the parent */
}
/* Now card's internal rows align with sibling cards */
```

---

## Exercise

Open `starter/index.html`.

**Goals:**
- [ ] Build a 12-column grid layout for the main page
- [ ] Use `grid-template-areas` to place a header, sidebar, main, and footer
- [ ] Create an image gallery using `repeat(auto-fill, minmax(200px, 1fr))`
- [ ] Make a "bento box" card layout where some cards span 2 columns or rows
- [ ] Use `subgrid` on a card row to align titles and body text across all cards
- [ ] **Bonus:** Recreate a 3-column editorial layout with a pull quote spanning both rows in the middle column

---

## Next

[Lesson 06 — Cascade Layers](../06-cascade-layers/)
