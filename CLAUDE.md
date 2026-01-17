# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Oblivion Emacs is an Emacs color theme ported from the Gedit Oblivion theme by Paolo Borelli. It uses the legacy `color-theme` package (version 6.6.1, vendored in repo).

## Repository Structure

- `color-theme-oblivion.el` - The theme implementation (edit this file)
- `color-theme.el` - Vendored dependency, do not modify

## Development Workflow

There is no build system, test suite, or linting. Development is:
1. Edit `color-theme-oblivion.el`
2. Load in Emacs: `M-x load-file RET color-theme-oblivion.el RET`
3. Apply theme: `M-x color-theme-oblivion RET`
4. Visually verify changes

## Color Palette

The theme uses GNOME 2 standard palette colors defined as variables at the top of `color-theme-oblivion.el`:
- **butter1-3**: Yellows (strings, highlights)
- **chameleon1-3**: Greens (types, variables)
- **orange1-3**: Oranges (warnings)
- **skyblue1-3**: Blues (functions, builtins)
- **plum1-3**: Purples (keywords)
- **chocolate1-3**: Browns
- **scarletred1-3**: Reds (errors, constants)
- **aluminium1-6**: Grays (1=lightest, 6=darkest background)
- **dark-red, dark-yellow, dark-magenta**: Dark background accents for error/warning highlighting

## Theme Architecture

The theme defines faces in three categories:
1. **Base faces** (`strong-face`, `warning-face`, `error-face`) - Other faces inherit from these
2. **Core Emacs faces** (default, cursor, region, font-lock-*, etc.)
3. **Mode-specific faces** (auto-complete, diff, eshell, flymake, flyspell, ido, js2, magit, nxml, css, mumamo, show-paren)

When adding support for a new mode, follow the existing pattern and use color variables rather than hardcoded hex values.
