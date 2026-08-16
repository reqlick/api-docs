# Reqlick API Docs — CLAUDE.md

## Overview

This repo contains the API documentation for [Reqlick](https://reqlick.com), a platform for managing short links, QR codes, and file-to-link conversions. Docs are built with [Mintlify](https://mintlify.com) and deployed to [docs.reqlick.com](https://docs.reqlick.com).

The OpenAPI spec is fetched live from `https://prod-service.reqlick.com/openapi.json`. Mintlify reads this spec to generate request/response schemas for each endpoint page automatically.

## Repo Structure

```
.
├── mint.json                          # Mintlify config: nav, colors, branding, OpenAPI URL
├── introduction.mdx                   # Landing page — platform overview
├── data-model.mdx                     # Data model overview (Workspaces, Links, Docs, etc.)
├── api-reference/
│   ├── introduction.mdx               # Base URL, auth, response codes
│   └── endpoint/
│       ├── links/                     # 8 endpoints
│       ├── qrcodes/                   # 1 endpoint
│       ├── documents/                 # 7 endpoints
│       ├── workspaces/                # 9 endpoints
│       ├── domains/                   # 5 endpoints
│       ├── subscriptions/             # 1 endpoint
│       └── users/                     # 4 endpoints
├── snippets/                          # Reusable MDX response field definitions
│   ├── link-response.mdx
│   ├── document-response.mdx
│   ├── workspace-response.mdx
│   ├── qrcode-response.mdx
│   ├── domain-response.mdx
│   ├── subscription-response.mdx
│   └── user-response.mdx
└── essentials/                        # Mintlify guide pages (starter kit)
```

## Endpoint File Convention

Every endpoint lives at:
```
api-reference/endpoint/{resource}/{method}/{endpoint-name}/index.mdx
```

Each file uses only frontmatter — Mintlify renders the full interactive page from the OpenAPI spec:

```mdx
---
title: "Human-readable title"
openapi: "METHOD /path/to/endpoint"
description: One-sentence description of what this endpoint does.
---
```

- `title`: Short, action-oriented (e.g., "Create a new link", "Retrieve a list of documents")
- `openapi`: Must exactly match the method and path in the OpenAPI spec at `https://prod-service.reqlick.com/openapi.json`
- `description`: One sentence, plain English, no trailing period inconsistencies

## Snippet Convention

Snippets in `snippets/` are reusable MDX fragments using Mintlify's `<ResponseField>` component:

```mdx
<ResponseField name="fieldName" type="string" required>
  Description of the field.
</ResponseField>
```

They are imported and used in `data-model.mdx` inside `<Accordion>` blocks.

## Navigation

All pages must be registered in `mint.json` under the `navigation` array to appear in the sidebar. Adding a new endpoint file without updating `mint.json` will make it unreachable.

## Local Development

```bash
npm i -g mintlify   # install CLI once
mintlify dev        # preview at localhost:3000
```

## API Details

- **Base URL**: `https://api.reqlick.com`
- **Auth**: `Authorization: Bearer <token>` (tokens from Settings > API Keys)
- **Status**: Currently in beta

## Resources

- Mintlify docs: https://mintlify.com/docs
- Reqlick dashboard: https://app.reqlick.com
- Support: support@reqlick.com
