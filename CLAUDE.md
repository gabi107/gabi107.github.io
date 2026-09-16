# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal portfolio for Gabriela Theis Marchan, served by GitHub Pages from `main` at https://gabi107.github.io. There is no build, lint, or test tooling and no package manager: pushing to `main` deploys.

Preview locally with `python -m http.server 8000` from the repo root (or open `index.html` directly).

The site content is derived from the owner's resume, `Gabriela_Theis_Marchan_Resume.docx`, which sits in the repo folder but is gitignored. Never commit it. When asked to update the site from the resume, extract its text (e.g. unzip `word/document.xml`; publication URLs are in `word/_rels/document.xml.rels`).

## Architecture

The entire site is `index.html`: CSS in a `<style>` block in `<head>`, markup in `<body>`, and a small `<script>` at the end. The only other asset is `images/headshot.png`. Font Awesome 6 (icons) and Google Fonts (Bricolage Grotesque for headings, Public Sans for body text) load from CDNs.

**Single scrolling page.** A sticky `<nav>` links to `<section id="...">` blocks in `<main>` (`about`, `research`, `experience`, `publications`, `education`, `skills`). The script uses an `IntersectionObserver` to set `aria-current="true"` on the nav link for the section in view, which the CSS styles as active. Any nav `href="#id"` with a matching section is picked up automatically. On phones the nav list scrolls sideways and the script keeps the active link visible.

**Layout conventions.** Each section is `.wrap` > `.section-head` (h2 plus optional `.intro`) + `.section-body`. On desktop, `.section-body` is offset by `margin-left: 16rem` to align with the intro column (14rem heading column + 2rem gap), so changing one of those values means changing the others. Responsive overrides are in two media queries (860px and 560px) at the end of the stylesheet.

**Theming.** All colors are CSS custom properties on `:root`, redefined under `prefers-color-scheme: dark`. Use the variables rather than hard-coded colors so dark mode keeps working.

**Hero molecule.** The header SVG draws a surfactant as a graph (grey tail nodes in air, accent head-group nodes in water). Tail nodes carry `--i` (sweep order) and `--r` (radius) inline custom properties for a one-time CSS animation. All animation is disabled under `prefers-reduced-motion`.
