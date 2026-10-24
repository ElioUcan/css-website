# Copilot instructions for `css-website`

## Project shape

This repository is a small, static HTML/CSS exercise for the Techium landing page. The working page is [CSS_advanced/index.html](/home/eliotito/holberton/csss/CSS_advanced/index.html), and its presentation work is intentionally split into numbered exercise stylesheets under [CSS_advanced/styles/](/home/eliotito/holberton/csss/CSS_advanced/styles/). Images and logos are kept locally in [CSS_advanced/images/](/home/eliotito/holberton/csss/CSS_advanced/images/).

The page is organized as one document with:

- a dark header and navigation;
- a hero section;
- anchored services, works, about, latest news, testimonials, and contact sections;
- a dark footer with address, social links, and footer navigation.

The navigation links depend on the section IDs in the HTML (`services`, `works`, `about`, `latest_news`, `testimonials`, and `contact`). Preserve those IDs and keep asset paths relative to `CSS_advanced/index.html`.

## Build, preview, test, and lint

There is no package manifest, build system, test runner, or linter configured in this repository. The deliverable is the static source itself.

From the repository root, preview the page with Python's built-in server:

```sh
python3 -m http.server 8000 --directory CSS_advanced
```

Then open <http://localhost:8000/> in a browser. This is preferable to opening the file directly because it exercises relative asset loading through HTTP.

For a quick source-level check, verify that the stylesheet and every referenced local asset exist:

```sh
grep -oE '(href|src)="[^"]+"' CSS_advanced/index.html
find CSS_advanced/images CSS_advanced/styles -type f -print
```

There is no automated single-test command. Validate an individual change by refreshing the page and checking the affected section at the relevant viewport sizes; for anchor or asset changes, also check the corresponding navigation link and browser console.

Before submitting changes, use:

```sh
git diff --check
```

## Implementation conventions

- Keep the page dependency-free. Do not add a framework, bundler, package manifest, or JavaScript dependency for styling tasks.
- Treat the numbered stylesheet name as part of the exercise progression. Add or modify the stylesheet referenced by the HTML rather than silently changing the link to a differently named file.
- Match the existing component vocabulary in the markup: `section`, `section-header`, `section-body`, `section-footer`, `container`, `row`, `col-1-2`, `col-1-3`, `card-*`, `nav`, `nav-item`, `nav-link`, and `button`.
- Preserve the existing section/row/card hierarchy when adding styles. Layout rules should target the structural classes already present instead of introducing one-off selectors tied to element order.
- Keep reusable layout and typography rules generic; use section-specific hooks such as `data-section-theme="dark"` for theme variations.
- Preserve the existing responsive foundation (`meta viewport`, flexible rows/columns, and intrinsic image dimensions). Check both narrow and wide layouts after changing widths, spacing, or typography.
- Use the supplied local assets and their existing dimensions/alt text conventions. Do not replace image paths with remote assets.
- Preserve smooth in-page navigation from `html { scroll-behavior: smooth; }` unless the exercise explicitly changes that behavior.
- Keep HTML formatting consistent with the current two-space indentation and existing semantic elements (`header`, `nav`, `main`, `section`, `article`, `footer`, `address`).
- External font loading currently comes from Google Fonts in the document head. If typography changes, keep the existing font-family intent and account for the page's network-free fallback behavior.

## Repository context

The project README is [CSS_advanced/README.md](/home/eliotito/holberton/csss/CSS_advanced/README.md). It describes this as continuing the previous Techium company website, so changes should extend the existing landing-page exercise rather than restructure it into a new application.
