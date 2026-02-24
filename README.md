# Content Workflow Demo

Demo repository for the WebOps content workflow pipeline. AI-generated content is validated against schema constraints, committed to a branch, and submitted as a PR with automated CI checks.

## How It Works

1. N8N webhook triggers content generation
2. Claude AI generates a blog post based on `content-spec.json`
3. Content is validated (title length, description length, body word count, slug format)
4. A GitHub PR is created with the new content
5. CI validates that only allowed files were modified
6. Content-only PRs auto-merge if CI passes

## Files

| File | Purpose |
|------|---------|
| `project-schema.yaml` | Defines protected files, modifiable paths, auto-merge rules |
| `content-spec.json` | Blog post spec with field constraints for AI generation |
| `.github/workflows/schema-validation.yml` | CI: diff check + auto-merge for content PRs |
| `src/content/blog/` | Target directory for generated blog posts |
