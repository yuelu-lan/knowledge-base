# 已安装 Skill 清单

本机 agent skill 清单，共 31 个。通过 `npx skills`（skills CLI v1.7.1）安装：

- **落盘**：`C:\Users\ywy\.agents\skills\`
- **记账**：`C:\Users\ywy\.agents\.skill-lock.json`
- **更新**：`npx skills@latest update -g`

> **首次使用提醒**：在要动代码的仓库里先跑一次 `/setup-matt-pocock-skills`。它配置 issue tracker、triage 标签与文档布局；不跑这一步，`/to-spec`、`/to-tickets`、`/triage` 找不到 tracker，链路是断的。

`名字` 列带 `/` 的需你手动输入调用，不带 `/` 的模型可自动触发。

## mattpocock/skills（27 个）

来源：<https://github.com/mattpocock/skills>，仅安装 `skills/engineering` 与 `skills/productivity` 两个 bucket。

未安装：`in-progress`（`chief-of-staff`、`claude-handoff`、`loop-me`、`setup-ts-deep-modules`、`writing-beats`、`writing-fragments`、`writing-shape`）、`misc`（`git-guardrails-claude-code`、`migrate-to-shoehorn`、`scaffold-exercises`、`setup-pre-commit`）。

| 名字 | 作用 |
|---|---|
| `/ask-matt` | 不确定用哪个 skill 时的入口路由器 |
| `/grill-me` | 反复盘问，逼出设计树的每个分支 |
| `/grill-with-docs` | 同上，并同步产出术语表与 ADR |
| `/to-spec` | 把当前对话整理成 spec 并发布 |
| `/to-tickets` | 把 spec 拆成带依赖的工单 |
| `/implement` | 按 spec 或工单实现，收尾自审 |
| `/implement-spec` | 并行子代理实现整份 spec |
| `/triage` | 按状态机推进 issue 与外部 PR |
| `/improve-codebase-architecture` | 扫架构找深模块化机会并出报告 |
| `/wayfinder` | 为超大工作铺决策工单地图 |
| `/retro` | 复盘会话，指出工作环境改进点 |
| `/setup-matt-pocock-skills` | 配置 tracker、标签与文档布局 |
| `/handoff` | 把对话压成交接文档 |
| `/teach` | 用当前目录做教学工作区授课 |
| `/to-questionnaire` | 把答不了的决策写成问卷 |
| `/wait-what` | 没听懂时要求换种说法重讲 |
| `grilling` | 盘问原语，供其它 skill 调用 |
| `tdd` | 测试先行，红-绿-重构逐片推进 |
| `diagnosing-bugs` | 难 bug 的反馈环加假设诊断闭环 |
| `code-review` | 双轴审查：规范与 spec 符合度 |
| `codebase-design` | 深模块设计词汇与接缝判断 |
| `domain-modeling` | 打磨领域术语并维护术语表 ADR |
| `prototype` | 抛原型回答逻辑或 UI 设计问题 |
| `research` | 高可信来源调研并落成引用文档 |
| `pr` | 规范 PR 正文：摘要、证据、风险 |
| `wizard` | 生成 bash 向导走人工配置步骤 |
| `writing-for-agents` | 为 agent 写作 skill 与文档 |

### 使用建议

- **一次性配置只见效于单个仓库**：tracker 可以是 GitHub、GitLab 或本地 markdown 文件，换仓库要重跑，换了 tracker 也要重跑。
- **不确定从哪开始就问 `/ask-matt`**：它是作者写的路由器，会告诉你当前处境该走哪条路。
- **主线：想法 → 上线**。仓库内用 `/grill-with-docs`（会留下 `GLOSSARY.md` 与 ADR）替代 `/grill-me`；单会话能做完的直接 `/implement`，跨会话的先 `/to-spec` → `/to-tickets`，再逐个 `/implement`（或 `/implement-spec` 一次做完整个 spec）。
- **上下文纪律**：`/grill-with-docs` → `/to-spec` → `/to-tickets` 要在一个不间断的窗口里做完；之后每个 `/implement` 都另起新会话。
- **收尾用 `/retro`**：复盘并改进 agent 的工作环境（检查、规范、导航），在清空上下文之前跑。
- **旁路**：新报的 issue 用 `/triage`，难 bug 用 `/diagnosing-bugs`，超大而模糊的工作用 `/wayfinder`，架构维护用 `/improve-codebase-architecture`，需要外部信息用 `/research`。

## cli/cli（1 个）

来源：<https://github.com/cli/cli>

| 名字 | 作用 |
|---|---|
| `gh` | 调用 GitHub CLI 的常用套路 |

## vercel-labs/skills（1 个）

来源：<https://github.com/vercel-labs/skills>

| 名字 | 作用 |
|---|---|
| `find-skills` | 发现并安装 agent skill |

## anthropics/skills（1 个）

来源：<https://github.com/anthropics/skills>

| 名字 | 作用 |
|---|---|
| `skill-creator` | 创建、改进、评测 skill |

## tw93/kami（1 个）

来源：<https://github.com/tw93/kami>

| 名字 | 作用 |
|---|---|
| `kami` | 用 Kami 模板排版 PDF 与幻灯片 |
