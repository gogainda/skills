# karpathy-coding-guidelines

Codex skill for applying Andrej Karpathy-style coding behavior guardrails before and during implementation.

It helps enforce:
- explicit assumptions
- simpler solutions
- surgical diffs
- verifiable success criteria

## Repository Layout

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── karpathy-guidelines.md
```

## Install In Codex

```bash
~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo gogainda/codex-skills \
  --path skills/karpathy-coding-guidelines
```

Restart Codex after install.

## Use In Codex

- `Use $karpathy-coding-guidelines for this task before writing code`
- `Apply $karpathy-coding-guidelines and implement the bugfix`
