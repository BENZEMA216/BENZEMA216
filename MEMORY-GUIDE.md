# 我的 GitHub 记忆系统

> 不是套框架，是从我已经在做的事情里，提炼出可以持续运转的方式。

---

## 我已经在用的记忆模式

回看自己的仓库，有几种记忆模式已经自然长出来了。把它们命名出来，是为了下次知道"这个东西该往哪放"。

### 1. 品牌记忆（creo）

creo 已经实现了一套完整的美学记忆系统：品牌档案 → Visual DNA → 资产索引 → `creo://` 统一寻址。核心循环是 **Reflect → Record → Reuse**：做完一次设计任务，提炼出有效的审美经验，结构化存下来，下次 Agent 创作时直接读取。

**已有的好设计：**
- 三层降级（原始素材 → 风格样本 → 文字描述），Agent 按可用性自动选择
- 品牌档案格式统一（Identity / Visual DNA / Tone / Catalog / Assets）
- 每张素材都有 `creo://` ID，Agent 不关心文件在哪

**可以继续做的：**
- 每服务一个新品牌，确保走完 Asset Intake Protocol
- 定期检查 Visual DNA 是否还反映品牌最新风格
- 社区贡献的风格样本做脱敏后上传

### 2. 踩坑记忆（openclaw-pitfalls）

这是整个系统里结构化程度最高的记忆。每条 PIT 用 YAML Capsule 格式记录：

```
问题信号 → 错误路径（走过的弯路）→ 正确路径 → 根因 → 置信度 → 爆炸半径
```

**这个格式的精髓：**
- **双路径对照**：同时记录"做错了什么"和"应该怎么做"——比只记正确答案多了认知深度
- **signal 可搜索**：下次遇到同样报错，`grep` 一下就能定位
- **置信度诚实**：承认有些修复不确定，这本身就是有价值的记忆

**可以继续做的：**
- 不只记 OpenClaw 的坑，任何基础设施踩坑（部署、配置、CI/CD）都可以用这个格式
- PIT-012 的教训（"SKILL.md 必须告诉 Agent 用什么工具"）本质上是产品设计原则，值得提炼到更高层

### 3. 技能记忆（Claude Code 插件体系）

music-analyzer / creative-think / agent-form / self-purify / chatshot——这些仓库共享同一个模式：

```
输入（音频/brief/问题）→ 结构化分析 → 规则映射 → 生成输出（Prompt/代码/报告）
```

它们就是 Agent 的"程序记忆"——不是知道什么，而是**会做什么**。每个 SKILL.md 就是一个可执行的能力定义。

**已有的好设计：**
- 统一的 Claude Code 插件架构（`.claude/skills/*/SKILL.md`）
- music-analyzer 的三层依赖降级（lite → standard → full）
- creative-think 的 4 阶段推理链

**可以继续做的：**
- 新技能按同样的架构创建，保持一致性
- SKILL.md 要写清楚"用什么工具做什么"（PIT-012 的教训）
- 技能之间可以组合调用（music-analyzer → creative-think → Dreamina）

### 4. 产品思考记忆（agent-identity-docs）

agent-identity-docs 里的对话记录和项目文档，保存了从模糊想法到清晰产品定义的完整思考链：

```
"看 Agent 状态的 App" → "Agent 形象不该人设计" → "把半成品扔给 Agent" → "弦自己完成了一切" → agentavatar.dev
```

**这类记忆的价值：** 不是记住结论，而是记住**推导过程**。半年后回看，能重新理解当时为什么做这个决定。

**可以继续做的：**
- 重要产品决策的思考过程，都值得一份类似的文档
- 格式不需要固定——对话记录、思维链、pro/con list 都行，关键是保留推理路径

### 5. 作品记忆（tradingcoach / rss-reader / xian-home）

这些是"做出来的东西"本身。tradingcoach 是完整的全栈产品，rss-reader 是信息管道，xian-home 是弦的存在空间。它们的代码、架构、CLAUDE.md 本身就是记忆。

**已有的好设计：**
- tradingcoach 的 CLAUDE.md 有完整的工程规范（文档维护、Git 分支策略、部署管道）
- rss-reader 架构极简（fetcher → summarizer → notifier），易于理解和复用

### 6. 日志记忆（clawd-daily）——未完成的实验

clawd-daily 设计很好（AI Agent 第一人称 + 技术笔记的双轨日志），但只写了 Day 1。

**反思：** 日志如果每天都要写，就容易断。更现实的做法可能是：
- 不追求"日更"，而是在有值得记的事发生时记
- 或者把日志嵌入已有的仓库（在 creo 里记一次品牌服务的复盘，在 pitfalls 里记一次部署的坑），而不是单独维护一个日志仓库

---

## 分类标签

上面 6 种记忆模式，对应 5 个 Topic 标签（已全部打好）：

| Topic | 对应的记忆模式 | 什么时候用 |
|-------|-------------|-----------|
| `memory-identity` | 身份 + 产品思考 | Profile、个人站点、笔记库 |
| `memory-agent` | 产品 + 作品 | OpenClaw/Clawd 生态的仓库 |
| `memory-skill` | 技能 | Claude Code 插件、可执行能力 |
| `memory-learning` | 踩坑 + 日志 | 认知记录、复盘、研究 |
| `memory-infra` | 作品（基础设施类） | RSS、监控、支付等服务 |

---

## 新建仓库时

1. **命名**：`kebab-case`
2. **描述**：一句话，格式 `Name — 做什么`
3. **Topic**：打上对应的 `memory-*`
4. **README**：至少说清楚这个仓库"记住了什么"
5. **Profile Memory Map**：同步更新

## 日常运转

**做了一次品牌服务 →** 更新 creo 里的品牌档案，走 Reflect → Record → Reuse

**踩了一个坑 →** 在 pitfalls 里新建一条 PIT-XXX.yaml，走 Signal → Error Path → Correct Path → Root Cause

**做了一个新 Claude Code 技能 →** 新建仓库，写 SKILL.md，确保告诉 Agent 用什么工具做什么

**做了一个重要产品决策 →** 在相关仓库（或 agent-identity-docs）里记下推导过程，不只是结论

**做出了一个新东西 →** 确保 CLAUDE.md 和 README 写好，代码本身就是记忆

## 每月检查

```bash
# 哪些仓库没有描述？
gh repo list --json name,description \
  --jq '.[] | select(.description == "" or .description == null) | .name'

# 哪些仓库没有 memory-* 标签？
gh repo list --json name,repositoryTopics,isFork,isArchived \
  --jq '.[] | select(.isFork==false and .isArchived==false) |
  select((.repositoryTopics | map(.name) | map(select(startswith("memory-"))) | length) == 0) | .name'

# 哪些仓库超过 6 个月没动了？
gh repo list --json name,pushedAt,isArchived \
  --jq '.[] | select(.isArchived==false) |
  select(.pushedAt < (now - 15780000 | strftime("%Y-%m-%dT%H:%M:%SZ"))) | .name'
```

过期的仓库 → 归档（`gh repo archive`），从 Memory Map 移除。

---

## 这套系统的本质

不是 PARA，不是 Zettelkasten，不是 Agent Memory 论文里的架构。
是从我自己的工作习惯里长出来的东西：

- **creo 的 Reflect-Record-Reuse** 是我处理品牌美学经验的方式
- **pitfalls 的 YAML Capsule** 是我处理踩坑经验的方式
- **SKILL.md** 是我给 Agent 定义能力的方式
- **对话记录和思维链** 是我保存决策推导过程的方式
- **代码仓库本身** 就是我做出的东西的记忆

把这些命名出来、保持标签一致、定期清理——就是全部了。

---

*最后更新：2026-03-04*
