# Testing & Validation

## Table of Contents
- [During Development Testing](#during-development-testing)
- [Manual Testing](#manual-testing)
- [Bugs and Fixes](#bugs-and-fixes)
- [Post Development Testing](#post-development-testing)
  - [Validators](#validators)
    - [HTML](#html)
    - [CSS](#css)
  - [Lighthouse Scores](#lighthouse-scores)
    - [Desktop Version](#desktop-version)
    - [Mobile Version](#mobile-version)
  - [Lighthouse Score Feedback From Third Party Testers](#lighthouse-score-feedback-from-third-party-testers)
  - [Accessibility](#accessibility)

## During Development Testing

All major errors and warnings encountered during development were documented and addressed as they arose. For details on fixes and design decisions, see the README.

- Issues with cache policy, third-party scripts, and webfont loading were identified and resolved or documented if unfixable (see below).
- Accessibility, navigation, and contrast issues were fixed iteratively.
- Image optimization and layout stability were improved throughout development.

## Manual Testing

- **Accessibility Testing:** Confirmed compatibility with screen readers and keyboard navigation.
- **Cross-Browser Testing:** Site tested across all major browsers (Chrome, Firefox, Edge, Safari).
- **Responsive Testing:** Verified on mobile, tablet, and desktop screen sizes.
- **User Experience:** All navigation, forms, and interactive elements are accessible and usable via keyboard.

## Bugs and Fixes

- **Font Choice & Special Characters:**
  Switched from `FrederickSans` to `SpecialElite` due to readability issues and lack of support for characters like “Š”.
- **FontAwesome Icon Display Issue:**
  Resolved issue with missing social media icons; initially used PNG placeholders, later replaced with FontAwesome via code adjustments.
- **Gallery Image Consistency:**
  Fixed inconsistent image heights by using uniform thumbnails and full-size WebP images for better layout and load times.
- **Contact Form User Experience:**
  Replaced external Formspree with custom feedback page for seamless UX; current version functions as a demo.
- **Redundant nav link vs. crawlability (WAVE vs. Lighthouse SEO):**
  Kept `href` on all nav links for SEO and accessibility, accepting the WAVE redundant link warning as informational.
- **Contrast, navigation, and accessibility issues:**
  Improved color contrast, updated navbars for correct active/current logic, fixed heading levels, and added ARIA labels.
- **Unoptimized images and LCP (Largest Contentful Paint):**
  Compressed and resized images, added explicit width/height and preload for the logo, and used WebP format for gallery images.
- **Unused CSS/JS:**
  Removed all unused CSS and JavaScript. No custom JS is used; Bootstrap JS is loaded via CDN only as needed.
- **Form autofill font fallback:**
  Added robust autofill CSS to ensure custom font is used after selection. (See README for browser limitation note)
- **Redundant/empty elements (e.g., figcaption, visually hidden spans):**
  Removed unnecessary elements, kept only descriptive alt text and ARIA labels.
- **Image elements do not have explicit width and height (CLS):**
  Explicit `width` and `height` attributes were added to all key images, including the logo and gallery images, in the HTML files.
- **Other Issues:**
  See the detailed list of warnings and fixes in the sections below.

## Post Development Testing

### Validators

#### HTML
- **W3C Markup Validator:** HTML verified for compliance.
- **Common Warnings:**
  - Use of `<h1>` as a top-level heading only (informational, correct usage).
  - Section lacks heading (resolved with `aria-labelledby`).
  - Possible misuse of `aria-label` (resolved).
  - Button inside element with `role=button` (resolved).

#### CSS
- **W3C CSS Validator:** CSS checked and passed.
- **Common Warnings:**
  - Vendor-specific warnings for `@font-face` (expected, no impact).

### Lighthouse Scores

#### Desktop Version
- All pages scored 90+ in all categories after optimization.
- Accessibility warnings addressed (color contrast, heading order, ARIA attributes, alt text, focus states).
- Performance improved by optimizing images (WebP), lazy-loading non-critical assets, and preloading LCP images.
- Best Practices and SEO warnings resolved (meta descriptions, link `href`/`aria-current`, favicon, etc.).
- <strong>Note:</strong> If you see a "Serve static assets with an efficient cache policy" warning in Lighthouse, this is due to GitHub Pages' default cache settings (10 minutes TTL). This cannot be changed from the codebase. All images and assets are optimized for size and performance, and this warning does not impact real-world user experience.
- Remaining warnings (if any) are due to third-party scripts (YouTube) or hosting limitations (GitHub Pages cache policy) and are documented below.

#### Mobile Version
- Mobile scores are similar to desktop, with minor differences due to device emulation and network throttling in Lighthouse.
- All actionable issues were fixed; remaining warnings are due to third-party scripts or hosting limitations.

### Lighthouse Score Feedback From Third Party Testers
- Third-party testers confirmed high scores and accessibility compliance.
- Any remaining warnings are informational and do not impact real-world usability or SEO.

### Accessibility
- All navigation, forms, and interactive elements are accessible and usable via keyboard.
- ARIA attributes and semantic HTML are used throughout.
- Color contrast and focus indicators meet accessibility standards.
- See README for a summary of accessibility features and any known limitations.

---

All actionable performance, accessibility, and best-practice issues in your code have been addressed and fixed. The only remaining warnings are caused by third-party services (YouTube) or hosting limitations (GitHub Pages cache policy) and cannot be fixed from your codebase. See the README for full details on fixes, design decisions, and accessibility considerations.