# skills

Central repository for Codex skills.

This repo is a monorepo so you can keep many skills in one place.

## Structure

```text
.
├── README.md
└── <skill-name>/
    ├── SKILL.md
    ├── agents/
    └── references/ (optional)
```

## Available Skills

| Skill | Purpose | Path |
|---|---|---|
| `seo-page-review` | Basic on-page SEO audit for a URL | `seo-page-review` |
| `karpathy-coding-guidelines` | Coding behavior guardrails for simpler, scoped, verifiable changes | `karpathy-coding-guidelines` |
| `mdview-open-markdown` | Open or publish Markdown with mdview.io | `mdview` |

## Install

Install the published skills collection:

```bash
npx skills add https://github.com/gogainda/skills/tree/main/skills
```

Install a single skill directly from this repo:

### `seo-page-review`

```bash
npx skills add gogainda/skills/seo-page-review
```

### `mdview-open-markdown`

```bash
npx skills add gogainda/skills/mdview
```

### `karpathy-coding-guidelines`

```bash
npx skills add gogainda/skills/karpathy-coding-guidelines
```

## Source Formats

```bash
# GitHub shorthand (owner/repo)
npx skills add gogainda/skills

# GitHub shorthand with path
npx skills add gogainda/skills/mdview

# Full GitHub URL
npx skills add https://github.com/gogainda/skills

# Direct path to a skill in a repo
npx skills add https://github.com/gogainda/skills/tree/main/skills/mdview

# GitLab URL
npx skills add https://gitlab.com/org/repo

# Any git URL
npx skills add git@github.com:gogainda/skills.git

# Local path
npx skills add ./my-local-skills
```

## Use In Codex

Example:

```text
$seo-page-review review https://example.com/blog/post
```

## Add New Skills

1. Create a new folder under `<new-skill-name>/`.
2. Add `SKILL.md` (required).
3. Add `agents/openai.yaml` (recommended).
4. Add `references/` files if needed.
5. Update this `README.md` table.
