# Lesson 03 — Custom Properties (CSS Variables)

Custom properties are one of the biggest shifts in modern CSS. They're how you bring **design tokens** into code.

---

## What Are They?

A custom property is a variable you define once and use everywhere:

```css
:root {
  --color-brand: #2c2cff;
}

h1 { color: var(--color-brand); }
button { background: var(--color-brand); }
```

Change the value in one place, it updates everywhere. Sound familiar? It's the same as updating a color style in Figma.

---

## The `:root` Convention

`:root` is the top-level element of the page — equivalent to `<html>`. Custom properties defined here are available *everywhere* in the stylesheet. Think of it as your global token file.

```css
:root {
  /* Color tokens */
  --color-bg: #f5f4f0;
  --color-surface: #ffffff;
  --color-text: #1a1a1a;
  --color-text-muted: #666;
  --color-brand: #2c2cff;
  --color-brand-dark: #1a1aaa;

  /* Spacing tokens (base-4 scale) */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-6: 24px;
  --space-8: 32px;
  --space-12: 48px;
  --space-16: 64px;

  /* Typography tokens */
  --font-sans: system-ui, sans-serif;
  --font-mono: ui-monospace, monospace;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-4xl: 2.25rem;

  /* Radius tokens */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-full: 9999px;
}
```

---

## Fallback Values

`var()` accepts an optional fallback:

```css
color: var(--color-brand, blue);
/* If --color-brand isn't defined, use blue */
```

---

## Local Overrides (The Superpower)

Custom properties inherit through the DOM. You can override them for a subtree:

```css
:root {
  --color-bg: white;
  --color-text: black;
}

.dark-section {
  --color-bg: #1a1a1a;
  --color-text: white;
  /* Now everything inside .dark-section uses these values */
}
```

This is how dark mode works in production CSS — a single class toggle, no duplicate rules.

---

## Theming a Component

```css
.button {
  background: var(--button-bg, var(--color-brand));
  color: var(--button-color, white);
  padding: var(--space-3) var(--space-6);
}

/* In context, override just the button tokens */
.danger-zone .button {
  --button-bg: #d00;
}
```

---

## Custom Properties vs. Preprocessor Variables (Sass/Less)

| | CSS Custom Properties | Sass Variables |
|---|---|---|
| Lives in the browser | ✅ | ❌ (compile-time only) |
| Changeable at runtime | ✅ | ❌ |
| Inheritable through DOM | ✅ | ❌ |
| Requires build step | ❌ | ✅ |

Custom properties are strictly more powerful for UI work.

---

## Exercise

Open `starter/index.html`. You'll find a page with hard-coded color, spacing, and typography values scattered everywhere.

**Goals:**
- [ ] Define a token system in `:root` (colors, spacing, type scale, radius)
- [ ] Replace every hard-coded value in the CSS with `var(--token-name)`
- [ ] Add a `.dark` class to `<body>` and override the color tokens to create a dark theme
- [ ] Create a `.compact` variant for a card that overrides its spacing tokens locally
- [ ] **Bonus:** Add a `prefers-color-scheme: dark` media query that auto-applies the dark theme

---

## Next

[Lesson 04 — Flexbox](../04-flexbox/)
