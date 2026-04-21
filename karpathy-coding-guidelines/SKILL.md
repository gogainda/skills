---
name: karpathy-coding-guidelines
description: Apply pragmatic coding behavior guidelines to reduce common LLM implementation mistakes. Use when writing or modifying code to keep changes simple, scoped, and verifiable.
---

# Karpathy Coding Guidelines

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them and do not choose silently.
- If a simpler approach exists, say so.
- If something is unclear, stop and ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- Do not add features beyond what was requested.
- Do not introduce abstractions for single-use code.
- Do not add configurability that was not requested.
- Do not add error handling for impossible scenarios.
- If a change is too large for the need, simplify it.

Ask: "Would a senior engineer consider this overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Do not "improve" unrelated adjacent code, comments, or formatting.
- Do not refactor code that is not part of the request.
- Match existing project style.
- If unrelated dead code is found, mention it and do not remove it unless asked.

When your own changes create unused code:
- Remove imports, variables, or functions made unused by your change.
- Do not remove pre-existing dead code unless asked.

Test: every changed line should trace directly to the request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Turn requests into verifiable goals:
- "Add validation" -> "Write tests for invalid inputs, then make them pass."
- "Fix the bug" -> "Write a test that reproduces it, then make it pass."
- "Refactor X" -> "Ensure tests pass before and after."

For multi-step work, use:
```text
1. [Step] -> verify: [check]
2. [Step] -> verify: [check]
3. [Step] -> verify: [check]
```

Strong criteria enable independent iteration. Weak criteria require repeated clarification.

## Working Signal

These guidelines are working when you see fewer unnecessary diff lines, fewer rewrites due to overcomplication, and more clarifications before implementation.
