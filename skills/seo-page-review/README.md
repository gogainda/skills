# seo-page-review

Codex skill for a fast on-page SEO audit of a single URL.

It returns:
- SEO score and verdict
- Critical issues
- Prioritized improvements
- Quick wins
- Short summary

## Repository Layout

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── manual-audit-prompt.md
```

## Install In Codex

### Option 1: Install directly from GitHub (recommended)

```bash
~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo gogainda/codex-skills \
  --path skills/seo-page-review
```

Restart Codex after install.

### Option 2: Manual install

```bash
git clone git@github.com:gogainda/codex-skills.git
mkdir -p ~/.codex/skills
cp -R codex-skills/skills/seo-page-review ~/.codex/skills/seo-page-review
```

Restart Codex after install.

## Use In Codex

Use the skill name in your request:

- `$seo-page-review review https://example.com/blog/post`
- `Use $seo-page-review for https://example.com with target keyword "best crm for startups"`
- `Run $seo-page-review on https://example.com/pricing (landing page)`

Optional inputs:
- target keyword
- page type (`blog`, `landing`, `product`, `docs`)
