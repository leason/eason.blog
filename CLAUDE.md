# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal blog (eason.blog) built with **Hugo** static site generator, using a custom fork of the **Aether** theme (git submodule at `themes/aether`). Deployed automatically via **Netlify** on push.

## Common Commands

- **Local dev server**: `hugo server` (serves at localhost:1313)
- **Production build**: `hugo --gc --minify`
- **Preview build** (includes drafts/future): `hugo --gc --minify --buildFuture --buildDrafts`
- **Create new post**: `hugo new posts/YYYY/MM/post-name/index.md`

Hugo version pinned to **0.125.4** in `netlify.toml`.

## Architecture

- **Config**: Multi-environment Hugo config in `config/` — `_default/` for production, `staging/` enables drafts/future posts
- **Content**: Posts live in `content/posts/YYYY/MM/post-slug/index.md` (date-based folder structure)
- **Theme**: `themes/aether/` is a git submodule pointing to `github.com/leason/aether` (personal fork of josephhutch/aether). Theme changes require commits in the submodule repo
- **Layout overrides**: Minimal custom layouts in `layouts/` that override theme defaults
- **Static assets**: Images and favicons in `static/`

## Content Front Matter

Posts use this front matter structure:

```yaml
---
title: "Post Title"
date: 2026-03-22T20:00:00-05:00
description: "Brief description"
displayInMenu: false
displayInList: true
featuredImage: "/posts/YYYY/MM/post-name/image.png"
featuredImageDescription: "Alt text for the image"
categories: ["category1", "category2"]
draft: false
---
```

## Deployment

Netlify auto-deploys on push. Build contexts configured in `netlify.toml`:
- **Production**: full build with git info enabled
- **Deploy preview / Branch deploy**: includes future and draft posts
