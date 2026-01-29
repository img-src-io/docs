# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Mintlify documentation site for [img-src](https://img-src.io), deployed at [docs.img-src.io](https://docs.img-src.io). This is a subdirectory of the main img-src monorepo — see the parent `CLAUDE.md` for full project context.

## Commands

```bash
# Install Mintlify CLI (one-time)
npm i -g mintlify

# Start local dev server (http://localhost:3000)
mintlify dev
```

Deployment is automatic via Mintlify on push — no manual deploy step.

## Architecture

### Configuration

- **`docs.json`** — Mintlify configuration: navigation structure, theme colors, OpenAPI spec path, API base URL, auth method (bearer), navbar, footer
- **`api-reference/openapi.json`** — OpenAPI 3.1.0 spec (source of truth for API reference pages). This file is shared with the parent project's `api/openapi.json`

### Content Structure

All content pages are `.mdx` (Markdown + JSX).

| Directory | Purpose |
|-----------|---------|
| Root (`*.mdx`) | Landing pages: `introduction.mdx`, `quickstart.mdx` |
| `api-reference/` | API endpoint docs organized by resource (`images/`, `settings/`, `presets/`, `usage/`) |
| `guides/` | How-to guides: authentication, image-transformation, presets |
| `sdk/` | SDK docs per language: TypeScript, Python, Go, Rust |
| `examples/` | Framework integration examples: React, Next.js, HTML, Go, Rust |

### Navigation

Two tabs defined in `docs.json`:
1. **Documentation** — Getting Started, Guides, SDKs, Examples
2. **API Reference** — Overview, Images, Settings, Presets (Pro), Usage

Adding or reordering pages requires updating the `navigation.tabs` array in `docs.json`.

## Content Conventions

### Page Frontmatter

Every `.mdx` file starts with:
```mdx
---
title: "Page Title"
description: "Brief description for SEO"
---
```

API reference pages additionally include:
```mdx
---
api: "METHOD /api/v1/endpoint"
---
```

### Mintlify Components Used

- `<CodeGroup>` — Multi-language code examples (cURL, TypeScript, Python, Go, Rust)
- `<CardGroup cols={2}>` / `<Card>` — Feature cards with icons and links
- `<Info>`, `<Warning>`, `<Tip>`, `<Note>` — Callout blocks
- `<AccordionGroup>` / `<Accordion>` — Expandable sections
- `<RequestExample>` / `<ResponseExample>` — API request/response pairs

### Multi-Language Pattern

SDK and example pages consistently show code in all supported languages. When adding new examples, provide snippets for TypeScript, Python, Go, and Rust (in that order).

### Pro Features

Features restricted to Pro plan are marked with "(Pro)" in navigation group names and called out with `<Info>` blocks in content.
