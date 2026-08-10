# Shared Knowledge-Base Governance（AI 共享知识库治理体系）

**Governance for a knowledge base shared by multiple AI agents and one human — directory contracts, naming rules, flow rules, sync obligations, and evidence discipline. Proven over months of daily multi-agent operation.**

When several AI agents (Hermes, Codex, Claude, Gemini) plus a human all read and write one Obsidian/Markdown knowledge base, chaos is the default: files land in the wrong place, names mean nothing, "done" claims don't match reality, and the human has to re-explain everything. This methodology is the operating system for that shared space.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/billyzhou0-0/verifiable-agent-skills-shared-kb-governance.svg)](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/stargazers)
## Why this exists（为什么做这个）

One human + several AI agents + one shared knowledge base = chaos by default: files land in the wrong place, names mean nothing, sync never happens, and "done" claims don't match reality.

This governance is the operating system for that shared space — directory contracts, naming rules, flow rules, sync obligations, and evidence discipline. And the rules are machine-checked on every commit, because written rules are not enforcement.

## The core insight

**Rules written in files are not enforcement** — agents don't reliably read them, and compression makes them forget. So this governance is designed as:

1. **Single source of truth**: one "must-read card" at the top of the shared AGENTS.md + one mirror in the always-injected system prompt. Detailed rules live in ONE referenced file (updated in one place), the injection layer carries only pointers + non-codeable core rules.
2. **Machine-checked**: a zero-token health-check script + git pre-commit hook (see the sibling repo [verifiable-agent-skills-ai-rule-enforcement](../verifiable-agent-skills-ai-rule-enforcement)) verify naming, sync, sensitive info, frontmatter, and transcript coverage on every commit.
3. **Flow rules with state machines**: every artifact has exactly one home depending on its state — see below.

## Directory contract (what lives where)

| Directory | What goes in | What does NOT |
|---|---|---|
| 收件箱 (inbox) | Produced work, not yet reviewed by the user (one file per task) | Verified/accepted work |
| ai暂存 (ai staging) | Tasks mentioned in conversation, per AI (one file per AI) | User decisions |
| 待办 (todo) | Only what the user explicitly asked to be tracked/passed on | AI's own work |
| 归档 (archive) | Frozen history — never modified | Active work |
| 领域知识 / 工作流 / 工具 / 项目 | Formal knowledge by domain | Unreviewed output |

**Flow rule**: when a file moves between inbox / staging / todo, the source file gets an appended line `✅ 已转交至<目标>（<AI名> <日期>）` — traceable provenance, always.

## Naming rules

- File name format: `<AI名>-<事项>-<日期><（N）>.md` — **date ALWAYS at the end** (unconditional, even for user-created files; archive layer exempt as frozen history).
- 事项 = plain-language "what this is" — no technical identifiers (agent_id, SQLite, frontmatter…) in the name; those go in frontmatter or body.
- Multiple outputs same day same AI: append （1）（2）…（N）with no dash before the paren.
- Directory names must say what they really are (no "工具与环境" that means "工具"); dedicated tools get （xx专用）markers.
- **AI 名 (nickname) is given by the user** — it's the role nickname (e.g. "记忆知识库管理"), not the model name. Register nicknames in one index file; when unsure, ask the user "what is my name?".

## Sync obligation (the non-negotiable one)

Any file/path/structure change MUST be propagated to every related reference — registry, tool index, manuals, INDEX, cross-references — **immediately, without asking "should I update?"**. Linking updates are a duty, not a choice. Verified by grep checks in the health-check script.

## Identity & evidence discipline

- Every document carries `创建人：<AI名> <日期>` and an appended `修改人：<AI名> <日期>` line for each modification (or maintained created_by/last_updated_by fields).
- **Attribution by session, not by vibes**: before claiming "I did X", check the conversation database's session ownership. A statement like "the file was created by X" is factual; "I created it" requires the session evidence.
- **"已落地/已完成" claims require verifiable evidence** (git commit hash / file path / script output) — applicable to any task, any reply.
- **Full-transcript discipline**: user's words, AI replies, and sub-agent conversations are transcribed verbatim into the 对话原始凭证 (raw evidence) archive — append-only, incremental, never overwritten. Before starting a formal task, write the user's latest words into the archive first, then backfill gaps.

## Sensitive-information rule (human decides)

API keys / tokens / passwords / customer data are **not written by default**. When something looks sensitive, STOP and ask the user — explain the pros and cons of writing vs not writing — and only write after explicit consent. No reply = keep asking, don't proceed. The AI never self-judges what is sensitive (AI misjudges both ways: treating examples as real, or treating real keys as harmless).

## Audits are immutable

Audit reports are never edited (not just historical ones). Non-substantive changes to an in-progress audit require discussion with the user first. 声称落地必验 applies to every task: any "landed" claim is programmatically scanned before it enters a report.

## Files

- `SKILL.md` — the full governance methodology (Chinese).
- `LICENSE` — MIT.

## Related

- [verifiable-agent-skills-ai-rule-enforcement](../verifiable-agent-skills-ai-rule-enforcement) — the machine-enforcement layer (health-check script + pre-commit hook).
- Hub: [verifiable-agent-skills](../verifiable-agent-skills).
