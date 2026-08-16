# PR Workflow

Standard workflow for all changes to this repository.

## Branch Creation

Always branch from `main`:

```bash
git checkout main && git pull origin main
git checkout -b feat/your-description   # or fix/ or chore/
```

## Making Changes

- Keep PRs focused — one logical change per PR (e.g., don't mix adding endpoints with updating colors)
- Run `mintlify dev` locally to preview changes before pushing
- Verify new endpoint pages render correctly (check for broken `openapi:` references)

## Commit Messages

Follow conventional commits:

```
feat: add webhooks endpoint documentation
fix: correct path parameter in update-link endpoint
chore: update mintlify config with new social links
docs: improve introduction page clarity
```

## Pull Request Guidelines

**Title**: Short and descriptive, matching the commit message style.

**Description must include**:
- What changed and why
- Which endpoint pages were added/modified (if applicable)
- Whether `mint.json` navigation was updated
- Any verification done against the OpenAPI spec

**PR template**:
```
## Summary
- [What was changed]
- [Why it was changed]

## Endpoints affected
- [List any endpoint .mdx files added or modified]

## Checklist
- [ ] Verified endpoint paths against OpenAPI spec
- [ ] Updated mint.json navigation (if new pages added)
- [ ] Previewed locally with `mintlify dev`
- [ ] No existing pages were removed
```

## Review Requirements

- At least one human review is required before merging
- Agents must not merge their own PRs
- If CI lint/preview checks fail, fix before requesting review

## After Merge

Mintlify auto-deploys from `main` — changes are live at docs.reqlick.com within minutes of merge. No manual deployment step is needed.
