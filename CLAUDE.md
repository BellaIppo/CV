# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a single-file static HTML CV/portfolio site for Isabella Ippolito, a Pipeline Technical Director. There is no build system, no JavaScript, no package manager, and no test suite.

**To preview:** open `index.html` directly in a browser. The site is deployed to GitHub Pages at `bellaippo.github.io/CV`.

## File structure

- `index.html` — the entire site: all HTML, CSS (inline `<style>` block), and SVG
- `projects/` — static PDF assets linked from the page

## Architecture

**Single file, no JS.** All layout, styling, and SVG decorations live inside `index.html`.

**CSS custom properties** control the entire design system. All colours, spacing, and layout dimensions are defined at the top of the `<style>` block under `:root`:
- `--bg`, `--bg2`, `--bg3` — dark background layers
- `--accent` (`#e85a1e`) and `--border-or` / `--acc-dim` / `--acc-mid` — orange accent variants
- `--text`, `--text-soft`, `--text-muted` — text hierarchy
- `--nav-w: 236px`, `--max: 1210px`, `--radius: 14px` — layout constants

**Layout:** a CSS grid on `.page` with two columns — `.nav` (sticky sidebar, `var(--nav-w)`) and `.main` (content area). Collapses to single-column at 980px; further tightens at 640px.

**Background:** `#tech-bg` is a fixed full-viewport `<svg>` (z-index 0) containing decorative geometric shapes. All page content sits at z-index 1 above it.

**Typography:** DM Serif Display (headings, `.st`, `.mt`, `.tl-h`) + DM Sans (body), both loaded from Google Fonts.

**Repeating patterns:** section titles use `.stw`/`.st` (large, with accent underline pseudo-element), subsection titles use `.mtw`/`.mt`. Timeline entries are `.tl-item` articles. Skill groups use `.sg-head` + `.sg-list`. Tags use `.tag` inside `.tag-row`.
