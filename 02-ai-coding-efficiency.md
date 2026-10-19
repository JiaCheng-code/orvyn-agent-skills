# AI 编程效率指南：Claude Code / Cursor / Codex 通用的 8 类 Agent Skills（2026）

> 发布：2026-10-13 · 分类：教程 · 原文：https://www.orvyn.top/articles/art-14ffb7d65531

Claude Code、Cursor、Codex 都装上之后，效率未必立刻起飞。原因很直接：AI 会陪聊，不等于会干活。让它真正接入工作流，靠的是技能（Skills），也就是教它按专业流程做事的能力包。

而且这件事不用挑工具。Agent Skills 是通用标准，同一套技能在 Claude Code、Cursor、Codex、Gemini CLI 里都能用。

下面按 8 类工作场景整理了 20 个技能，都来自官方或高星开源仓库，附安装命令，哪个场景像你的日常就装哪个。

## 场景 1：代码质量与审查

### Addy Osmani Agent Skills（10.6 万星）
Google Chrome 团队 Addy Osmani 发布，覆盖从写规格、实现、测试到发布上线的完整开发流程，侧重生产环境的工程规范。

```bash
npx skills add https://github.com/addyosmani/agent-skills
```

### Claude Code 官方插件（15.0 万星）
Anthropic 官方插件集，其中的 PR 审查工具包能把代码审查固定成标准流程。

```bash
npx skills add https://github.com/anthropics/claude-code
```

### Matt Pocock's Skills（28.8 万星）
TypeScript 教育者 Matt Pocock 的工程技能，TS 项目建议直接装。

```bash
npx skills add https://github.com/mattpocock/skills
```

## 场景 2：安全扫描与审计

### Cloudflare 安全审计（2.9 万星）
多阶段安全审计技能，每项结论独立验证，输出机器可读的结果。改完代码让它跑一遍。

```bash
npx skills add https://github.com/cloudflare/security-audit-skill
```

### NVIDIA Skill Inspector（2.0 万星）
它管的是另一件事：扫描「待安装的技能」本身，查漏洞、恶意模式、提示注入和供应链风险。装陌生技能前先让它跑一遍。

```bash
npx skills add https://github.com/NVIDIA/SkillSpector
```

## 场景 3：代码库理解与架构

接手新项目、给老项目补文档，这两个技能很省时间。

### Graphify（12.6 万星）
把代码库（含文档、SQL 模式、PDF）转成可查询的知识图谱，基于本地确定性 AST 解析，每条边都有解释。

```bash
npx skills add https://github.com/Graphify-Labs/graphify
```

### Archify（8.3 万星）
生成可验证的架构图、工作流图、时序图、数据流图，输出自包含 HTML，可直接分享。

```bash
npx skills add https://github.com/tt-a1i/archify
```

## 场景 4：设计与前端

### UI UX Pro Max（13.5 万星）
跨平台的 UI/UX 设计智能，写页面前装上它，配色和排版会好看不少。

```bash
npx skills add https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
```

### Hallmark（3.0 万星）
「反 AI 味设计」技能，专治一眼假的模板感。做过 AI 生成页面的都懂这个痛点。

```bash
npx skills add https://github.com/nutlope/hallmark
```

### Taste Skill（9.5 万星）
前端设计加图片转代码的「品味」技能库，和上面两个配合用效果更好。

## 场景 5：办公文档自动化

### Officecli（3.2 万星）
为 AI 代理打造的 Office 套件，能读取、编辑、自动化处理 Word、Excel、PowerPoint。周报、报表、合同的批量处理场景直接受益。

```bash
npx skills add https://github.com/iofficeai/officecli
```

### PDF（OpenAI 官方技能，2.8 万星）
OpenAI 官方技能目录里的 PDF 处理技能，解析、提取、生成 PDF 的标准做法。

```bash
npx skills add https://github.com/openai/skills
```

### Book to Skill（3.5 万星）
把技术书籍 PDF 转成可随时查阅的技能，想把常翻的书「装进」AI 的可以试试。

## 场景 6：演示与视频

### Frontend Slides（3.1 万星）
用 HTML 生成动画丰富的演示文稿，也能直接转换已有 PPT，程序员做分享的利器。

```bash
npx skills add https://github.com/zarazhangrui/frontend-slides
```

### OpenMontage（6.8 万星）
开源代理视频制作系统，12 条生产管线、100+ 工具、700+ 技能，把 AI 编程助手变成视频工作室。

## 场景 7：写作与内容

### Humanizer（5.6 万星）
把 AI 写的内容「去味」，删掉空话和模板句。写公众号、发博客的刚需。

```bash
npx skills add https://github.com/blader/humanizer
```

### Marketing Skills（5.4 万星）
面向 Claude Code 的营销技能集，文案、SEO、分析、增长工程都有，独立开发者做产品推广很实用。

```bash
npx skills add https://github.com/coreyhaines31/marketingskills
```

## 场景 8：知识管理与研究

### Obsidian Skills（4.9 万星）
Obsidian 创始人 kepano 出品，教 AI 使用 Obsidian CLI 与开放格式。用笔记软件搭第二大脑的用户可以装。

```bash
npx skills add https://github.com/kepano/obsidian-skills
```

### Academic Research Skills（5.2 万星）
学术研究技能，覆盖文献审计、写作、同行评审辅助，科研工作者从开题到投稿的全流程。

### Last30days（6.4 万星）
调研某个话题近 30 天的全网动态（Reddit、X、YouTube、Hacker News），做技术选型、写行业分析前先跑一次。

## 加餐：两个和效率直接相关的技能

### Caveman（11.1 万星）
让 Claude Code 用「超压缩通信」模式输出，实测能省约 65% 的输出 token，技术准确性基本不受影响。高频使用的话，省下的都是钱。

### Superpowers（29.8 万星）
社区最火的开发方法论框架：头脑风暴、计划、实现、验证四步走。适合作为第一个安装的技能打底。

## 怎么把这些技能组合成工作流？

一个顺手的组合（前端项目 + 团队协作）：

1. Superpowers 打底，把 AI 的开发流程规范起来
2. 加上 UI UX Pro Max 和 Hallmark，前端场景提审美、去 AI 味
3. 提交前用 Claude Code 官方插件跑 PR 审查
4. 上线前跑一遍 Cloudflare 安全审计
5. 之后装任何新技能前，先用 Skill Inspector 扫一遍

## 常见问题 FAQ

**Q：技能在所有 AI 编程工具里通用吗？**
A：Agent Skills 是通用标准，Claude Code、Cursor、Codex、Gemini CLI 等主流工具都兼容，一套技能可以跨工具使用。

**Q：装这么多技能，AI 会不会「乱用」？**
A：不会。技能按需触发，AI 只在任务匹配时加载对应技能，不会全部同时生效。建议还是分批安装。

**Q：去哪里找这些技能？**
A：[Agent Skills 资源库](https://www.orvyn.top) 收录了 1700+ 个技能仓库、2.5 万+ 个技能，按开发、安全、设计、办公等 42 个分类整理，每个技能都有安装命令、星标和搜索，本文提到的全部可以在这里搜到。

## 写在最后

上面 8 类场景，挑最贴近你日常的 1-2 类先用起来。装多了容易哪个都不用，先把一个用顺手，再考虑下一个。

全部分类浏览：[Agent Skills 资源库](https://www.orvyn.top/categories)
新手入门：[什么是 Agent Skills？](https://www.orvyn.top/articles/art-8ca4253fad14) ｜ [Claude Code 必装技能推荐](https://www.orvyn.top/articles/art-5b553fc19dd2)

---

> 本文首发于 [Agent Skills 资源库](https://www.orvyn.top)，收录 1700+ 个 AI 技能仓库。
