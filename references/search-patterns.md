# 搜索模式速查

## 会议官网直搜（2026新录用论文）

```
site:cvpr.thecvf.com "[方向关键词]" 2026
site:iclr.cc "[方向关键词]" 2026
site:ojs.aaai.org "[方向关键词]" 2026
site:openreview.net "[方向关键词]" 2026
site:proceedings.mlr.press "[方向关键词]" 2026
site:dl.acm.org "[方向关键词]" 2026
```

## GitHub 代码搜索

```
# 搜论文代码（优先级低——论文标题搜命中率低）
"[论文标题关键词]" site:github.com

# 搜作者代码（优先级中）
"[作者英文名]" site:github.com language:python

# 搜实验室组织（优先级高——lab org 搜到就是全套代码）
"[方向关键词]" org:"GitHubOrgName" in:name

# 搜 awesome list
"awesome [方向]" site:github.com stars:>10

# 搜特定文件判断复现难度
"[论文名]" filename:requirements.txt
"[论文名]" filename:Dockerfile
"[论文名]" filename:README.md
```

## 招生信息搜索

```
# 中文优先（命中率远高于英文）
"[研究方向]" 招生 2026 OR 2027 研究生

# 导师个人主页
site:github.io "[导师名]" recruitment OR join OR 招生

# 学校官网
site:edu.cn "[导师名]" "研究生" OR "硕士" OR "博士"
```

## DBLP 消歧模式

遇到同名研究者时的交叉验证搜索：
```
# 验证归属
"[作者英文名]" "[单位英文名]" site:dblp.org

# 验证合作网络
"[作者英文名]" "[合作者英文名]" paper OR publication
```

## 综述搜索

```
# 英文综述
"[方向关键词]" survey OR review 2024 2025 site:dl.acm.org
"[方向关键词]" survey OR review 2024 2025 site:ieeexplore.ieee.org

# 中文综述
"[方向关键词]" 综述 OR 综述 2024 2025 site:cnki.net
```

## 引文链追踪

```
# 向后追踪（这篇引用了谁？）
Semantic Scholar API: /paper/{paper_id}/references

# 向前追踪（谁引用了这篇？）
Semantic Scholar API: /paper/{paper_id}/citations
Google Scholar: "cited by" count
```
