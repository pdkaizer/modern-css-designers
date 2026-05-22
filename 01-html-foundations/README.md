# Lesson 01 — HTML Foundations

Before we can style anything, we need content. This lesson is about writing HTML that actually *means* something.

---

## Semantic HTML

Every HTML element has a meaning. Using the right elements isn't just good practice — it affects accessibility, SEO, and how browsers interpret your content.

**Don't think about how things look. Think about what things *are*.**

| If it's... | Use... |
|------------|--------|
| A page title | `<h1>` |
| A section heading | `<h2>`, `<h3>`, etc. |
| Body text / prose | `<p>` |
| A clickable link | `<a href="...">` |
| A clickable action | `<button>` |
| Navigation links | `<nav>` |
| The main content | `<main>` |
| A self-contained piece | `<article>` |
| A grouped section | `<section>` |
| Supporting content | `<aside>` |
| Page footer | `<footer>` |
| Generic container | `<div>` (last resort) |

Designers often reach for `<div>` for everything. Resist that urge.

---

## Document Structure

A well-structured HTML page looks like an outline:

```html
<body>
  <header>
    <nav>...</nav>
  </header>

  <main>
    <article>
      <h1>Article Title</h1>
      <p>Intro paragraph...</p>

      <section>
        <h2>First section</h2>
        <p>Content...</p>
      </section>
    </article>
  </main>

  <footer>...</footer>
</body>
```

This nesting mirrors the visual hierarchy of a design. Figma's layers panel and HTML structure are closer than you'd think.

---

## Attributes

Elements can have **attributes** — extra information living inside the opening tag:

```html
<a href="https://example.com" target="_blank">Visit site</a>
<!-- href = where the link goes -->
<!-- target="_blank" = open in a new tab -->

<img src="photo.jpg" alt="A cat sleeping on a keyboard" />
<!-- src = path to the image file -->
<!-- alt = text description for screen readers -->
```

The `alt` attribute on images isn't optional if you care about accessibility (you should).

---

## Classes and IDs

**Classes** let you target specific elements with CSS:

```html
<p class="intro">This paragraph is special.</p>
<p>This one is not.</p>
```

```css
.intro {
  font-size: 1.25rem;
  font-weight: bold;
}
```

A class can be used on many elements. An ID (`id="..."`) should only appear once per page — reserve it for JavaScript hooks or page anchors, not styling.

---

## Exercise

Open `starter/index.html`. You'll find a wall of `<div>` tags with comments telling you what each section is *supposed* to be. Your job is to replace the divs with proper semantic HTML.

**Goals:**
- [ ] Use `<header>`, `<main>`, `<footer>` for the page regions
- [ ] Use `<nav>` for navigation links
- [ ] Use `<article>` and `<section>` for content groupings
- [ ] Use correct heading levels (`<h1>` through `<h3>`) — only one `<h1>` per page
- [ ] Use `<p>` for all prose
- [ ] Add `alt` text to the image
- [ ] Use `<button>` for the call-to-action, not `<div>`

Check `solution/index.html` when you're done.

---

## Next

[Lesson 02 — CSS Foundations](../02-css-foundations/)
