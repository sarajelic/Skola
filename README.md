# Škola Bend Website

<!--
README SECTION TIPS (delete these after use):

About the Project:
- What is the main goal of this website?
- Why did you create it? (e.g., to promote the band, to learn web dev, to provide info for fans)
- What problem does it solve or what need does it fill?
- Who is the intended audience?
- Any unique aspects or inspiration?

Features:
- List all major features (e.g., responsive design, gallery, contact form, accessibility, sticky footer, social links, etc.)
- Mention any planned or upcoming features.

Screenshots:
- Add screenshots of the homepage, gallery, contact page, etc.
- Include wireframes or design mockups (add as images or links).
- Use Markdown image syntax: ![Description](path/to/image.png)

Getting Started:
- Step-by-step setup instructions (clone, install, run, open in browser, etc.)
- Mention any dependencies or tools needed (e.g., Node, Python, Live Server).
- Add deployment instructions if relevant.

Folder Structure:
- Show the main folders/files and what each contains.
- Briefly describe the purpose of key folders (e.g., assets/images for band photos).

Technologies Used:
- List all frameworks, libraries, and tools (e.g., Bootstrap, custom CSS, HTML5, etc.).
- Mention any build tools or preprocessors if used.

Accessibility & Semantics:
- List specific accessibility features (semantic HTML, ARIA, color contrast, keyboard navigation, etc.).
- Mention any audits or tools used (Lighthouse, axe, etc.).
- Note any accessibility goals or standards aimed for (e.g., WCAG).

Contributing:
- How can others contribute? (fork, PR, open issues)
- Any coding standards or guidelines?
- Link to a Code of Conduct if you have one.

License:
- State the license type (MIT, GPL, etc.).
- Link to the LICENSE file.

Other sections you might add:
- Live Demo: Link to a deployed version.
- Contact: How to reach you or the band.
- Roadmap: Planned features or improvements.
- Credits: Acknowledge contributors, designers, or inspiration.
- Badges: Add build, license, or other badges at the top.
-->

## Table of Contents
- [About the Project](#about-the-project)
- [Features](#features)
- [Screenshots](#screenshots)
- [Getting Started](#getting-started)
- [Folder Structure](#folder-structure)
- [Technologies Used](#technologies-used)
- [Accessibility & Semantics](#accessibility--semantics)
- [Contributing](#contributing)
- [License](#license)

## About the Project
<!-- See tips above: add your motivation, goals, reasoning, audience, and inspiration here. -->
This is the official website for Škola Bend, an alternative rock/punk band from Zagreb, Croatia. The site provides information about the band, a gallery of live performances, and a contact form for fans and event organizers. The design is modern, accessible, and responsive, ensuring a great experience on all devices.

The motivation behind this project came from a good friend of mine, who is a band member in Skola alongside her brother, cousin, boyfriend and friend, all of whom I know very well. They have been playing music together for about 3 years. Last year, they began playing in live music pubs, bars, and progressed to performing ahead of well known bands and musicians in small festivals. They created and released their first official song called "Ova Pjesma" (or in English: "This Song") earlier this year.

Due to their fast progression within Croatian music industry, they told me their next step was to get a website made, for bigger and more official exposure of band to fans, music event bookers, ...

## Features
<!-- List all major and planned features. -->
- Responsive design using Bootstrap 5
- Semantic HTML5 structure for accessibility
- Sticky footer on all pages
- Image gallery with uniform aspect ratio and high-DPI support
- Contact form with visible placeholders and accessible labels
- Social media links with accessible icons
- Consistent navigation and footer across all pages
- Visually hidden text for screen readers

## Screenshots
<!--
Add screenshots, wireframes, or design mockups here.
Example:
![Homepage Screenshot](assets/images/screenshots/homepage.png)
![Wireframe](assets/images/wireframes/homepage-wireframe.png)
-->

## Getting Started
<!-- Add setup, install, and run instructions. -->
1. Clone or download this repository.
2. Open `index.html` in your web browser.
3. For best results, use a local web server (e.g., VS Code Live Server, Python's `http.server`, or similar).

## Folder Structure
<!-- Briefly describe the purpose of key folders/files. -->
```
assets/
  css/
    styles.css
  fonts/
    SpecialElite-Regular.woff
  images/
    favicon.ico
    instagram.png
    skolalogo.png
    youtube.png
    gajnice/
      all.png
      eva-playing-drums.png
      everybody-except-eva.png
      iva-playing-bass-guitar.png
      max-davor-iva.png
    ksff/
      davor-and-antun.png
      eva.png
      fico.png
      ivamakseva.png
      jura.png
      krv.png
      maksivaroko.png
      whole-band.png
contact.html
gallery.html
index.html
feedback.html
README.md
```

## Technologies Used
<!-- List all frameworks, libraries, and tools. -->
- HTML5
- CSS3 (custom + Bootstrap 5)
- [Bootstrap 5.3.3](https://getbootstrap.com/)
- PNG images for social icons

## Accessibility & Semantics
<!-- List specific accessibility features and any audits/tools used. -->
- Uses semantic HTML elements: `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<figure>`, `<figcaption>`
- ARIA labels for navigation and social media links
- Visually hidden text for screen readers using `.visually-hidden`
- High color contrast and visible focus indicators
- Placeholder text for form fields is visible and accessible

## Contributing
<!-- Add contribution guidelines, PR process, and code of conduct if any. -->
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## License
<!-- State the license type and link to the LICENSE file. -->
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
