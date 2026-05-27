# scholar-search

面向计算机学科研究生的全能学术搜索与评估 Skill，7种模式 + 3项知识增强 + 阅读清单持久化。

## 文件结构

```
scholar-search/
├── SKILL.md                          # 主 Skill 文件（含兼容性元数据）
├── references/
│   ├── ccf-rankings.md               # CCF 第七版（2026）分级速查
│   ├── search-patterns.md            # 搜索语法与模式速查
│   └── platform-adapter.md           # 多平台适配指南
├── CHANGELOG.md                      # 版本更新日志
├── LICENSE                           # MIT
└── README.md
```

## 七种模式

| 模式 | 功能 | 示例 |
|------|------|------|
| **C** 团队搜索 | 团队结构 + 产出模式 + 定位分析 | "分析一下 XX 课题组" |
| **D** 方向发现 | 四级发散搜索 + 必读论文 + 代码 + 入门路径 | "我研一想做深度哈希，该读什么？" |
| **E** 复现评估 | 代码质量 + 硬件需求 + 性价比评分 | "这篇论文代码能跑吗？" |
| **F** 基准追踪 | 标准数据集 + SOTA + 天花板判断 | "这个方向 SOTA 多少？" |
| **G** 招生匹配 | 招生导师 + 课题组风格 + 择导建议 | "做 XX 方向的老师谁在招生？" |
| **H** Socratic引导 | 5 层对话：模糊想法 → 行动计划 | "我对 XX 有兴趣但不知研究什么" |
| **I** 🆕 资源驱动规划 | 有什么数据/GPU → 能做什么 → 论文推荐 | "我手上有XX数据，能做什么方向？" |

## 特色功能

- **搜索前追问** — 模式 D/I 开始前先了解用户的技术栈/GPU/目标，精准推荐
- **阅读清单持久化** — 推荐论文后可保存到本地 `~/.claude/scholar-reading-list-[方向].md`，后续对话追踪进度
- **四级发散搜索** — 模式 D 不再窄化推荐：同领域 → 同类问题×其他文字 → 通用方法 → 跨域启发
- **所有推荐附链接** — arXiv/DOI/GitHub 必填，可直接点击验证

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

```bash
git clone https://github.com/aa565645/scholar-search.git ~/.claude/skills/scholar-search/
# 重启 Claude Code 即可触发
```

### OpenAI Codex

| 能力 | 内置工具 | 说明 |
|------|:---:|------|
| 网页搜索 | `web_search` | 内置，无需额外安装 |
| 网页抓取 | `fetch` | 内置 |
| 命令行 | `bash` | 内置 |

```bash
git clone https://github.com/aa565645/scholar-search.git ~/.codex/skills/scholar-search/
```

> 模型自动将 WebSearch → web_search，WebFetch → fetch 适配，无需修改 SKILL.md。

### 纯 API 环境

参考 `references/platform-adapter.md`。

---

## 版本

v3.1 — 详见 [CHANGELOG.md](CHANGELOG.md)
