# Changelog

## v3.1 (2026-05-27)

### feat: 搜索前追问
- 模式 D 开始前先问研几/技术栈/GPU/目标
- 根据回答自动调整推荐方向

### feat: 阅读清单持久化
- 推荐论文后可选择保存到本地 `~/.claude/scholar-reading-list-[方向].md`
- 每篇附 arXiv/DOI 链接 + 复选框
- 后续对话可读回清单追踪阅读进度

### feat: 四级发散搜索
- 层级1 同领域直搜 → 层级2 同类问题跨文字 → 层级3 通用方法 → 层级4 跨域启发
- 解决之前"用户说满文只推荐满文+甲骨文"的窄化问题

### feat: 所有推荐附链接
- 模式 D/E/F 的所有论文/代码/数据集必须附可点击 URL

### feat: 平台适配文档
- 新增 `references/platform-adapter.md`
- Claude Code / Codex / Cursor / 纯API 四种环境的安装与适配指南

### feat: CCF分级速查 + 搜索语法速查
- 新增 `references/ccf-rankings.md`（第七版，2026）
- 新增 `references/search-patterns.md`

## v3.0 (2026-05-26)

### feat: 初始发布
- 6种模式：C团队搜索 / D方向发现 / E复现评估 / F基准追踪 / G招生匹配 / H Socratic引导
- 3项知识增强：三遍阅读法 / 引文链追踪 / 来源质量矩阵
- 降级策略表 + GitHub搜索语法 + 11条陷阱速查
- MIT 开源
