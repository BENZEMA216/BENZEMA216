# GitHub Memory System — 维护指南 v2

> 以 Agent Memory 设计理念 + 个人知识管理最佳实践，构建 GitHub 上的外部大脑。

---

## 设计理念

本系统融合三个方法论：

| 方法论 | 核心思想 | 在本系统中的体现 |
|--------|---------|----------------|
| **PARA**（Tiago Forte） | 按行动力分类：Projects / Areas / Resources / Archives | 仓库分层：活跃项目 → 长期领域 → 参考资料 → 归档 |
| **Agent Memory 分类体系**（CoALA / A-MEM） | 语义记忆 / 情景记忆 / 程序记忆 / 工作记忆 | 对应仓库类型：知识库 / 日志 / 技能插件 / 当前项目 |
| **Zettelkasten** | 原子化笔记 + 双向链接 + 知识涌现 | 每个仓库是一个"记忆单元"，通过 Topic 和 README 索引互联 |

### 为什么用 GitHub 而不是 Notion / Obsidian？

- **Git 即记忆时间线**：每次 commit 自带时间戳，天然记录知识演化轨迹
- **可移植性**：纯 Markdown + Git，不被任何平台锁定
- **代码与知识统一**：对技术型 PM，代码仓库本身就是知识资产
- **AI 可读**：Claude Code / Cursor 可以直接读取和操作 GitHub 仓库
- **协作与公开**：部分记忆可开源分享，形成个人品牌

> 参考：[A Personal Git Repo as a Knowledge Base Wiki](https://dev.to/adam_b/a-personal-git-repo-as-a-knowledge-base-wiki-j51)

---

## 记忆架构

### 认知科学视角：四类记忆

借鉴 CoALA 框架（Princeton, 2023）和 2025 年 arXiv 综述 *"Memory in the Age of AI Agents"*，将仓库映射为四类认知记忆：

```
┌─────────────────────────────────────────────────────┐
│                  GitHub Memory System                │
├──────────────┬──────────────────────────────────────┤
│ 语义记忆      │ 积累的事实、认知、方法论              │
│ Semantic     │ → memory-learning / memory-identity   │
├──────────────┼──────────────────────────────────────┤
│ 情景记忆      │ 过去的经历、踩坑、日志                │
│ Episodic     │ → clawd-daily / openclaw-pitfalls     │
├──────────────┼──────────────────────────────────────┤
│ 程序记忆      │ 可执行的技能、工具、插件              │
│ Procedural   │ → memory-skill 类仓库                │
├──────────────┼──────────────────────────────────────┤
│ 工作记忆      │ 当前活跃的项目上下文                  │
│ Working      │ → memory-agent 中活跃开发的仓库       │
└──────────────┴──────────────────────────────────────┘
```

### PARA 视角：GitHub 结构映射

| PARA 层级 | GitHub 对应 | 说明 |
|-----------|------------|------|
| **Projects** | GitHub Projects (boards) | 有明确目标和截止日期的短期工作 |
| **Areas** | Repositories | 持续维护的责任领域（仓库本身） |
| **Resources** | README / Wiki / Topic 索引 | 参考资料，随时可检索 |
| **Archives** | Archived repos / 归档分支 | 不活跃但保留的历史记忆 |

> 参考：PARA 方法应用于 GitHub 的实践（[Forte Labs](https://fortelabs.com/blog/para/)）

---

## Topic 标签体系

每个仓库**必须**打上对应的分类 Topic。这是记忆系统的索引基础。

| Topic | 认知记忆类型 | 含义 | 示例 |
|-------|------------|------|------|
| `memory-identity` | 语义 | 身份：Profile、站点、笔记库 | BENZEMA216, BENZEMA-vault |
| `memory-agent` | 工作/程序 | Agent 生态：OpenClaw/Clawd 产品 | creo, HomForClawd, xian-home |
| `memory-skill` | 程序 | 技能/插件：可执行的能力 | music-analyzer, chatshot |
| `memory-learning` | 情景/语义 | 认知记忆：踩坑、复盘、研究 | openclaw-pitfalls, tradingcoach |
| `memory-infra` | 程序 | 基础设施：服务与工具链 | rss-reader, web3-timeline |

**按 Topic 快速检索：**
```
https://github.com/BENZEMA216?tab=repositories&q=topic:memory-skill
```

---

## CODE 工作流：日常记忆运转

借鉴 Tiago Forte 的 CODE 框架（Capture → Organize → Distill → Express），适配到 GitHub：

### 1. Capture（捕获）

> 只捕获引起共鸣的 10%，而非所有信息。

- **GitHub Issues 作为收件箱**：在对应仓库创建 Issue 记录灵感、问题、发现
- **clawd-daily 快速记录**：日常碎片认知直接 commit 到日志仓库
- **踩坑即记**：遇到部署/技术问题，立即更新对应的 pitfalls 仓库

### 2. Organize（组织）

> 问自己："这条信息对哪个项目/领域最有用？"

- 新信息归入对应的 `memory-*` 仓库
- 新仓库创建时立即打 Topic 标签
- 定期检查 Issues，将已处理的关闭，将有价值的转为文档

### 3. Distill（蒸馏）

> 渐进式总结：高亮 → 摘要 → 精华。

- 日志定期提炼为**周复盘 / 月总结**
- 踩坑记录提炼为**决策原则**（"下次遇到 X 情况，做 Y"）
- 项目经验提炼为**可复用模式**（"问题 → 方案 → 复盘"三段式）

### 4. Express（表达）

> 笔记不是终点，而是创作的原材料。

- 蒸馏后的认知输出为博客、分享、或新项目的设计文档
- 技能插件本身就是"程序记忆"的表达
- Profile README 的 Memory Map 是记忆系统的公开表达

---

## 记忆生命周期管理

借鉴 Agent Memory 研究中的记忆动态管理模型（Formation → Evolution → Retrieval → Decay）：

### Formation（形成）
- 新仓库 = 新记忆单元
- 遵循下方的「新建仓库 Checklist」

### Evolution（演化）
- 定期更新仓库内容，保持记忆鲜活
- 当认知升级时，更新而非新建（避免冗余记忆）
- 关联仓库之间建立链接（README 中互相引用）

### Retrieval（检索）
- 通过 Topic 标签快速定位分类
- 通过 Profile README 的 Memory Map 导航
- 通过 `gh` CLI 搜索：`gh search repos --owner=BENZEMA216 --topic=memory-skill`

### Decay（衰减与淘汰）
| 条件 | 操作 |
|------|------|
| Fork 且 > 6 个月无修改 | `gh repo archive` |
| 原创但已弃用 | 归档，保留描述作为"死记忆" |
| 空仓库、无意义仓库 | 直接删除 |
| 认知已被更新的旧记录 | 合并到新记录中，归档旧仓库 |

> 参考：A-MEM（[arXiv 2502.12110](https://arxiv.org/abs/2502.12110)）将 Zettelkasten 原则应用于 Agent Memory，每条记忆带有上下文描述、关键词和标签，支持动态索引和记忆演化。

---

## 新建仓库 Checklist

每次创建新仓库时，确保完成以下步骤：

- [ ] **命名**：使用 `kebab-case`（如 `my-new-tool`）
- [ ] **描述**：一句话描述，格式 `Name — 功能说明`
- [ ] **Topic**：打上对应的 `memory-*` 分类标签
- [ ] **可见性**：含敏感信息的设为 private
- [ ] **README**：至少包含一段话说明这个仓库"记住了什么"
- [ ] **Memory Map**：将新仓库添加到 Profile README 的对应分类中

---

## 定期维护（建议每月一次）

### 1. 健康检查脚本
```bash
# 查找没有 description 的仓库
gh repo list --json name,description \
  --jq '.[] | select(.description == "" or .description == null) | .name'

# 查找没有 memory-* topic 的仓库（排除 fork 和 archived）
gh repo list --json name,repositoryTopics,isFork,isArchived \
  --jq '.[] | select(.isFork==false and .isArchived==false) |
  select((.repositoryTopics | map(.name) | map(select(startswith("memory-"))) | length) == 0) | .name'

# 查找 6 个月未更新的仓库
gh repo list --json name,pushedAt,isArchived \
  --jq '.[] | select(.isArchived==false) |
  select(.pushedAt < (now - 15780000 | strftime("%Y-%m-%dT%H:%M:%SZ"))) | .name'
```

### 2. Memory Map 同步
检查 Profile README 中的 Memory Map 是否与实际仓库一致，新增/删除/归档的仓库需要同步更新。

### 3. 记忆蒸馏
- 回顾 `clawd-daily` 近一个月的日志，提炼 3-5 条关键认知
- 检查 `memory-learning` 类仓库，将碎片信息合并为结构化文档

---

## 命名规范

- **统一 `kebab-case`**：`my-project-name`
- **可选命名前缀**：
  - `clawd-*` / `clawdbot-*` — Clawd/OpenClaw 生态
  - 无前缀 — 通用工具/知识

---

## 参考文献

### Agent Memory
- [Memory in the Age of AI Agents (arXiv 2512.13564)](https://arxiv.org/abs/2512.13564) — 最全面的 Agent Memory 综述
- [A-MEM: Agentic Memory (arXiv 2502.12110)](https://arxiv.org/abs/2502.12110) — 将 Zettelkasten 应用于 Agent Memory
- [CoALA: Cognitive Architectures for Language Agents](https://arxiv.org/html/2309.02427v3) — 认知架构四分法
- [Letta (MemGPT)](https://github.com/letta-ai/letta) — OS 启发的 Agent Memory 框架
- [Mem0](https://github.com/mem0ai/mem0) — 统一记忆层
- [ICLR 2026 MemAgents Workshop](https://openreview.net/pdf?id=U51WxL382H) — Agent Memory 成为独立研究方向

### 个人知识管理
- [PARA Method (Forte Labs)](https://fortelabs.com/blog/para/) — 按行动力分类
- [Building a Second Brain](https://www.buildingasecondbrain.com/) — CODE 工作流
- [Andy Matuschak — Evergreen Notes](https://notes.andymatuschak.org/Evergreen_notes) — 原子化常青笔记
- [Zettelkasten.de](https://zettelkasten.de/overview/) — 卡片盒笔记法

### GitHub 知识管理
- [Foam](https://github.com/foambubble/foam) — VS Code + GitHub 知识管理
- [Quartz](https://github.com/jackyzha0/quartz) — Obsidian → 网站发布
- [jbranchaud/til](https://github.com/jbranchaud/til) — TIL 模式典范

---

*最后更新：2026-03-04*
*综合 Agent Memory 研究 + PARA/Second Brain/Zettelkasten 方法论*
*由 Claude Code 多 Agent 协作研究并生成*
