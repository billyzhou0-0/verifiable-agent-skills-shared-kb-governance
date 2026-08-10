# Shared Knowledge-Base Governance（AI 共享知识库治理体系）

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/billyzhou0-0/verifiable-agent-skills-shared-kb-governance.svg)](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/stargazers)

**Governance for a knowledge base shared by multiple AI agents and one human — directory contracts, naming rules, flow rules, sync obligations, and evidence discipline. Machine-checked, because written rules are not enforcement.**
**多个 AI 与一个人共享一个知识库时的治理体系——目录分工、命名规矩、流转规则、联动同步义务、证据纪律。机器自动检查，因为写在纸上的规矩不算强制。**

When several AI agents (Hermes, Codex, Claude, Gemini) plus a human all read and write one Obsidian/Markdown knowledge base, chaos is the default: files land in the wrong place, names mean nothing, "done" claims don't match reality, and the human has to re-explain everything. This methodology is the operating system for that shared space. Proven over months of daily multi-agent operation.
当多个 AI Agent（Hermes/Codex/Claude/Gemini…）加一个人共同读写一个 Obsidian/Markdown 知识库时，混乱是默认状态：文件落错位、命名无意义、"完成"声称与事实不符、人类被迫重复解释。本方法论就是这个共享空间的"操作系统"，已在数月日常多 Agent 运行中验证。

## Why this exists（为什么做这个）

One human + several AI agents + one shared knowledge base = chaos by default: files land in the wrong place, names mean nothing, sync never happens, and "done" claims don't match reality.
一个人 + 多个 AI + 一个共享知识库 = 默认混乱：文件放错地方、名字毫无意义、同步永远没人做、"做完了"的声称对不上现实。

This governance is the operating system for that shared space — directory contracts, naming rules, flow rules, sync obligations, and evidence discipline. And the rules are machine-checked on every commit, because written rules are not enforcement.
本治理体系就是这个共享空间的操作系统——目录分工、命名规矩、流转规则、同步义务、证据纪律。而且规矩由机器在每次提交时自动检查——因为写在纸上的规矩不算强制。

## The core insight（核心洞察）

**Rules written in files are not enforcement** — agents don't reliably read them, and compression makes them forget. So this governance is designed as:
**写在文件里的规矩 ≠ 强制**——AI 不主动读文件，压缩后更忘。因此本治理按三层设计：

1. **Single source of truth / 单一事实源** — one "must-read card" at the top of the shared AGENTS.md + one mirror in the always-injected system prompt. Detailed rules live in ONE referenced file (updated in one place), the injection layer carries only pointers + non-codeable core rules. 共享 AGENTS.md 顶部一张"必读卡" + 每次会话自动注入的系统提示词镜像。细则放一个承接文件（常更新只改一处），注入层只留指针 + 不可代码化核心。
2. **Machine-checked / 机器检查** — a zero-cost health-check script + git pre-commit hook verify naming, sync, sensitive info, frontmatter, and transcript coverage on every commit. 零成本体检脚本 + git 提交前钩子，每次提交验证命名/同步/敏感/frontmatter/凭证转录。
3. **Flow rules with clear states / 落位规则** — every artifact has exactly one home depending on its state. 每个产物按状态恰好有一个家。

## Directory contract（目录分工契约——什么放哪里）

| Directory（目录） | What goes in（放什么） | What does NOT（不放什么） |
|---|---|---|
| 收件箱 (inbox) | Produced work, not yet reviewed by the user (one file per task)<br>已产出、用户尚未验收的过程性文件（一任务一文件） | Verified/accepted work<br>已验收成果 |
| ai暂存 (ai staging) | Tasks mentioned in conversation, per AI (one file per AI)<br>对话中提到过的任何任务（一 AI 一文件） | User decisions<br>用户决策 |
| 待办 (todo) | Only what the user explicitly asked to be tracked/passed on<br>只有用户明确要求才放 | AI's own work<br>AI 自己的活 |
| 归档 (archive) | Frozen history — never modified<br>冻结历史——永不修改 | Active work<br>活跃内容 |
| 领域知识/工作流/工具/项目 | Formal knowledge by domain<br>按领域的正式知识 | Unreviewed output<br>未验收产出 |

**Flow rule / 流转回写** — when a file moves between inbox / staging / todo, the source file gets an appended line `✅ 已转交至<目标>（<AI名> <日期>）` — traceable provenance, always. 文件在收件箱/ai暂存/待办之间流转时，来源文件内部追加一行"✅ 已转交至…"——永远可追溯。

## Naming rules（命名规矩）

- File name format: `<AI名>-<事项>-<日期><（N）>.md` — **date ALWAYS at the end** (unconditional, even for user-created files; archive layer exempt as frozen history). / 文件名格式：`<AI名>-<事项>-<日期><（N）>.md`——**日期一律放末尾**（无条件；归档层豁免=冻结历史）。
- 事项 = plain-language "what this is" — no technical identifiers (agent_id, SQLite, frontmatter…) in the name; those go in frontmatter or body. / 事项 = 单纯事项名，不塞技术标识；技术标识放 frontmatter 或正文。
- Multiple outputs same day same AI: append （1）（2）…（N）with no dash before the paren. / 同一日期同一 AI 多份产出：末尾标（1）（2）…（N），（N）前无连字符。
- **AI 名 (nickname) is given by the user** — it's the role nickname, not the model name. Register nicknames in one index file; when unsure, ask. / **AI 名 = 用户给的角色昵称**，不是模型名；昵称登记表一文件；不确定就问用户。

## Sync obligation（联动同步铁律——不可谈判）

Any file/path/structure change MUST be propagated to every related reference — registry, tool index, manuals, INDEX, cross-references — **immediately, without asking "should I update?"**. Linking updates are a duty, not a choice. Verified by grep checks in the health-check script.
任何文件/路径/结构改动必须**立即**全库同步所有相关引用（登记册/索引/说明书/INDEX/交叉引用）——**不允许问"要不要更新"**。联动更新是义务不是选项。体检脚本 grep 验证。

## Identity & evidence discipline（身份与证据纪律）

- Every document carries `创建人：<AI名> <日期>` and an appended `修改人：<AI名> <日期>` line for each modification. / 每个文档带"创建人：AI名 日期"和每次修改追加的"修改人"行。
- **Attribution by session, not by vibes** — before claiming "I did X", check the conversation database's session ownership. "The file was created by X" is factual; "I created it" requires the session evidence. / **归属按会话证据，不凭感觉**——说"是我做的"前先查会话归属。"文件创建人是 X"是事实；"我创建的"需要会话证据。
- **"已落地/已完成" claims require verifiable evidence** (git commit hash / file path / script output) — applicable to any task, any reply. / **"已落地/已完成"的声称必须附可验证证据**（git 提交号/文件路径/脚本输出）——适用于任何任务。
- **Full-transcript discipline / 全量转录** — user's words, AI replies, and sub-agent conversations are transcribed verbatim into the raw-evidence archive — append-only, never overwritten. 用户原话、AI 回复、子 agent 对话全部逐字转录入原始凭证档案——只增量追加，绝不覆盖。

## Sensitive-information rule（敏感信息规矩——判断权在用户）

API keys / tokens / passwords / customer data are **not written by default**. When something looks sensitive, STOP and ask the user — explain the pros and cons — and only write after explicit consent. No reply = keep asking, don't proceed. The AI never self-judges what is sensitive (AI misjudges both ways: treating examples as real, or treating real keys as harmless).
API Key/Token/密码/客户资料**默认不写入**。遇疑似敏感内容必须停下问用户，说明利弊，用户明确同意才写；不回复=反复问，不擅自继续。AI 不自行判断是否敏感（AI 易双向误判）。

## Audits are immutable（审计不可变）

Audit reports are never edited (not just historical ones). Non-substantive changes to an in-progress audit require discussion with the user first. 声称落地必验 applies to every task: any "landed" claim is programmatically scanned before it enters a report.
审计报告一律不改（不止历史几份）；进行中审计如需非实质性修改，先与用户商议。"声称落地必验"适用于任何任务。

## Files（文件）

- `SKILL.md` — the full governance methodology（完整治理方法论，中文）.
- `LICENSE` — MIT.

## Related（相关）

- [verifiable-agent-skills-ai-rule-enforcement](../verifiable-agent-skills-ai-rule-enforcement) — the machine-enforcement layer (health-check script + pre-commit hook). 强制层：体检脚本+提交前钩子。
- Hub: [verifiable-agent-skills](../verifiable-agent-skills). 主仓库：[verifiable-agent-skills](../verifiable-agent-skills)。
