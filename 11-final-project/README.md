# Lesson 11 — Final Project

You've learned every major concept. Now put them together.

---

## The Brief

Build a **design system component library page** — a single HTML/CSS file that demonstrates all the techniques from this course working together as a cohesive system.

Think of it like a Figma component page, but in the browser.

---

## What to Build

A page that showcases the following components, all styled with your own token system:

### 1. Design Tokens Section
A visual display of your token system:
- Color swatches (brand, neutrals, semantic colors)
- Spacing scale
- Type scale
- Border radius scale

### 2. Typography
- Display heading (`h1`)
- Section heading (`h2`)
- Subsection heading (`h3`)
- Body text
- Small/label text
- Code text

### 3. Buttons
- Primary
- Secondary / Ghost
- Destructive
- Disabled state
- Loading state (with spinner animation)
- Icon + label

### 4. Form Elements
- Text input (default, focus, error states)
- Textarea
- Select
- Checkbox (with `:has()` label styling)
- Radio group

### 5. Cards
- Basic card
- Card with image (container query: horizontal on wide, vertical on narrow)
- Featured card
- Compact card

### 6. Navigation
- Top nav with logo and links
- Active state
- Mobile-adapted layout

### 7. Notifications / Alerts
- Info
- Success
- Warning
- Error
- With entrance animation

---

## Requirements

Your implementation must use:

- [ ] **Custom properties** — a complete token system in `:root`
- [ ] **Flexbox** — for component-level layout (nav, button internals, form rows)
- [ ] **Grid** — for page-level and component grid layouts
- [ ] **CSS Nesting** — at least the card and button components
- [ ] **Cascade Layers** — separate tokens, base, components, and utilities
- [ ] **Container queries** — at least one responsive card
- [ ] `:has()` — at least form field focus state and card image detection
- [ ] **Transitions** — all interactive elements
- [ ] **Keyframe animations** — at least the alert entrance and button spinner
- [ ] `prefers-reduced-motion` — motion must be optional

---

## Constraints (on purpose)

- **One HTML file** — no external CSS files, no JavaScript
- **No frameworks** — no Tailwind, Bootstrap, or any CSS library
- **No `!important`** — manage specificity properly with cascade layers

---

## Getting Started

Open `starter/index.html`. It provides:
- A complete token scaffold to fill in
- Cascade layer declarations in the right order
- Section headings and empty component slots

The `solution/index.html` shows one possible implementation. Yours will look different — that's the point.

---

## Grading Yourself

After you're done, check off:

- [ ] Does the page look intentional and designed, not accidental?
- [ ] Does dark mode work? (Either via `.dark` class or `prefers-color-scheme`)
- [ ] Do the cards respond to their container, not the viewport?
- [ ] Does everything still look good with animations disabled?
- [ ] Would a developer be able to use this as a reference to build the actual product?

If you can check all five — you've learned modern CSS.

---

*Nice work getting here.*
