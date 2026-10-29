# Agent Skills — SKILL.md packs for AI coding agents (MIT)

Three ready-to-use **agent skills** (`SKILL.md` instruction files) that make AI coding agents such as Claude Code, Cursor or Codex follow a proven workflow for a specific job. Each folder has the `SKILL.md`, an `EXAMPLE.md` showing a real run, and a cover image.

| Skill | What it does |
|---|---|
| [`nextjs-landing-skill`](nextjs-landing-skill/SKILL.md) | One brief in → a Next.js App Router + Tailwind landing page with a spam-protected waitlist API, SEO (OG image, sitemap, JSON-LD), dark mode and a lint+build quality gate. All copy lives in one typed config file. |
| [`roblox-progression-skill`](roblox-progression-skill/SKILL.md) | Exploit-safe, data-loss-safe Roblox progression (daily streaks, rewards, XP, currencies): server authority, server time only, idempotent claims, `UpdateAsync` with retries, `BindToClose` saves, strict Luau, test plan. |
| [`sheets-template-skill`](sheets-template-skill/SKILL.md) | Reproducible, formula-driven Excel / Google Sheets templates with Python openpyxl: summary block, SUMIFS, dropdowns, conditional formatting, print setup, protected formulas, PDF preview and an error check. |

## Why

Generic prompts give generic results. A skill file pins down the stack, the non-negotiables and the quality gate, so the agent produces the same reliable result every time.

## Quickstart

```bash
git clone https://github.com/kensondev/agent-skills.git
# Claude Code (personal skills):
mkdir -p ~/.claude/skills && cp -r agent-skills/nextjs-landing-skill ~/.claude/skills/
# Project-level: copy a folder into .claude/skills/ (or your agent's skills/rules folder)
```

For agents without native skill support, paste the contents of `SKILL.md` into your system prompt or rules file, then ask for the task (e.g. "build a landing page for my app").

## Built with AI assistance

This project was written with the help of AI coding assistants and then reviewed and tested by the maintainer. Please review the code before using it in production, and open an issue if you find a problem.

## Support this project

This project is free and MIT-licensed. If it saved you time, an optional tip is appreciated and helps keep it maintained.

- **Solana (SOL or USDC on Solana):** `Cx9qsVknF5FYB2sS925zssK6GeiHBSy5gzwss8MxS3wp`
- Pay link (SOL): [`solana:Cx9qsVknF5FYB2sS925zssK6GeiHBSy5gzwss8MxS3wp?label=kensondev&message=Thanks`](solana:Cx9qsVknF5FYB2sS925zssK6GeiHBSy5gzwss8MxS3wp?label=kensondev&message=Thanks)
- Pay link (USDC): [`solana:Cx9qsVknF5FYB2sS925zssK6GeiHBSy5gzwss8MxS3wp?spl-token=EPjFWdd5AufqSSqeM2qN1xyybapC8G4wEGGkZwyTDt1v&label=kensondev`](solana:Cx9qsVknF5FYB2sS925zssK6GeiHBSy5gzwss8MxS3wp?spl-token=EPjFWdd5AufqSSqeM2qN1xyybapC8G4wEGGkZwyTDt1v&label=kensondev)

Please only send SOL or Solana-network USDC to this address. Tips are voluntary and do not buy support, priority or any license rights.

## License

[MIT](./LICENSE) © 2026 Kenson (kensondev)
