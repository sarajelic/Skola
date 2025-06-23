# Testing & Known Issues

## Lighthouse & Evaluation Tool Warnings: Documentation

Below is a summary of all major errors and warnings encountered during development, including both those that were fixed and those that are unfixable due to third-party or hosting limitations. For details on fixes and design decisions, see the README.

### 1. Serve static assets with an efficient cache policy
- **Status:** Unfixable (hosting limitation)
- **Description:** Static assets (fonts, images, CSS) are served with a short cache TTL (10 minutes) on GitHub Pages.
- **Reason:** GitHub Pages does not allow custom cache headers. This cannot be changed from your codebase.
- **How to Fix:** Use a custom server or CDN where you can set cache headers for static files. Not possible on default GitHub Pages.

### 2. Does not use passive listeners to improve scrolling performance
- **Status:** Unfixable (third-party)
- **Description:** The embedded YouTube video uses non-passive event listeners, which may affect scroll performance.
- **Reason:** This is caused by YouTube's own JavaScript (www.youtube-nocookie.com). You cannot modify third-party scripts.
- **How to Fix:** Not possible unless YouTube updates their embed code. Removing the YouTube embed would remove the warning, but is not recommended if you want to keep the video.

### 3. Ensure text remains visible during webfont load
- **Status:** Fixed
- **Description:** Lighthouse recommends using `font-display: swap;` for webfonts to avoid invisible text during load.
- **Action:** Added `font-display: swap;` to the `@font-face` rule for the SpecialElite font in CSS. (See `assets/css/styles.css`)

### 4. Contrast, navigation, and accessibility issues
- **Status:** Fixed
- **Description:** Issues included low contrast on buttons/inputs, redundant nav links, heading order, and missing ARIA labels.
- **Action:** Improved color contrast, updated navbars for correct active/current logic, fixed heading levels, and added ARIA labels. (See HTML and CSS files)

### 5. Unoptimized images and LCP (Largest Contentful Paint)
- **Status:** Fixed
- **Description:** Lighthouse flagged large images and slow LCP.
- **Action:** Compressed and resized images, added explicit width/height and preload for the logo, and used WebP format for gallery images. (See `assets/images/` and HTML)

### 6. Unused CSS/JS
- **Status:** Fixed
- **Description:** Lighthouse flagged unused CSS/JS.
- **Action:** Removed all unused CSS and JavaScript. No custom JS is used; Bootstrap JS is loaded via CDN only as needed.

### 7. Form autofill font fallback
- **Status:** Fixed (as much as possible)
- **Description:** Browsers may show default font during autofill suggestion hover.
- **Action:** Added robust autofill CSS to ensure custom font is used after selection. (See README for browser limitation note)

### 8. Redundant/empty elements (e.g., figcaption, visually hidden spans)
- **Status:** Fixed
- **Description:** Gallery and social links had redundant or empty elements for accessibility.
- **Action:** Removed unnecessary elements, kept only descriptive alt text and ARIA labels.

### 9. Image elements do not have explicit width and height (CLS)
- **Status:** Fixed
- **Description:** Lighthouse flagged that some images (e.g., the Škola logo) did not have explicit width and height attributes, which can cause layout shifts and affect Cumulative Layout Shift (CLS) scores.
- **Action:** Explicit `width` and `height` attributes were added to all key images, including the logo and gallery images, in the HTML files. This ensures layout stability and optimal CLS. (See `index.html`, `gallery.html`, and other HTML files)

### 10. Reduce unused JavaScript (YouTube embed)
- **Status:** Unfixable (third-party)
- **Description:** Lighthouse flags a large amount of unused JavaScript loaded by the embedded YouTube video (base.js, www-embed-player-pc.js, etc.), with potential savings of ~700 KiB.
- **Reason:** These scripts are required by YouTube for the video player to function and are loaded automatically by the embed code. You cannot control or defer their loading from your codebase.
- **How to Fix:** The only way to eliminate this warning is to remove the YouTube embed or use a static image placeholder that loads the video only on user interaction ("lite" YouTube embed). This has tradeoffs for user experience and accessibility. See README for discussion.

### 11. Reduce unused CSS (YouTube embed, Bootstrap, Font Awesome)
- **Status:** Unfixable (third-party/CDN)
- **Description:** Lighthouse flags a large amount of unused CSS from the YouTube embed (www-player.css, embed_ui_css.css) and from Bootstrap/Font Awesome (CDN CSS), with potential savings of ~123 KiB.
- **Reason:** YouTube loads its own CSS for the video player, which cannot be modified or purged. Bootstrap and Font Awesome are loaded from CDN and include many general-purpose styles not used on this site.
- **How to Fix:** You cannot remove or defer unused CSS from third-party embeds or CDN libraries unless you self-host and customize them, or remove the YouTube embed. The current setup already uses non-blocking CSS loading for Bootstrap/Font Awesome, which is best practice for static sites.

---

## Lighthouse: Reduce unused CSS (Bootstrap, Font Awesome)

**Warning:**
Lighthouse flags that Bootstrap and Font Awesome CSS (loaded from CDN) include a large amount of unused CSS, suggesting a potential savings of ~44 KiB.

**Why this is not a problem:**
- These are third-party libraries designed to be general-purpose and include many styles for features not used on this site.
- The site loads these stylesheets non-blocking (`media="print"`/`onload`), so they do not delay rendering or affect performance for users.
- Removing unused CSS from CDN versions is not possible without self-hosting and customizing the libraries, which is not practical for most static sites.
- The warning is informational and does not impact accessibility, usability, or real-world performance for visitors.

**Conclusion:**
No action is needed. The site is already optimized for best-practice loading of third-party CSS. This warning can be safely ignored for this project.

---

## HTML Validation Warnings and Explanations (index.html)

### 1. Warning: Consider using the h1 element as a top-level heading only
- **Excerpt:**
  ```html
  <h1 id="about-heading" class="mb-3 h2">About Us</h1>
  ```
- **Explanation:**
  Only one `<h1>` is present on the page, used for the "About Us" heading. This is correct and best practice. The warning is informational and can be safely ignored, as the structure is accessible and semantically sound.

### 2. Warning: Section lacks heading
- **Excerpt:**
  ```html
  <section id="about" aria-labelledby="about-heading">
  ```
- **Explanation:**
  The `<section id="about">` contains a heading (`<h1 id="about-heading">About Us</h1>`) and uses `aria-labelledby` to reference it. This is semantically correct and accessible. The warning is informational and does not require changes.

### 3. Warning: Possible misuse of aria-label
- **Excerpt (previously):**
  ```html
  <div class="youtube-lazy ..." aria-label="YouTube video player" ...>
  ```
- **Explanation:**
  The `aria-label` was removed from the `.youtube-lazy` div to avoid misuse, as the button inside is the interactive element. The div now has no `aria-label`, resolving the warning.

### 4. Error: The element button must not appear as a descendant of an element with the attribute role=button
- **Excerpt (previously):**
  ```html
  <div class="youtube-lazy ..." role="button"> ... <button> ... </button> ... </div>
  ```
- **Explanation:**
  The `role="button"` was removed from the `.youtube-lazy` div, so the button is not inside an element with `role=button`. This resolves the error and improves accessibility.

---

All warnings and errors above have been reviewed and addressed for accessibility and semantic correctness. No further action is needed unless new issues are reported.

---

**Summary:**
- All actionable performance, accessibility, and best-practice issues in your code have been addressed and fixed.
- The only remaining warnings are caused by third-party services (YouTube) or hosting limitations (GitHub Pages cache policy) and cannot be fixed from your codebase.
- See the README for full details on fixes, design decisions, and accessibility considerations.
