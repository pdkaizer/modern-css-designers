# Modern CSS for Designers

A hands-on course for designers who want to write real, modern HTML and CSS — not outdated tutorials from 2015.

Every lesson is written with **designers in mind**: you'll build things that look good, learn why the code works the way it does, and develop an intuition that bridges design thinking and front-end code.

---

## 🗺️ Course Map

| # | Lesson | What You'll Learn |
|---|--------|-------------------|
| 00 | [Getting Started](./00-getting-started/) | Set up your environment, open your first HTML file |
| 01 | [HTML Foundations](./01-html-foundations/) | Semantic HTML, document structure, thinking in elements |
| 02 | [CSS Foundations](./02-css-foundations/) | Selectors, the box model, the cascade |
| 03 | [Custom Properties](./03-custom-properties/) | Design tokens in CSS, theming, dynamic values |
| 04 | [Flexbox](./04-flexbox/) | One-dimensional layout, alignment, spacing |
| 05 | [Grid](./05-grid/) | Two-dimensional layout, named areas, responsive grids |
| 06 | [Cascade Layers](./06-cascade-layers/) | Taking control of specificity wars |
| 07 | [CSS Nesting](./07-css-nesting/) | Writing CSS the way your brain already thinks |
| 08 | [Container Queries](./08-container-queries/) | Components that respond to *their container*, not the viewport |
| 09 | [Modern Selectors](./09-modern-selectors/) | `:has()`, `:is()`, `:where()`, and logical grouping |
| 10 | [Animations & Transitions](./10-animations/) | Motion design in CSS, respecting user preferences |
| 11 | [Final Project](./11-final-project/) | Build a complete design system component library |
| ✦ | [Bonus — HTML Résumé](./12-bonus/) | Put it all together: build a real, printable résumé |

---

## 📁 Lesson Structure

Every lesson (01–11) follows the same format so you always know what to expect. The bonus activity (12) follows the same structure:

```
01-html-foundations/
├── README.md        ← Concepts explained, with visual examples
├── starter/
│   └── index.html   ← Your starting point — exercises are inside
└── solution/
    └── index.html   ← A complete reference solution (peek if stuck!)
```

**How to use each lesson:**
1. Read the `README.md` first — don't skip it
2. Open `starter/index.html` in your browser and your editor side by side
3. Follow the exercise prompts written in the HTML comments
4. Check `solution/index.html` when you're done (or stuck)

---

## 🛠️ Setup

**Get the course files**

Clone this repository to your computer:

```bash
git clone git@github.com:pdkaizer/modern-css-designers.git
cd modern-css-designers
```

Then open the `modern-css-designers` folder in VS Code.

---

You need two things:

**1. A code editor**
Download [VS Code](https://code.visualstudio.com/) — it's free and what most front-end developers use.

Recommended extensions:
- **Live Preview** (Microsoft) — see your changes instantly in the browser
- **Prettier** — auto-formats your code
- **CSS Peek** — jump from HTML to the CSS that styles it

**2. A modern browser**
Use [Chrome](https://www.google.com/chrome/) or [Firefox](https://www.mozilla.org/firefox/). All the CSS in this course is supported in evergreen browsers.

**That's it.** No build tools, no npm, no terminal commands. Just files.

---

## 💡 A Note on Modern CSS

This course deliberately avoids patterns you'll find on older tutorials:

| ❌ Old way | ✅ Modern way |
|-----------|--------------|
| `float: left` for layout | Flexbox / Grid |
| Lots of nested selectors | CSS Nesting |
| Repeated color values | Custom Properties |
| `!important` everywhere | Cascade Layers |
| Media queries only | Container Queries |
| Vendor prefixes | Baseline CSS |

The old ways still *work* — but the new ways are cleaner, more powerful, and match how designers actually think.

---

## 🗣️ How to Learn This Well

- **Type the code yourself.** Don't copy-paste. Muscle memory matters.
- **Break things on purpose.** Change a value and see what happens.
- **Connect it to your design tools.** After each lesson, think: "where does this concept live in Figma/Sketch?"
- **Don't memorize syntax.** Look things up. Even experienced developers Google CSS properties constantly.

---

## 🔗 Reference Resources

- [MDN Web Docs](https://developer.mozilla.org) — the definitive CSS/HTML reference
- [CSS Tricks](https://css-tricks.com) — visual guides and deep dives
- [Every Layout](https://every-layout.dev) — reusable layout primitives
- [Lea Verou's blog](https://lea.verou.me) — advanced CSS techniques
- [web.dev](https://web.dev/learn/css) — Google's structured CSS course

---

*Built for designers who are ready to speak the language of the web.*
