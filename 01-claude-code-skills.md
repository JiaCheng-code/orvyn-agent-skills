# Claude Code 必装技能推荐：10 个高星 Agent Skills 清单（2026 版）

> 发布：2026-10-13 · 分类：教程 · 原文：https://www.orvyn.top/articles/art-5b553fc19dd2

同样是用 Claude Code，写出来的代码质量可以差很多。区别常常在技能（Skills）：装过安全审计技能的，会按清单逐项检查；没装的，就只能靠自己一句句追问。

技能就是给 Claude Code 预先装好的专业能力包，装上之后，它在特定任务里会按固定流程做事。这篇整理了 10 个值得装的 Claude Code 技能，全部来自官方或高星开源仓库，每个都附安装命令。括号里标了仓库的 GitHub 星数，方便你判断热度。

## Claude Code 技能（Skills）是什么？

Skill 是教 Claude Code 做专业工作的可复用能力包。一个技能通常包含两部分：SKILL.md 指令文件，写明什么时候用它、按什么流程做；以及配套资源，比如脚本、模板、示例文件。

安装一次之后，在任何项目里都能让 Claude Code 按同一套流程执行。它和几个常被混淆的概念，分工大致是这样：

| 概念 | 负责什么 | 例子 |
|------|---------|------|
| Prompt | 这次做什么 | 「帮我改这个函数」 |
| **Skill** | 怎么做才对 | 「按安全清单审查代码」 |
| MCP | 能调用什么工具 | 连接数据库、浏览器 |

三者互补：MCP 负责「连接」，Skill 负责「方法论」，Prompt 负责「这一次的任务」。

## 怎么安装 Claude Code 技能？

绝大多数技能一条命令就能装好：

```bash
npx skills add https://github.com/obra/superpowers
```

装完之后正常描述任务即可，Claude Code 会自动匹配并加载对应技能。例如装了代码审查类技能后，你说「帮我审查这次改动」，它会按技能预设的流程逐项检查，而不是随口点评两句。

> 提示：技能也可以手动管理目录，个人级放在 `~/.claude/skills/`，项目级放在项目内的 `.claude/skills/`。

## 10 个必装 Claude Code 技能推荐

### 开发工程类：让 AI 像靠谱工程师一样干活

### 1. Superpowers（29.8 万星）

社区目前最火的技能框架，本体是一套开发方法论：先头脑风暴，再拆计划，然后实现、验证。它要求 AI 每个阶段都停下来跟你确认，用不惯的人会觉得啰嗦，做正式项目时省心。适合把 Claude Code 当主力工具的开发者。

安装：`npx skills add https://github.com/obra/superpowers`

### 2. Matt Pocock's Skills（28.8 万星）

TypeScript 圈知名教育者 Matt Pocock 放出的工程技能，取材自他本人日常使用的 `.agents` 目录，覆盖 TS 项目里的类型设计和重构场景。写 TypeScript 的话建议优先装。

安装：`npx skills add https://github.com/mattpocock/skills`

### 3. Karpathy Skills（21.9 万星）

把 Andrej Karpathy 关于 LLM 编码常见坑的观察，整理成一份改进 Claude Code 行为的 `CLAUDE.md` 文件。它不改你的工作流，装完立刻生效，是这批技能里成本最低的一个。

安装：`npx skills add https://github.com/multica-ai/andrej-karpathy-skills`

### 4. Addy Osmani Agent Skills（10.6 万星）

Google Chrome 团队 Addy Osmani 发布，覆盖从写规格、实现、测试到发布上线的完整流程。适合对代码质量有要求的团队项目。

安装：`npx skills add https://github.com/addyosmani/agent-skills`

### 官方出品：稳定可靠、随版本更新

### 5. Anthropic 官方技能库（18.1 万星）

Anthropic 官方维护的技能仓库，有前端设计、文档处理（docx / xlsx / pdf）、Canvas 设计等技能。更新跟着 Claude Code 的版本节奏走，是各家技能里最稳的一档。

安装：`npx skills add https://github.com/anthropics/skills`

### 6. Claude Code 官方插件（15.0 万星）

Anthropic 随 Claude Code 一起维护的官方插件集，包括 Agent SDK 开发工具、PR 审查工具包和提交工作流。团队协作场景重点看 PR 审查部分。

安装：`npx skills add https://github.com/anthropics/claude-code`

### 7. Cloudflare 安全审计（2.9 万星）

Cloudflare 开源的多阶段安全审计技能，每项结论都要独立验证，输出机器可读的结果。建议在发版前跑一遍。

安装：`npx skills add https://github.com/cloudflare/security-audit-skill`

### 场景类：即装即用

### 8. UI UX Pro Max（13.5 万星）

给 AI 补「设计审美」的技能，面向跨平台的 UI/UX 场景。做前端页面前装上它，生成界面的配色和排版会好看不少。

安装：`npx skills add https://github.com/nextlevelbuilder/ui-ux-pro-max-skill`

### 9. Officecli（3.2 万星）

为 AI 代理打造的 Office 套件，让 Claude Code 直接读取、编辑、自动化处理 Word、Excel、PowerPoint。经常做报表、合同、汇报文档的话值得装。

安装：`npx skills add https://github.com/iofficeai/officecli`

### 10. Obsidian Skills（4.9 万星）

Obsidian 创始人 kepano 发布的笔记库技能，教 AI 使用 Obsidian CLI 和开放格式（Markdown、Bases、JSON Canvas）。用 Obsidian 管知识库可以直接装。

安装：`npx skills add https://github.com/kepano/obsidian-skills`

## 怎么挑适合自己的技能？

技能不是装得越多越好。先想想你每周重复最多的动作是什么，写周报、审代码，还是处理表格？按这个去挑，一般装 1-2 个就够开始用了。

挑选时优先看两类：官方出品和高星仓库。技能本质上是给 AI 看的指令文件，安装前花两分钟打开 SKILL.md 看一眼，比什么评测都直接。

最后一个提醒：先装 2-3 个用一周，留下顺手的再扩充。

## 常见问题 FAQ

**Q：Claude Code 技能是免费的吗？**
A：本文推荐的技能全部免费开源，来源都是 GitHub 公开仓库，可自由查看、修改。

**Q：技能安全吗？会不会有恶意代码？**
A：优先选官方或高星仓库的技能，安装前打开 SKILL.md 看一下它做什么。在意安全的话，先装 NVIDIA SkillSpector 这类扫描技能，把目标技能扫一遍再用。

**Q：这些技能能在 Cursor / Codex 里用吗？**
A：可以。Agent Skills 是通用标准，Claude Code、Codex、Cursor 等主流 AI 编程工具都兼容同一套技能。

**Q：去哪里找更多 Claude Code 技能？**
A：推荐 [Agent Skills 资源库](https://www.orvyn.top)，目前收录了 1700+ 个技能仓库、2.5 万+ 个技能，按 42 个分类整理，每个都提供安装命令和 GitHub 星标，支持关键词搜索。官方专区收录了 Anthropic、OpenAI、Cloudflare、Docker 等机构的出品。

## 写在最后

还没想好从哪个开始的话，Karpathy Skills 和 Superpowers 都行：前者只改 Claude Code 的行为规则，装上就能看出区别；后者要配合它那套流程用上一两天，才体会得到价值。

浏览全部技能：[Agent Skills 资源库](https://www.orvyn.top/categories)
进阶阅读：[AI 编程效率指南：8 类通用 Agent Skills（Claude Code / Cursor / Codex）](https://www.orvyn.top/articles/art-14ffb7d65531)
新手先看：[什么是 Agent Skills？](https://www.orvyn.top/articles/art-8ca4253fad14) ｜ [5 分钟装好你的第一个 Skill](https://www.orvyn.top/articles/art-34554f629041)

---

> 本文首发于 [Agent Skills 资源库](https://www.orvyn.top)，收录 1700+ 个 AI 技能仓库。
