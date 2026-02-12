# codex-skills

Central repository for Codex skills.

This repo is a monorepo so you can keep many skills in one place.

## Structure

```text
.
├── README.md
└── skills/
    └── <skill-name>/
        ├── SKILL.md
        ├── agents/
        └── references/ (optional)
```

## Available Skills

| Skill | Purpose | Path |
|---|---|---|
| `seo-page-review` | Basic on-page SEO audit for a URL | `skills/seo-page-review` |

## Install A Skill In Codex

Install a specific skill from this repo:

```bash
~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo gogainda/codex-skills \
  --path skills/seo-page-review
```

Restart Codex after install.

## Use In Codex

Example:

```text
$seo-page-review review https://example.com/blog/post
```

## Add New Skills

1. Create a new folder under `skills/<new-skill-name>/`.
2. Add `SKILL.md` (required).
3. Add `agents/openai.yaml` (recommended).
4. Add `references/` files if needed.
5. Update this `README.md` table.
