# scholar-search

面向计算机学科研究生的全能学术搜索与评估 Skill，6种模式 + 3项知识增强。

## 文件结构

```
scholar-search/
├── SKILL.md                          # 主 Skill 文件（含兼容性元数据）
├── references/
│   ├── ccf-rankings.md               # CCF 第七版（2026）分级速查
│   ├── search-patterns.md            # 搜索语法与模式速查
│   └── platform-adapter.md           # 多平台适配指南
├── LICENSE                           # MIT
└── README.md
```

## 六种模式

| 模式 | 功能 | 示例 |
|------|------|------|
| **C** 团队搜索 | 团队结构 + 产出模式 + 定位分析 | "分析一下 XX 课题组" |
| **D** 方向发现 | 必读论文 + 核心研究者 + 代码 + 入门路径 | "我研一想做深度哈希，该读什么？" |
| **E** 复现评估 | 代码质量 + 硬件需求 + 性价比评分 | "这篇论文代码能跑吗？" |
| **F** 基准追踪 | 标准数据集 + SOTA + 天花板判断 | "这个方向 SOTA 多少？" |
| **G** 招生匹配 | 招生导师 + 课题组风格 + 择导建议 | "做 XX 方向的老师谁在招生？" |
| **H** Socratic引导 | 5 层对话：模糊想法 → 行动计划 | "我对 XX 有兴趣但不知研究什么" |

## 知识增强

- **三遍阅读法** — Survey → Understanding → Deep Dive
- **引文链追踪** — 向前/向后引用分析定位根论文
- **来源质量矩阵** — 期刊/引用/复现/独立性/时效五维评估

---

## 安装

### Claude Code（原生支持）

**前置条件：**

| 插件/工具 | 用途 | 获取方式 |
|-----------|------|---------|
| **WebSearch** | 网页搜索（搜论文/学者/招生） | Claude Code 内置，或 MCP: `plugin_playwright` |
| **WebFetch** | 网页抓取（读个人主页/DBLP/GitHub） | Claude Code 内置，或 MCP: `plugin_context7` |
| **Bash** | 执行 git/curl/API 调用 | 系统自带 |
| **Agent** | 并行批量搜索（可选，加速用） | Claude Code 内置 |

**安装步骤：**

```bash
# 1. 确认 Claude Code 版本 >= 1.0
claude --version

# 2. 确认必要 MCP 插件已启用（在 settings.json 中）
#    "mcpServers": {
#      "plugin_playwright": { ... },    // WebSearch 能力
#      "plugin_context7": { ... }       // WebFetch 能力
#    }

# 3. 克隆 skill
git clone https://github.com/aa565645/scholar-search.git ~/.claude/skills/scholar-search/

# 4. 重启 Claude Code，输入 "分析一下 XX 课题组" 即可触发
```

### OpenAI Codex

**前置条件：**

| 能力 | Codex 内置工具 | 说明 |
|------|:---:|------|
| 网页搜索 | `web_search` | 内置，无需额外安装 |
| 网页抓取 | `fetch` | 内置，无需额外安装 |
| 命令行 | `bash` | 内置 |
| 并行搜索 | ❌ 不支持 Agent 模式 | 自动降级为串行搜索 |

**安装步骤：**

```bash
# 1. 确认 Codex 版本 >= 0.45.0
codex --version

# 2. 克隆 skill
git clone https://github.com/aa565645/scholar-search.git ~/.codex/skills/scholar-search/

# 3. 在 Codex 配置中注册 skill 路径（具体方式见 Codex 文档）
# 4. 重启 Codex。模型会自动将 WebSearch → web_search，WebFetch → fetch 适配
```

> Codex 无需修改 SKILL.md——模型会自动理解指令语义并调用自己的工具链。

### 纯 API 环境（无浏览器/Claude）

参考 `references/platform-adapter.md` 中的 API 映射表，可将搜索替换为：
- DBLP API → `https://dblp.org/search/publ/api`
- Semantic Scholar API → `https://api.semanticscholar.org`
- arXiv API → `https://export.arxiv.org/api/query`

---

## 来源

与 Claude Code 多轮迭代开发（v3.0），从真实 CS 研究生需求出发。参考了 ustc-ai4science/academic-search 的工程化结构。
