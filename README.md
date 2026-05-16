# EurekaMXZ Blog

[![Deploy-Cloudflare](https://img.shields.io/badge/Deploy-Cloudflare-F38020?logo=cloudflare)](https://pages.cloudflare.com/)

A production-ready personal blog repository built with [Hugo](https://gohugo.io/) and the [DoIt](https://github.com/HEIGE-PCloud/DoIt) theme.

The repository is already wired for direct deployment and routine validation:

- Hugo is configured via `config/_default/hugo.toml`
- The DoIt theme is imported as a Hugo Module

## Overview

This repository is not just raw blog content. It is a fully configured blog workspace that includes:

- site configuration, content structure, and theme integration
- Hugo Module-based dependency management for `hugo-theme-DoIt`
- a reproducible build entrypoint for hosted deployment
- CI validation to catch build regressions before merge or release

## Stack

- [Hugo](https://gohugo.io/) for static site generation
- [DoIt](https://github.com/HEIGE-PCloud/DoIt) for the site theme and presentation layer
- [Cloudflare](https://pages.cloudflare.com/) for deployment and hosting
- [GitHub Actions](https://github.com/features/actions) for build validation

## Included Automation

### Deployment

This repository can be imported into Cloudflare pages and deployed directly without needing to reconstruct the build logic from scratch.

## Local Development

### Requirements

- Git
- Hugo
- Go 1.18 or later for Hugo Modules

### Start the development server

```shell
git clone https://github.com/EurekaMXZ/blog.git
cd blog
hugo mod tidy
hugo serve -D
```

## Production Build

To reproduce the production-style build locally:

```shell
bash ./build.sh
```

The build output is written to `public/`.

## Repository Structure

- `content/`: blog posts and pages
- `config/`: Hugo configuration
- `assets/`: custom assets and overrides
- `archetypes/`: content templates
- `.github/workflows/`: CI workflows

## License

This repository uses different licenses for different types of material.

- Original source code, templates, configuration, and other software-related files authored for this repository are licensed under the [MIT License](LICENSE), unless otherwise noted.
- Original blog post Markdown source files authored for this repository, including files under `content/**`, are licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License (CC-BY-SA-4.0)](LICENSE-DOC), unless otherwise noted.
- Third-party components keep their upstream licenses. In particular, the DoIt theme remains under its own upstream license.
