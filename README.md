# Gabriela Theis Marchan — Portfolio

Personal portfolio site for Gabriela Theis Marchan, a PhD Chemical Engineering student at Louisiana State University working on machine learning and materials science.

**Live site:** https://gabi107.github.io

## What's on the site

A single scrolling page with a sticky navigation bar that highlights the section in view:

| Section | Contents |
| --- | --- |
| Header | Name, role, contact buttons, and a surfactant molecule drawn as a graph |
| About | Bio, headshot, work authorization, contact details |
| Research | Ongoing and published research projects |
| Experience | Research, industry and teaching roles as a timeline |
| Publications | Papers, newest first, linked to the publisher |
| Education | Degrees |
| Skills | Technical skills, grouped by category |

The content follows the resume. The resume `.docx` is kept locally in the repo folder but is listed in `.gitignore`, so it's never published.

## Project structure

```
.
├── .gitignore          # Keeps the resume file out of the repo
├── index.html          # The whole site: markup, CSS (<style>) and JavaScript (<script>)
├── images/
│   └── headshot.png    # Profile photo shown in the About section
└── README.md
```

There is no build step, framework, or package manager. External dependencies are loaded from CDNs: [Font Awesome 6](https://fontawesome.com/) for icons and Google Fonts (Bricolage Grotesque for headings, Public Sans for body text).

## Running locally

Open `index.html` in a browser, or serve the folder so relative paths behave the same as on GitHub Pages:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Editing the content

Everything lives in `index.html`:

- **Section content**: each section is a `<section id="...">` inside `<main>`. Research projects are `<article>`s, experience entries are `<li>`s in the `.timeline` list, publications are `<li>`s in `.pubs`, and education and skills are rows in a `<dl class="rows">`.
- **Adding a section**: add a `<section id="new-id">` in `<main>` (copy an existing one for the `.wrap` / `.section-head` / `.section-body` structure) and a matching `<li><a href="#new-id">...</a></li>` in the `<nav>`. The active-link highlighting picks it up automatically.
- **Colors and fonts**: CSS custom properties at the top of the `<style>` block (`--ink`, `--accent`, and so on). Dark mode overrides the same variables under `prefers-color-scheme: dark`.
- **Headshot**: replace `images/headshot.png` (keep the filename, or update the `<img src>` in the About section).
- **Icons**: use any Font Awesome 6 class, e.g. `<i class="fas fa-flask" aria-hidden="true"></i>`.

## Deployment

The site is hosted with GitHub Pages from the `main` branch. Pushing to `main` publishes the changes, usually within a minute or two.

```bash
git add .
git commit -m "Describe your change"
git push origin main
```
