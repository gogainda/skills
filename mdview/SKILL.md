---
name: mdview-open-markdown
description: Open or publish Markdown with mdview.io. Use when the user wants to open a local `.md` file from the terminal, publish Markdown and get a share link, open an existing mdview page, fetch raw Markdown, or read shared content as JSON.
---

# Mdview Open Markdown

Use this skill for two mdview flows:

- open a local file in the browser with the `#mvd=zip:` handoff URL
- publish Markdown with `POST /api/public/publish`

## Use the right path

- Local file, immediate browser view:
  use `https://mdview.io/#mvd=zip:<base64-zip-bytes>`
- Markdown text, hosted share:
  use `POST https://mdview.io/api/public/publish`
- Existing share, rendered page:
  use `https://mdview.io/s/:shortId`
- Existing share, raw Markdown:
  use `https://mdview.io/s/:shortId.md`
- Existing share, JSON content:
  use `https://mdview.io/api/shares/:shortId`

## Terminal helpers

Linux:

```bash
mvd() { xdg-open "https://mdview.io/#mvd=zip:$(zip -q -j - "$1" | base64 -w0)"; }
```

macOS:

```bash
mvd() { open "https://mdview.io/#mvd=zip:$(zip -q -j - "$1" | base64)"; }
```

PowerShell:

```powershell
function mvd { param($file); $zip = [System.IO.Path]::GetTempFileName() + ".zip"; Compress-Archive -Path $file -DestinationPath $zip -Force; $b64 = [Convert]::ToBase64String([IO.File]::ReadAllBytes($zip)); Remove-Item $zip; Start-Process "https://mdview.io/#mvd=zip:$b64" }
```

## Publish body

```json
{
  "title": "Optional title",
  "content": "# Markdown",
  "expiresInDays": 7
}
```

`markdown` is accepted as an alias for `content`.

## Rules

- Use terminal handoff for local-file viewing, not hosted sharing.
- Return `shareUrl` or `viewerUrl` for the rendered page.
- Return `markdownUrl` for a raw `.md` link.
- Respect anonymous limits when they matter:
  - 2MB max payload
  - 30-day default expiry
  - 10 publishes per 15 minutes per IP
