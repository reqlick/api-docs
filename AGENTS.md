# AGENTS.md — Reqlick API Docs

Guidelines for AI agents working in this documentation repository.

## Scope

This is a **documentation-only** repo. There is no application code here. All changes are `.mdx` files, `mint.json`, or assets. The actual API is defined by the OpenAPI spec at `https://prod-service.reqlick.com/openapi.json` — agents must never invent or modify endpoint definitions.

## Primary Goals

1. **Accuracy** — docs must reflect the real API exactly
2. **Clarity** — writing should be concise and developer-friendly
3. **Completeness** — every endpoint in the OpenAPI spec should have a corresponding page registered in `mint.json`

## What Agents May Do

- Add new endpoint pages (`.mdx` files) for endpoints that exist in the OpenAPI spec
- Update `title` or `description` frontmatter for clarity
- Fix typos, grammar, or formatting in prose pages (`introduction.mdx`, `data-model.mdx`, etc.)
- Update `snippets/` files to reflect accurate response field definitions
- Add or reorder navigation entries in `mint.json`
- Update branding/config in `mint.json` (colors, links, social handles)

## What Agents Must NOT Do

- **Invent endpoint paths** — the `openapi:` field in frontmatter must match the real spec
- **Remove existing endpoint pages** without explicit human approval
- **Remove navigation entries** from `mint.json` without explicit human approval
- **Modify the `openapi` URL** in `mint.json` (`https://prod-service.reqlick.com/openapi.json`)
- **Push directly to `main`** — all changes must go through a PR
- **Create pages for endpoints that don't exist** in the OpenAPI spec

## Endpoint Page Format

Every endpoint page must follow this exact format:

```mdx
---
title: "Action-oriented title"
openapi: "METHOD /exact/path/from/spec"
description: One sentence describing what this endpoint does.
---
```

No additional content is needed — Mintlify generates the full interactive page from the spec.

## Verifying Against the OpenAPI Spec

Before adding or editing an endpoint page, verify the method and path against the live spec:

```bash
curl https://prod-service.reqlick.com/openapi.json | jq '.paths | keys'
```

## Content Quality Standards

- Titles: imperative verb phrases ("Create a new link", "Retrieve all documents")
- Descriptions: single sentence, no trailing period required, no jargon
- Snippet fields: match exact field names from the API response; include `required` attribute where appropriate
- Navigation labels in `mint.json` must match the `title` in the page's frontmatter

## Branch and PR Conventions

See `.claude/rules/agent-safety.md` and `.claude/rules/pr-workflow.md`.
