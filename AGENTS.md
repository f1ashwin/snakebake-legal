# Agent memory — Cursor and Claude, same file

**Canonical.** Cursor loads this via `.cursor/rules/`. Claude Code loads it via `CLAUDE.md`.
After `git pull`, this file beats any prior chat. Update it in the same commit as the work.
Keep it short. Template: https://github.com/f1ashwin/agent-memory
New repos: `gh repo create NAME --template f1ashwin/agent-memory --private`

## This repo

SnakeBake legal copy.

## Pickup

Legal texts for SnakeBake. Confirm what is live on infoash.de vs draft.

## Hard rules — every InfoaSH / f1ashwin repo

1. Never push to `main`. Branch, PR, merge.
2. After any App Store / Play upload, **read the store API back**. A 2xx is not proof.
3. Do not expire old TestFlight until the new build is group-assigned and installable.
4. Do not forge owner sign-offs or rewrite guard tests so a suite goes green.
5. Mac and Windows stay in sync via GitHub. Commit and push before a session ends.
6. Never chase a saturated genre's words in store metadata (Laser Sharp 4.3(a) lesson).
