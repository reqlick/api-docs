# Agent Safety Rules

These rules apply to all AI agents (Claude Code and any automated pipelines) working in this repository.

## Branch Protection

- **NEVER push directly to `main`** — the `main` branch is protected and deploys automatically to production (docs.reqlick.com)
- All changes must be made on a feature branch and submitted via pull request
- Branch naming convention:
  - `feat/` — new endpoint pages, new sections, new features
  - `fix/` — correcting inaccurate content, broken links, typos
  - `chore/` — config changes, tooling, CI/CD, non-content updates
- Examples: `feat/add-webhooks-endpoints`, `fix/update-link-response-fields`, `chore/update-mintlify-config`

## API Endpoint Rules

- **Never modify the `openapi:` field** in an endpoint `.mdx` file unless you have verified the new path exists in the live OpenAPI spec at `https://prod-service.reqlick.com/openapi.json`
- **Never add an endpoint page** for a path that does not exist in the OpenAPI spec
- **Never change the `openapi` URL** in `mint.json` — it points to the production spec

## Documentation Preservation

- **Never delete existing endpoint pages** without explicit human approval in a PR review
- **Never remove navigation entries** from `mint.json` without explicit human approval
- **Never remove snippets** from `snippets/` without verifying they are not imported anywhere

## Verification Before Editing

Before making changes to endpoint frontmatter, verify:
1. The HTTP method matches the spec
2. The path (including path parameters like `{id}`, `{workspace}`) matches the spec exactly
3. The endpoint is included in `mint.json` navigation if adding a new page

## Secrets and Credentials

- This repo contains no secrets or credentials
- Do not add API keys, tokens, or any credentials to any file
- Do not hardcode example tokens in documentation — use placeholder syntax like `<Your-Token>`
