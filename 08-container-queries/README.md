# Lesson 08 — Container Queries

Container queries are one of the most important additions to CSS in years. They let components respond to **their own container's size**, not the viewport.

---

## The Problem with Media Queries for Components

You're building a card component. It needs to be:
- Vertical layout in a sidebar (narrow)
- Horizontal layout in the main content area (wide)

With media queries, you'd write:

```css
@media (min-width: 768px) {
  .card { flex-direction: row; }
}
```

But this is based on the **viewport width**, not the card's context. What if you put that card in a sidebar on a large screen? It's still narrow — but the media query fires anyway.

Container queries solve this by asking: *"How wide is my container right now?"*

---

## Syntax

**Step 1:** Mark the container that will be queried.

```css
.card-wrapper {
  container-type: inline-size;
  /* You can also name it: */
  container-name: card;
  /* Shorthand: */
  container: card / inline-size;
}
```

**Step 2:** Write the query inside the component.

```css
.card {
  display: flex;
  flex-direction: column; /* default: vertical */
}

@container (min-width: 500px) {
  .card {
    flex-direction: row; /* horizontal when container is wide */
  }
}

/* Named container query: */
@container card (min-width: 500px) {
  .card { flex-direction: row; }
}
```

---

## Container Query Units

You also get new units relative to the container size:

| Unit | Meaning |
|------|---------|
| `cqw` | 1% of the container's width |
| `cqh` | 1% of the container's height |
| `cqi` | 1% of the container's inline size |
| `cqb` | 1% of the container's block size |
| `cqmin` | Smaller of `cqi` or `cqb` |
| `cqmax` | Larger of `cqi` or `cqb` |

```css
.card__title {
  font-size: clamp(1rem, 4cqi, 2rem);
  /* Scales with the container, not the viewport */
}
```

---

## The Mental Model Shift

| Before | After |
|--------|-------|
| "When the **screen** is 768px wide..." | "When **this component's space** is 500px wide..." |
| Layouts driven by viewport | Layouts driven by context |
| Components need to know where they live | Components are truly self-contained |

This is huge for design systems. A component should look right wherever you drop it, regardless of the page layout.

---

## Exercise

Open `starter/index.html`. You'll find a card component placed in two different contexts — a full-width main area and a narrow sidebar.

**Goals:**
- [ ] Set `container-type: inline-size` on the appropriate wrapper elements
- [ ] Write a `@container` query that makes the card layout horizontal when it has room (≥ 480px)
- [ ] Use `cqi` units to scale the card title's font size with the container
- [ ] Add a second container query that hides the card's image below 300px
- [ ] **Bonus:** Create a `.card--featured` variant that queries named containers differently

---

## Next

[Lesson 09 — Modern Selectors](../09-modern-selectors/)
