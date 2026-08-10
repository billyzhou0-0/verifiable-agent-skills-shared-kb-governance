# Changelog（更新记录）

All notable changes to this project are documented here, following Keep a Changelog with semver versioning. / 本文件按 Keep a Changelog 规范记录本项目所有重要变更。

## [1.0.0] - 2026-08-11

### Initial open-source release / 初始开源发布

- Rules for a knowledge base shared by multiple AIs and one human: directory contracts, naming rules, flow rules, sync obligation, evidence discipline - machine-checked on every commit. / 多 AI 共享知识库的治理规矩：目录契约、命名、流转、同步铁律、证据纪律——每次提交机器检查。

## Pre-release evolution（开源前演进史）

Each fix below was proven in real production. / 以下每条修复均在真实生产中验证。

### 1. 多 AI 共库默认混乱

- **Fix / 修复**：文件落错位、命名无意义、同步没人做、「完成」声称对不上现实。修复：目录分工契约（收件箱/ai暂存/待办/归档）+ 命名规矩（日期末尾无条件）+ 流转回写（✅已转交）+ 联动同步铁律（义务不是选项）。

### 2. 纸面规矩不是强制

- **Fix / 修复**：AI 不主动读文件、压缩后遗忘。修复：单一事实源（必读卡+自动注入镜像）+ 机器检查（体检脚本+提交前钩子）；归属按会话证据不凭感觉；「已落地」必须附可验证证据。

### 3. 敏感信息判断权错位

- **Fix / 修复**：AI 自行判断敏感会双向误判（把示例当真、把真的当无害）。修复：敏感默认不写入，疑似停下问用户，用户明确同意才写，判断权在用户。

### 4. 审计报告被随意修改

- **Fix / 修复**：历史审计被改会破坏可信度。修复：审计报告一律不改（不止历史几份）；进行中审计非实质性修改先与用户商议。
