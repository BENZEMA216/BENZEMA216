# GitHub Memory System — 维护指南

> 这份文档定义了我的 GitHub 作为"外部大脑"的组织规范和维护方式。
> 每次新建仓库、整理仓库时，请参照此文档执行。

---

## 架构总览

```
BENZEMA216 (Profile README) ← 总索引入口
│
├── 🧠 Identity       — 身份、站点、知识库
├── 🦞 Agent Ecosystem — OpenClaw / Clawd 产品线
├── 🔧 Skills & Plugins — Claude Code 技能与工具
├── 📓 Learnings       — 踩坑、认知、反思记忆
├── ⚙️ Infrastructure  — 基础设施与服务
└── 📦 Archived        — 归档的旧项目与 Fork
```

---

## Topic 标签体系

每个仓库**必须**打上对应的分类 Topic，这是记忆系统的索引基础。

| Topic | 含义 | 示例 |
|-------|------|------|
| `memory-identity` | 身份类：Profile、个人站点、笔记库 | BENZEMA216, BENZEMA-vault |
| `memory-agent` | Agent 生态：OpenClaw/Clawd 相关产品 | creo, HomForClawd, xian-home |
| `memory-skill` | 技能/插件：Claude Code 插件、工具 | music-analyzer, chatshot |
| `memory-learning` | 认知记忆：踩坑记录、复盘、研究 | openclaw-pitfalls, tradingcoach |
| `memory-infra` | 基础设施：RSS、监控、支付等服务 | rss-reader, web3-timeline |

**查看某一分类的所有仓库：**
```
https://github.com/BENZEMA216?tab=repositories&q=topic:memory-agent
```

---

## 新建仓库 Checklist

每次创建新仓库时，确保完成以下步骤：

- [ ] **命名**：使用 `kebab-case`（如 `my-new-tool`），不用下划线或大驼峰
- [ ] **描述**：填写一句话描述，中英文皆可，格式 `Name — 功能说明`
- [ ] **Topic**：打上对应的 `memory-*` 分类标签
- [ ] **可见性**：确认 public/private 是否正确（含敏感信息的设为 private）
- [ ] **README 索引**：将新仓库添加到 Profile README 的 Memory Map 对应分类中

---

## 定期维护（建议每月一次）

### 1. 清理检查
- 超过 6 个月无更新的仓库 → 考虑归档（`gh repo archive`）
- Fork 仓库如果没有自己的修改 → 删除或归档
- 仓库名带 "private" 但实际公开的 → 检查可见性

### 2. 描述与标签补全
```bash
# 查找没有 description 的仓库
gh repo list --json name,description --jq '.[] | select(.description == "" or .description == null) | .name'

# 查找没有 memory-* topic 的仓库
gh repo list --json name,repositoryTopics --jq '.[] | select((.repositoryTopics | map(.name) | map(select(startswith("memory-"))) | length) == 0) | .name'
```

### 3. Memory Map 同步
检查 Profile README 中的 Memory Map 是否与实际仓库一致，新增/删除/归档的仓库需要同步更新。

---

## 归档规则

| 条件 | 操作 |
|------|------|
| Fork 且 > 6 个月无修改 | `gh repo archive` |
| 原创但已弃用 | 归档，保留描述作为记忆 |
| 空仓库、无意义仓库 | 直接删除 |
| 归档后的仓库 | 从 Memory Map 中移除，不再打 `memory-*` 标签 |

---

## 命名规范

- **统一使用 `kebab-case`**：`my-project-name`
- **避免**：下划线 `my_project`、大驼峰 `MyProject`、特殊字符 `-`
- **可选前缀**：
  - `clawd-*` — Clawd/OpenClaw 生态项目
  - `clawdbot-skill-*` — Clawdbot 技能插件

---

## 快速操作命令

```bash
# 给仓库打标签
gh repo edit BENZEMA216/<repo> --add-topic memory-agent

# 修改描述
gh repo edit BENZEMA216/<repo> --description "New description"

# 归档仓库
gh repo archive BENZEMA216/<repo> --yes

# 设为私有
gh repo edit BENZEMA216/<repo> --visibility private

# 查看所有仓库及分类
gh repo list --limit 100 --json name,repositoryTopics,description --jq '.[] | [.name, (.repositoryTopics | map(.name) | join(",")), .description // ""] | @tsv'
```

---

*最后更新：2026-03-04*
*由 Claude Code 多 Agent 协作整理生成*
