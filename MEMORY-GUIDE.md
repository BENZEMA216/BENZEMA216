# GitHub 记忆系统

> 从我们的实际工作中长出来的记忆管理方式。
> 每次 Claude Code session 初始化时，从这里开始。

---

## 核心原则

**记忆按温度分层，按项目组织，技能跟着项目走。**

---

## 一、记忆温度分层

### 🔴 热记忆 — 当前工作状态

实时更新，每次 session 的起点。

- **载体**：项目根目录的 `active_context.md` 或 `CLAUDE.md`
- **内容**：当前在做什么、优先级、阻塞项、最近的关键决策
- **更新时机**：对话中达成共识或形成结论时，直接写入
- **示例**："即梦 Agent RL 第 3 轮 A/B 进行中，重点观察创意多样性指标"

### 🟡 温记忆 — 项目文档

定期整理，项目推进的过程记录。

- **载体**：各项目 Repo 中的 `docs/` 或独立文档
- **内容**：需求分析、技术方案、产品决策链、踩坑记录
- **更新时机**：完成一个阶段、做了重要决策、踩了坑
- **关键**：保留推导过程，不只存结论

### 🔵 冷记忆 — 长期沉淀

归档存储，需要时检索。

- **载体**：BENZEMA-vault（Obsidian）
- **内容**：方法论总结、行业研究、阅读笔记、竞品分析
- **更新时机**：定期从热/温记忆中蒸馏
- **格式**：Obsidian 双链语法（`[[Link]]`）+ YAML Front Matter

### 温度流转

```
输入（rss-reader / 阅读 / 调研）
  ↓ 捕获
冷记忆（Obsidian 归档）
  ↓ 激活（与当前项目相关时）
温记忆（项目 docs/）
  ↓ 聚焦（正在做的事）
热记忆（active_context.md）
  ↓ 完成后
温记忆（项目文档沉淀）→ 冷记忆（长期归档）
```

---

## 二、项目记忆

每个方向是一个独立的项目组，技能作为子结构挂在项目下。

### 即梦创作 Studio

字节跳动即梦 AI 的创作工具链。

| 仓库 | 角色 |
|------|------|
| [Dremaina-AGENT-2026](https://github.com/BENZEMA216/Dremaina-AGENT-2026) | 主项目 |
| [music-analyzer](https://github.com/BENZEMA216/music-analyzer) | 技能：音频 → Dreamina Prompt |
| [creative-think](https://github.com/BENZEMA216/creative-think) | 技能：Brief → 创意推理链 → Prompt |
| [dreamina-claude-skills](https://github.com/BENZEMA216/dreamina-claude-skills) | 技能集 |

### OpenClaw 生态

AI Agent Gateway 部署与产品。

| 仓库 | 角色 |
|------|------|
| [xian-home](https://github.com/BENZEMA216/xian-home) | 弦的信号空间（Web 入口） |
| [HomForClawd](https://github.com/BENZEMA216/HomForClawd) | iOS 客户端 |
| [Creative-Cowork](https://github.com/BENZEMA216/Creative-Cowork) | 协作平台 |
| [openclaw-pitfalls](https://github.com/BENZEMA216/openclaw-pitfalls) | **技能：部署经验库**（每次新开 OpenClaw 时加载） |
| [agent-observability-tools](https://github.com/BENZEMA216/agent-observability-tools) | 观测工具 |

### Agent Identity（实验方向）

让 AI Agent 拥有自主视觉表达。

| 仓库 | 角色 |
|------|------|
| [agent-form](https://github.com/BENZEMA216/agent-form) | agentavatar.dev 网站 + AVI 协议 |
| [agent-identity-docs](https://github.com/BENZEMA216/agent-identity-docs) | 产品思考文档 |

### creo（实验方向）

品牌美学记忆持久化平台。Reflect → Record → Reuse。

| 仓库 | 角色 |
|------|------|
| [creo](https://github.com/BENZEMA216/creo) | 品牌档案 + Visual DNA + 资产索引 |

### tradingcoach（独立项目）

| 仓库 | 角色 |
|------|------|
| [tradingcoach](https://github.com/BENZEMA216/tradingcoach) | AI 交易复盘分析平台 |

---

## 三、独立技能

跨项目通用，不隶属于任何项目组。

| 仓库 | 用途 |
|------|------|
| [chatshot](https://github.com/BENZEMA216/chatshot) | AI 对话截图（跨 ChatGPT/Claude/豆包） |
| [self-purify](https://github.com/BENZEMA216/self-purify) | Claude Code 安全审计与自净化 |
| [rss-reader](https://github.com/BENZEMA216/rss-reader) | 信息输入管道（RSS → AI 摘要 → 飞书） |

---

## 四、身份层

| 仓库 | 用途 |
|------|------|
| [BENZEMA216](https://github.com/BENZEMA216/BENZEMA216) | Profile README + Memory Map + 本文档 |
| [BENZEMA216.github.io](https://github.com/BENZEMA216/BENZEMA216.github.io) | 个人网站 |
| [BENZEMA-vault](https://github.com/BENZEMA216/BENZEMA-vault) | Obsidian 笔记库（冷记忆归档） |

---

## 五、日常操作

### 对话中达成结论时

→ 写入当前项目的 `active_context.md`

### 完成一个项目阶段时

→ 更新项目 `docs/`，保留决策推导过程

### 踩了一个坑时

→ 在对应项目仓库追加记录（如 openclaw-pitfalls 的 PIT-XXX.yaml）

### 新开一个 OpenClaw 部署时

→ 加载 openclaw-pitfalls 技能，确保历史经验可用

### 读到有价值的内容时

→ 写入 BENZEMA-vault，用 `[[双链]]` 关联相关笔记

### 每周/定期

→ 检查热记忆是否需要降温到温/冷
→ 检查温记忆中是否有值得蒸馏到冷记忆的内容

### 每月

```bash
# 哪些仓库缺描述？
gh repo list --json name,description \
  --jq '.[] | select(.description == "" or .description == null) | .name'

# 哪些仓库没有 memory-* 标签？
gh repo list --json name,repositoryTopics,isFork,isArchived \
  --jq '.[] | select(.isFork==false and .isArchived==false) |
  select((.repositoryTopics | map(.name) | map(select(startswith("memory-"))) | length) == 0) | .name'
```

---

## 六、新建仓库 Checklist

- [ ] 命名：`kebab-case`
- [ ] 描述：`Name — 做什么`
- [ ] Topic：对应的 `memory-*` 标签
- [ ] 归属：明确属于哪个项目组，还是独立技能
- [ ] 如果是技能：写好 SKILL.md，告诉 Agent 用什么工具做什么
- [ ] 更新 Profile README 的 Memory Map

---

*最后更新：2026-03-04*
