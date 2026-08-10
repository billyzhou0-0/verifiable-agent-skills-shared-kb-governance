# Changelog（更新记录）

## Open-source release / 开源发布

- Rules for a knowledge base shared by multiple AIs and one human: directory contracts, naming, flow, sync obligation, evidence discipline — machine-checked on every commit. / 多 AI 共享知识库的治理规矩：目录契约、命名、流转、同步铁律、证据纪律——每次提交机器检查。

## Initial version / 最初版本

- Multiple AIs and one human sharing a knowledge base descended into chaos by default: files in the wrong place, meaningless names, sync never happened → the governance system was built: directory contracts (inbox / ai-staging / todo / archive), naming rules (date always at the end), flow callbacks, the link-sync iron rule. / 多个 AI 与一个人共用一个知识库=默认混乱：文件落错位、命名无意义、同步没人做 → 建立治理体系：目录分工契约（收件箱/ai暂存/待办/归档）、命名规矩（日期末尾无条件）、流转回写、联动同步铁律。

## Second update / 第二次更新

- Written rules are not enforcement (AI doesn't reliably read files, compression makes it forget) → a single source of truth (must-read card + auto-injected mirror) + machine checks (health-check script + pre-commit hook); sensitive-info judgment was mis-placed → not written by default, stop and ask the human, the human decides. / 纸面规矩不是强制（AI 不主动读文件、压缩后遗忘）→ 单一事实源（必读卡+自动注入镜像）+ 机器检查（体检脚本+提交前钩子）；敏感信息判断权错位 → 默认不写入、疑似停下问用户、判断权在用户。

## Third update / 第三次更新

- Audit reports were being edited at will → the immutable-audit rule: audit reports are never modified; non-substantive changes to an in-progress audit require discussion with the human first. / 审计报告被随意修改 → 审计不可变铁律（一律不改，进行中审计非实质性修改先与用户商议）。
