
# 🧱 Smart Grid Energy – Design & Development Rules (v1)

This is the master reference for how every layout, section, and file should behave on the Smart Grid Energy website. It includes current confirmed design logic, scaling behavior, content structure, and styling rules based on your actual project files as of April 2025.

---

## 📐 Global Layout & Responsiveness

- Entire site uses **clamp()** for scaling fonts, padding, and margins
- All sections are mobile-first and use media queries to adjust for screens ≥768px
- All images use `max-width: 100%` and `height: auto` for responsive scaling
- Text headers should avoid wrapping unless intended (e.g. subheader2 in Spanish)
- Use `white-space: nowrap` with overrides on `html[lang="es"]` when needed

---

## 🎨 Design + Colors

- Brand Primary: `#152a45` (Dark Blue)
- Accent: `#f0c14b` (hover color)
- Text/Base: `#fff` (white), `#ccc` (borders), `rgba(0, 0, 0, 0.08)` for shadow overlays
- Font: `'Open Sans', sans-serif` (loaded site-wide)
 - body background: linear-gradient(to bottom right, #EAEAEA, #ffffff);

---

## 🧭 Navigation

### Desktop
- Logo left
- Menu items vertically centered
- CTA centered between language toggle and phone
- Phone above language toggle
- Language toggle (🌐) right-aligned with dropdown behavior

### Mobile
- Logo left
- CTA center
- Hamburger menu right
- Mobile menu overlays with link stacking and language toggle

---

## 🏠 Hero Section

- Desktop hero uses:
  - `desktop-hero-header`
  - `desktop-subheader1-fix`
  - `desktop-subheader2-fix` positioned with `top: 58.6%`
  - CTA (`.desktop-cta-button-invert`) positioned at `top: 72.8%`, floats over garage

- Mobile hero uses:
  - `mobile-hero-header`
  - `mobile-subheader1-fix`
  - `mobile-subheader2-fix` (Spanish wraps, EN does not)
  - CTA (`.mobile-cta-button`) floats at `bottom: 3%`

---

## 🌐 Language Toggle (Weglot)

- Uses Weglot API
- Toggles between English and Spanish
- Custom relabel script with 150ms delay after switch
- Click-outside-to-close logic is implemented
- Custom dropdown styles override default Weglot menu
- `html[lang="en"] .lang-en` and `html[lang="es"] .lang-es` for content switching

---

## 🧾 Pages + Files

### index.html
- Main homepage with nav, hero, and CTA
- No meta description yet (needs SEO upgrade)

### form1.html
- Full consultation form layout
- Includes `img/unlocking.png` and testimonial block
- JS handles warning for non-homeowners
- Also missing meta description

### privacy-terms.html
- Plain text legal content
- Includes data, SMS, cookie, and contact policy
- Good heading hierarchy, missing description tag

---

## ✅ SEO Rules

- All `<img>` elements must include `alt=""` or descriptive alt text
- All pages should include `<meta name="description" content="...">`
- Pages should follow heading structure (H1 > H2 > P) without skipping levels
- Internal links should use real anchors or full page paths
- URLs should be readable and lowercase (`/energy-news`, not `/EnergyNews`)
- Prepare `sitemap.xml` and `robots.txt` before launch
- Optimize images (WebP, lazy loading) before production

---

## ✨ Additional Rules

- Animate CTA pulse only on primary conversion button
- Use fade-in or scroll animation sparingly and only after above-the-fold content
- Maintain mobile stacking logic in all new sections (e.g. testimonials, partners, blog)
- Use consistent file naming:
  - `index.html`, `form1.html`, `privacy-terms.html`
  - `style.css` for site-wide layout

---

:

🔐 Global Page Requirements (HTML + JS Integration)
All future HTML pages must include the following for consistent behavior across navigation, language toggling, and layout:

✅ The full Weglot-related JavaScript must be wrapped inside:

javascript
Copy
Edit
document.addEventListener("DOMContentLoaded", () => {
  Weglot.on("initialized", () => {
    // logic here
  });
});
✅ Language label toggle logic using updateLangLabel() must be included and delayed with setTimeout after language change.

✅ All .lang-en / .lang-es text elements must be wrapped with data-wg-notranslate to prevent Weglot conflicts.

✅ Header must include:

Logo linking to index.html

.desktop-only and .mobile-only visibility logic scoped in CSS

Manual mobile menu toggle and language toggle logic

✅ DOM-safe query selectors must be used with existence checks:

javascript
Copy
Edit
const menu = toggle.querySelector('.lang-menu');
if (!menu) return;
✅ Footer placement should follow Option A: content pushes it downward naturally — no position: fixed or flex: 1 unless specifically instructed.

---

📌 Last Updated: April 4, 2025  
This is version 1 of the design system. Update only after full audit or visual test cycle.
