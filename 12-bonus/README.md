# Bonus — HTML Résumé

A résumé is one of the most personal documents you'll ever build, and it turns out to be a perfect HTML/CSS project. It has a clear hierarchy, repeating structures, and a real-world audience.

This bonus activity has no new CSS concepts — it's a chance to practice the skills from the whole course on something you might actually ship.

---

## The Brief

Build a **single-page HTML résumé** for a fictional UX designer. Use only HTML and CSS — no frameworks, no JavaScript.

The résumé should look polished enough to send to a hiring manager.

---

## What to Build

A résumé with the following sections:

### Header
- Name (large, prominent)
- Job title
- Contact details: email, phone, location, website/LinkedIn
- Use `<address>` and `<a href="mailto:...">` for semantic correctness

### Summary
- A short professional bio paragraph

### Experience
- At least 3 roles, each with:
  - Job title, company, date range (use `<time>`)
  - 2–4 bullet points of accomplishments

### Education
- Degree, institution, graduation year

### Skills
- A visual list of skills grouped by category (Design, Tools, Code)

---

## Layout Options

Choose one:

**Option A — Two-column sidebar**
Sidebar (contact + skills) on the left, main content on the right.
Use CSS Grid: `grid-template-columns: 260px 1fr`.

**Option B — Single column**
Full-width, clean vertical flow.
Better for print. Use `max-width: 720px` centered.

---

## Requirements

- [ ] Use semantic HTML — `<header>`, `<main>`, `<section>`, `<article>`, `<address>`, `<time>`
- [ ] Design token system in `:root` — color, spacing, type scale
- [ ] At least one `@layer` block separating base from component styles
- [ ] Transitions on any interactive element (links, hover states)
- [ ] A `@media print` block — the page should print cleanly
- [ ] No `!important`

---

## Constraints (on purpose)

- One HTML file, one CSS file
- No frameworks
- Must pass a "would I actually send this?" test

---

## Getting Started

Open `starter/index.html`. The HTML structure is scaffolded for you — your job is to:

1. Replace the placeholder content with your fictional designer's real details
2. Fill in every `/* your styles here */` section in `styles.css`
3. Choose and implement a layout (sidebar or single-column)

The `solution/` folder shows a complete two-column implementation.

---

## Going Further

- Add a dark mode with `.dark` class or `prefers-color-scheme: dark`
- Add a subtle entrance animation on load (respect `prefers-reduced-motion`)
- Make it responsive — collapse the sidebar at narrow widths
- Host it on GitHub Pages

---

*This is a real thing you can keep. Make it yours.*
