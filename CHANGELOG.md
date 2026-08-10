# Changelog（更新记录）

All notable changes to this project are documented here, following Keep a Changelog with semver versioning. / 本文件按 Keep a Changelog 规范记录本项目所有重要变更。

## [1.1.1] - 2026-08-11

### Patch Changes / 补丁

- [`5f322c2`](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/commit/5f322c2) Add `CHANGELOG.md` and `CONTRIBUTING.md`; add an **Example usage（使用示例）** section to `SKILL.md` (scenario → steps → expected output). / 添加更新记录与贡献指南；SKILL.md 新增使用示例（场景→步骤→输出）。

## [1.1.0] - 2026-08-11

### Minor Changes / 次要版本：发布打磨（Release polish）

- [`fcb1f9c`](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/commit/fcb1f9c), [`79f4555`](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/commit/79f4555) — README overhaul: / README 改造：
  - Description rewritten pain-point-first (EN+CN) / 描述痛点驱动（双语）
  - Topics tags added / 添加 Topics 标签
  - License + Stars badges / License 和 Stars 徽章
  - 'Why this exists' pain-point story / '为什么做这个'痛点故事
  - README fully bilingual (native-level EN + CN, every paragraph and table cell) / README 全面中英双语

## [1.0.0] - 2026-08-11

### Initial open-source release / 初始开源发布

- [`a8f5776`](https://github.com/billyzhou0-0/verifiable-agent-skills-shared-kb-governance/commit/a8f5776) — Initial release. / 初始发布。

- **Directory contract / 目录分工契约** — inbox (produced, unreviewed) / ai-staging (mentioned tasks, one file per AI) / todo (user-explicit only) / archive (frozen) / domain directories; flow rule: every transfer appends '✅ 已转交至<目标>' to the source file. 收件箱/ai暂存/待办/归档/领域目录分工；流转回写「✅ 已转交」。
- **Naming rules / 命名规矩** — `<AI名>-<事项>-<日期><（N）>.md`, date ALWAYS at the end (unconditional), AI nickname given by the user, no technical identifiers in file names. 日期一律末尾、AI 名由用户给定、文件名不塞技术标识。
- **Sync obligation / 联动同步铁律** — any file/path/structure change must propagate to every related reference immediately, without asking 'should I update?' — a duty, not a choice, machine-checked. 改动必须立即全库同步引用——义务不是选项，机器检查。
- **Identity & evidence discipline / 身份与证据纪律** — created_by/modified_by lines on every document; attribution by session evidence, not vibes; 'landed' claims need verifiable evidence; full-transcript discipline (append-only). 文档署名、归属按会话证据、「落地」要证据、全量转录只增不改。
- **Sensitive-information rule / 敏感信息规矩** — API keys/tokens/customer data not written by default; the AI stops and asks the user; the human decides, never the AI. 敏感默认不写、AI 停下问用户、判断权在用户。
- **Immutable audits / 审计不可变** — audit reports are never edited; in-progress audits need user discussion for non-substantive changes. 审计报告一律不改。

> Background / 背景：Governance distilled from months of daily multi-agent operation of a shared knowledge base (2026-08-07~10), including the machine-checked rule system and the 'single source of truth' injection design. / 从共享知识库数月多 Agent 日常运行中提炼（2026-08-07~10），含机器检查规矩体系与单一事实源设计。
