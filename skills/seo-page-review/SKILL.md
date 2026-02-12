---
name: seo-page-review
description: Evaluate a webpage for basic SEO quality and produce a concise, actionable audit report. Use when auditing blog posts, landing pages, product pages, or pre-publish drafts for on-page SEO fundamentals, including indexability, metadata quality, heading hierarchy, canonical consistency, structured data, social preview tags, content depth, and crawl infrastructure.
---

# SEO Basic Page Review

## Workflow

1. Collect inputs.
- Request the page URL.
- Request optional target keyword and page type (blog, landing, product, docs).

2. Verify accessibility and indexability first.
- Check HTTP status and final URL after redirects.
- Verify HTTPS usage.
- Detect `noindex` in meta robots or `X-Robots-Tag`.
- Detect likely crawl blocks (robots disallow, auth wall, broken response).
- Stop and report blockers first when the page is not indexable.

3. Evaluate core on-page elements in fixed order.
- Title tag quality.
- Meta description quality.
- Heading hierarchy.
- Canonical tag validity.
- Structured data presence and relevance.
- Open Graph and Twitter tags.
- Content depth and intent coverage.
- `robots.txt` and `sitemap.xml` availability.

4. Score and prioritize findings.
- Apply the optional 20-point score model.
- Separate critical issues from non-critical improvements.
- Distinguish measured facts from recommendations.

5. Return the report in the required output structure.

## Prompt Templates

- Use `references/manual-audit-prompt.md` when a user asks for a reusable prompt they can paste into another LLM for a one-off SEO audit.
- Keep the final report structure unchanged from this skill.

## Evaluation Criteria

### 1) Indexability and Accessibility (Critical)
Check:
- HTTP status (`200` expected).
- HTTPS enabled.
- `noindex` directives.
- Crawlability signals.

Mark as critical when:
- `noindex` is present.
- HTTP errors block access.
- Crawl blocks likely prevent indexing.

### 2) Title Tag Quality
Check:
- Length target: 50-60 characters.
- Relevance to page topic and intent.
- Clarity and specificity.
- Low truncation risk.
- No keyword stuffing.

Red flags:
- Shorter than 30 characters.
- Longer than 65 characters.
- Generic titles such as "Home".
- Obvious duplicate-title pattern risk.

### 3) Meta Description Quality
Check:
- Length target: 50-160 characters.
- Compelling, accurate summary.
- Distinct wording from title.

Red flags:
- Extremely short descriptions.
- Vague or generic copy.
- Exact duplication of the title.

Note:
- Treat meta description as CTR optimization, not a direct ranking factor.

### 4) Heading Structure (Semantic Hierarchy)
Check:
- Exactly one meaningful `H1`.
- `H1` matches primary topic.
- Logical `H2`/`H3` structure.
- Content headings dominate over nav boilerplate.

Red flags:
- Missing `H1`.
- `H1` is only brand/site name.
- Multiple unrelated `H1` values.
- Skipped hierarchy (for example `H1` directly to `H3`).

### 5) Canonical Tag
Check:
- Presence of `<link rel="canonical">`.
- Canonical URL validity.
- Alignment with preferred URL.

Prioritize for:
- Blog posts.
- Pagination variants.
- Query-parameter pages.

### 6) Structured Data (Schema.org / JSON-LD)
Check for page-type-appropriate schema.

For blog/article pages, verify:
- `Article` or `BlogPosting`.
- `headline`.
- `author`.
- `datePublished`.
- Publisher/organization identity.

### 7) Social Preview Tags (OG / Twitter)
Check:
- `og:title`
- `og:description`
- `og:image`
- `twitter:card`
- `twitter:image`

Treat missing tags as share-preview and CTR weaknesses.

### 8) Content Depth
Check:
- Approximate word count.
- Intent coverage and completeness.
- Thin-content signals.

Guidance:
- Under 300 words is often thin for informational pages.
- 800+ words is often suitable for many blog topics when quality is strong.
- Avoid intent or quality claims without direct evidence.

### 9) Crawl Infrastructure
Check:
- `robots.txt` accessibility.
- `sitemap.xml` accessibility.

Treat failures as crawl/discovery inefficiencies.

## Optional Scoring Model (20 Points)

- Technical access: 4
- Title and description: 4
- Headings: 2
- Canonical: 2
- Structured data: 2
- Social tags: 3
- Content depth: 2
- Crawl files: 1

Verdict mapping:
- 17-20: Excellent
- 14-16: Good
- 10-13: Fair
- Under 10: Needs Improvement

## Output Format

Return sections in this order:

1. `SEO Score`: Numeric score and verdict.
2. `Critical Issues`: Bullet list of blockers/high-severity findings.
3. `Improvements`: Bullet list of prioritized recommendations.
4. `Quick Wins`: Short, high-impact fixes.
5. `Summary`: 1-2 sentence executive overview.

## Behavioral Rules

- Report only verifiable, page-level facts.
- Avoid speculative penalty or traffic claims.
- Prioritize critical issues before minor optimizations.
- Keep recommendations specific and actionable.
- Keep tone concise and professional.
- Separate observed facts from suggestions.

## Do Not

- Assume Google penalties.
- Hallucinate missing tags or values.
- Invent traffic impact claims.
- Overstate minor positives.
- Write long SEO tutorials when an audit is requested.

## Typical Triggers

- "Review this page for SEO basics."
- "Audit this landing page before publishing."
- "Give me quick SEO fixes for this blog post."
- "Run a basic on-page SEO QA."
