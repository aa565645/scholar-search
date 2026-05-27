# 平台适配说明

本 Skill 的核心逻辑（模式定义、搜索策略、输出模板、降级规则）是**平台无关的**。
不同平台需要映射到各自的工具链。

## 工具依赖

| 能力 | Claude Code | OpenAI Codex CLI | Cursor / Windsurf | 说明 |
|------|:---:|:---:|:---:|------|
| 网页搜索 | `WebSearch` | `web_search` | `@web` / `RAG_search` | 核心：搜论文/搜人/搜招生 |
| 网页抓取 | `WebFetch` | `fetch` | 内置 browser | 核心：读个人主页/读DBLP |
| 并行搜索 | `Agent` (background) | 自定义 subagent | 不支持 | 可选：加速批量搜索 |
| GitHub API | `Bash` + gh/curl | `bash` | 内置 terminal | 核心：搜代码仓库 |

## Claude Code（原生）

本 Skill 为 Claude Code 原生设计。所有模式直接使用 `WebSearch` 和 `WebFetch`，
通过后台 `Agent` 实现并行批量搜索。

**安装：**
```bash
git clone https://github.com/aa565645/scholar-search.git ~/.claude/skills/scholar-search/
```

## OpenAI Codex CLI

Codex 使用 `web_search` 替代 `WebSearch`，使用 `fetch` 替代 `WebFetch`。
核心工作流指令**无需修改**——Skill 中描述的是搜索目标而非具体工具名。

**需要适配的部分：**

| Claude Code 写法 | Codex 等价写法 |
|------|------|
| `WebSearch(query="...")` | `web_search(query="...")` |
| `WebFetch(url="...")` | `fetch(url="...")` |
| 后台 Agent 并行搜索 | 串行搜索 or 手动并发 |
| `Bash` 执行 git/curl | `bash` 执行相同命令 |

**安装（Codex）：**
```bash
git clone https://github.com/aa565645/scholar-search.git ~/.codex/skills/scholar-search/
```

在 Codex 中，模型会自动理解 Skill 的语义并用 `web_search` + `fetch` 执行。

## Cursor / Windsurf

这些 IDE 内置了网页搜索和浏览器能力。将 `SKILL.md` 作为 system prompt 的
补充指令注入即可。需要手动调整的：

- `WebSearch` → `@web` 或内置搜索
- `Agent` 并行 → 单步串行（Cursor 不支持子 agent）

## 纯 API 模式（无浏览器环境）

如果运行环境中没有浏览器，所有搜索可通过以下 API 替代：

| 能力 | API 替代方案 |
|------|------------|
| DBLP 搜索 | `https://dblp.org/search/publ/api?q=NAME&format=json` |
| Semantic Scholar | `https://api.semanticscholar.org/graph/v1/paper/search?query=...` |
| arXiv | `https://export.arxiv.org/api/query?search_query=...` |
| GitHub 搜索 | `https://api.github.com/search/repositories?q=...` |
| Papers with Code | `https://paperswithcode.com/api/v1/papers/?q=...` |
| 招生信息 | 无法 API 替代——只能从论文作者 affiliation 推断 |

这是 academic-search (ustc-ai4science) 采用的方案，适合有稳定 API 访问的环境。

## 推荐策略

- **Claude Code**：直接用，原生支持，效果最好
- **Codex**：直接导入，模型会自动适配工具名，核心逻辑不变
- **Cursor/Windsurf**：将 SKILL.md 注入为 system context，搜索策略不变
- **纯 API 环境**：参考 academic-search 的 API 调用模式，我们 Skill 的工作流逻辑仍可复用
