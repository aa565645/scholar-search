# scholar-search

面向计算机学科研究生的全能学术搜索与评估 Skill，6种模式 + 3项知识增强。

## 文件结构

```
scholar-search/
├── SKILL.md              # 主 Skill 文件（300 行，6 种模式）
├── references/
│   ├── ccf-rankings.md   # CCF 第七版（2026）分级速查
│   └── search-patterns.md # 搜索模式与语法速查
├── LICENSE               # MIT
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

## 安装

```bash
git clone https://github.com/aa565645/scholar-search.git ~/.claude/skills/scholar-search/
```

或直接将 `SKILL.md` 放入任意 Claude Code skills 目录。

## 来源

与 Claude Code 多轮迭代开发（v3.0），从真实 CS 研究生需求出发。参考了 ustc-ai4science/academic-search 的工程化结构。
