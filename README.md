# EurekaMXZ Blog

[![Deploy-Cloudflare](https://img.shields.io/badge/Deploy-Cloudflare-F38020?logo=cloudflare)](https://pages.cloudflare.com/)

A personal blog built with [Hugo](https://gohugo.io/) and the [DoIt](https://github.com/HEIGE-PCloud/DoIt) theme.

- Hugo is configured via `config/_default/hugo.toml`
- The DoIt theme is imported as a Hugo Module
- Hugo version is pinned via `.hugo-version` for reproducible Cloudflare Pages builds

## Overview

This repository is a fully configured blog workspace that includes:

- site configuration, content structure, and theme integration
- Hugo Module-based dependency management for the DoIt theme
- Dependabot automation to keep the theme and GitHub Actions up to date
- a scheduled workflow that checks for new Hugo releases and opens update PRs

## Stack

- [Hugo](https://gohugo.io/) for static site generation
- [DoIt](https://github.com/HEIGE-PCloud/DoIt) for the site theme and presentation layer
- [Cloudflare Pages](https://pages.cloudflare.com/) for deployment and hosting
- [Dependabot](https://docs.github.com/en/code-security/dependabot) for automated dependency updates

## Automation

### Dependency Updates

| Dependency | How It's Tracked | Frequency |
|---|---|---|
| DoIt theme | Dependabot (`gomod`) | Weekly (Tuesday 03:00 CST) |
| GitHub Actions | Dependabot (`github-actions`) | Weekly (Tuesday 03:00 CST) |
| Hugo version | `.github/workflows/hugo-version-check.yml` | Weekly (Tuesday 03:00 CST) |

When a Hugo update is detected, the workflow updates `.hugo-version` and opens a PR. Merging the PR causes Cloudflare Pages to use the new Hugo version on the next build.

Dependabot is configured in `.github/dependabot.yml`. Manual update checks can be triggered via `workflow_dispatch` in the Actions tab.

### Deployment

This repository can be imported directly into Cloudflare Pages. The platform reads `.hugo-version` to select the correct Hugo release, installs Hugo Modules via `go mod`, and builds the site with `hugo`.

## Local Development

### Requirements

- Git
- Hugo (use the version in `.hugo-version`)
- Go 1.26+

### Start the development server

```shell
git clone https://github.com/EurekaMXZ/blog.git
cd blog
hugo mod tidy
hugo serve -D
```

## Repository Structure

- `content/`: blog posts and pages
- `config/_default/`: Hugo configuration (site, menus, params, etc.)
- `assets/`: custom CSS and asset overrides
- `archetypes/`: content templates
- `.github/workflows/`: Hugo version check workflow
- `.github/dependabot.yml`: Dependabot configuration

## License

This repository uses different licenses for different types of material.

- Original source code, templates, configuration, and other software-related files authored for this repository are licensed under the [MIT License](LICENSE), unless otherwise noted.
- Original blog post Markdown source files authored for this repository, including files under `content/**`, are licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License (CC-BY-SA-4.0)](LICENSE-DOC), unless otherwise noted.
- Third-party components keep their upstream licenses. In particular, the DoIt theme remains under its own upstream license.
