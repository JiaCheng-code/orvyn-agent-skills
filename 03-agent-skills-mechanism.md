# Agent Skills 是怎么工作的？拆解 SKILL.md 的加载机制与触发逻辑

> 发布：2026-10-19 · 分类：教程 · 原文：https://www.orvyn.top/articles/art-f27e6cfff2da

装了 Skills 之后，Claude Code 的表现会明显不一样。同一个需求，之前要来回解释三遍，现在它自己按流程走完了。

这背后是两个机制在起作用：加载和触发。这篇文章拆一下 Agent Skills 的文件结构和工作逻辑，然后从零写一个能用的 Skill。

## 一个 Skill 到底是什么？

按 Anthropic 官方仓库的定义，Skill 是"文件夹形式的指令、脚本和资源，Claude 会动态加载它们，以便在特定任务上表现更好"。

最核心的只有一个文件：`SKILL.md`。

```
my-skill/
├── SKILL.md          # 必需：元数据 + 指令
├── scripts/          # 可选：辅助脚本
└── references/       # 可选：参考资料
```

SKILL.md 分两部分。上面是 YAML frontmatter，下面是给 Claude 的正文指令：

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it
---

# My Skill Name

（这里写给 Claude 的步骤说明、示例和注意事项）
```

frontmatter 只有两个必需字段：

- `name`：唯一标识，小写字母加连字符
- `description`：说清楚这个技能做什么、什么时候该用

## 它是怎么被加载的？

有人担心装了 10 个 Skill 会把上下文塞满。实际加载是分层的，官方把这种设计叫动态加载：

1. **启动时只加载元数据**。每个可用技能的名字和 description 进入上下文，用来判断任务要不要用某个技能。
2. **匹配后才加载正文**。任务命中某个技能，完整的 SKILL.md 指令才会被读进来。
3. **资源按需读取**。正文里提到的脚本和参考资料，只在真正需要执行时才读。

这样处理有两个直接结果：技能装多了不会撑爆上下文窗口；无关任务不会被无关指令干扰。代价也明显：description 写得好不好，直接决定技能会不会被用起来。

## 触发是怎么判断的？

触发靠语义匹配，没有关键词命中表。模型读 description，结合你当前的任务判断该不该用。

所以 description 的写法基本决定了技能的使用率。对比两个写法：

```yaml
# 写法一：只说了做什么
description: 生成周报。

# 写法二：说清做什么 + 什么时候用
description: 把本周的 Git 提交、Jira 工单和会议纪要整理成周报。当用户要求写周报、汇报本周进展，或整理一周工作记录时使用。
```

第二种写法多了使用场景，模型在"帮我写下这周的进度"这类模糊请求里更容易想到它。

## 从零写一个 Skill：最小示例

以"提交前检查"为例，建一个文件夹：

```
pre-commit-check/
└── SKILL.md
```

SKILL.md 的内容：

```markdown
---
name: pre-commit-check
description: 提交前检查代码变更。当用户准备提交代码、要求检查 staged 改动，或询问这次改动有没有问题时使用。
---

# Pre-commit Check

## 步骤

1. 运行 `git diff --staged` 查看本次提交的改动
2. 检查以下项目：
   - 是否残留调试代码（console.log、print、debugger）
   - 是否误提交密钥、token、.env
   - 是否有未处理的 TODO/FIXME
3. 按文件输出检查结果，列出问题和建议

## 输出格式

按「文件 → 问题 → 建议」组织。没发现问题就明确说明，不要含糊。
```

装到本机有两种方式：

```bash
# 放进了 Git 仓库（推荐，团队可以共用）
npx skills add https://github.com/your-name/pre-commit-check

# 或者手动放进 Claude Code 的技能目录
# 个人级：~/.claude/skills/pre-commit-check/SKILL.md
# 项目级：项目根目录/.claude/skills/pre-commit-check/SKILL.md
```

装完直接说"帮我看看这次改动能不能提交"，它就会按步骤跑一遍。

## 写 Skill 时最容易踩的四个坑

**1. description 太笼统**

"提升代码质量"这种描述，模型没法判断什么时候用。把触发场景写进去。

**2. 正文写成散文**

SKILL.md 是给模型执行的指令，不是博客。步骤要编号，判断条件要明确，输出格式最好固定下来。

**3. 什么流程都往里塞**

一个 Skill 只解决一类任务。流程太长就拆成多个技能，让模型自己组合。

**4. 把 Skill 和 MCP 混着讲**

Skill 是"怎么做事"的指令，MCP 是"能连什么工具"的协议。一个查 Jira 工单的技能，可能需要 MCP 提供数据访问，但两者不是一回事。

## 怎么判断一个 Skill 值不值得装？

看三个地方，比只看 star 数有用：

1. **description**：有没有写清触发场景
2. **SKILL.md 正文**：步骤是否具体，有没有可验证的输出要求
3. **仓库更新情况**：最近还在维护的技能，通常跟得上工具版本变化

想找现成的技能，可以到 [Agent Skills 资源库](https://www.orvyn.top) 按分类浏览。目前收录了 1700+ 个技能仓库、2.5 万+ 个技能，每个详情页都能直接看 SKILL.md 内容和安装命令。

## 小结

Agent Skills 的机制不复杂：一个文件夹、一份 SKILL.md、按需加载。关键是把触发条件和执行步骤写清楚，文笔的影响反而小。

延伸阅读：[Claude Code 必装技能推荐](https://www.orvyn.top/articles/art-5b553fc19dd2) ｜ [AI 编程效率指南](https://www.orvyn.top/articles/art-14ffb7d65531)

---

> 本文首发于 [Agent Skills 资源库](https://www.orvyn.top)，收录 1700+ 个 AI 技能仓库。
