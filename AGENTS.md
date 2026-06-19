# 本项目目标

写作一本解释人类社会发展的经济学著作。

核心问题：

为什么生产力决定组织形态？

为什么组织竞争推动历史发展？

为什么生产循环是社会演化的核心？

---

# 基础公理

A1:
组织是人类社会的基本竞争单元。

A2:
组织间存在资源竞争。

A3:
生产力决定组织可获取资源规模。

A4:
生产循环能够强化生产力。

A5:
正循环组织最终扩张。

---

# 写作原则

1. 不允许空泛论述
2. 每个命题必须有历史案例
3. 每个章节必须回归核心公理
4. 所有反例必须记录
5. 先寻找反例，再寻找支持证据

---

# 输出要求

任何论证必须包含：

- 命题
- 推导过程
- 支持证据
- 反对意见
- 适用边界

---

# OpenCode 工作流

## 可用技能

本项目的 `.opencode/skills/` 包含四个写作专用 skill，请在对应场景加载：

| Skill | 加载指令 | 适用场景 |
|-------|---------|---------|
| book-chapter-brainstorming | `skill("book-chapter-brainstorming")` | 写作前规划章节结构、设计论证链 |
| book-research | `skill("book-research")` | 查找历史证据、反例、定量数据 |
| book-chapter-writing | `skill("book-chapter-writing")` | 按五要素格式撰写章节 |
| book-chapter-review | `skill("book-chapter-review")` | 审查章节是否符合写作原则 |

## 可用 Agent

共 7 个 agent，按 `@agent名` 调用：

| Agent | 职责 | 调用时机 |
|-------|------|---------|
| `@philosopher` | 构建理论体系：审计公理集、推导命题、发现逻辑漏洞 | 写作前、重大论证前 |
| `@historian` | 找跨文明历史案例（古罗马、英国、美国、中国、苏联等） | 需要历史证据时 |
| `@opponent` | **最重要的角色**：专门找反例，不找任何支持证据 | 每个命题写完后必须测试 |
| `@editor` | 统一术语风格、查重复、检查章节间一致性 | 批量修改或全文统稿 |
| `@book-researcher` | 资料查找与整理（web 搜索+论文搜索） | 需要查资料时 |
| `@book-writer` | 按五要素格式撰写章节 | 写作阶段 |
| `@book-reviewer` | 综合审查（调用 editor + opponent 汇总意见） | 写完每个章节后 |

## 可用 MCP 服务器

在 `opencode.jsonc` 的 `mcp` 段已配置，默认 `enabled: false`，需要时手动改为 `true`：

| MCP | 连接对象 | 用途 | 前置条件 |
|-----|---------|------|---------|
| `research-papers` | arXiv / Semantic Scholar / OpenAlex | 搜索学术论文、引用关系、全文下载 | 安装 `uvx` |
| `zotero` | Zotero 桌面版 | 管理文献库、生成引用、读 PDF 注释 | Zotero 运行中+本地 API 开启 |
| `obsidian` | Obsidian 知识库 | 做知识图谱、跨笔记链接、思维导图 | 安装 `obsidian-local-rest-api` 插件 |

推荐在写作中这样使用 MCP：
- 需要学术文献支撑 → 启用 `research-papers`，用 `@book-researcher` 代理搜索
- 需要管理引用 → 启用 `zotero`，自动获取格式化的 BibTeX 引用
- 需要连接概念图谱 → 启用 `obsidian`，在 Obsidian 中建立术语网络

## 可用命令

- `/write-chapter <章节名>` — 含哲学审查+反例测试+编辑统一的完整流程
- `/review-chapter <章节名>` — 四重审查（逻辑/反例/风格/写作原则）
- `/research-topic <主题>` — 跨文明案例+反例+学术论文
- `/check-progress` — 进度统计+四 agent 质量评估
- `/stress-test` — 对全书所有命题做反例压力测试

## 推荐写作流程（完整版）

```
写前规划：
  skill("book-chapter-brainstorming")  → 章节设计
  @philosopher                         → 逻辑审计

证据收集：
  @historian                           → 找历史案例
  @opponent                            → 找反例（先找反例！）
  @book-researcher + research-papers MCP → 学术论文

正式写作：
  skill("book-chapter-writing")        → 撰写正文
  @editor                              → 风格统一

审查验证：
  @opponent                            → 再次反例检查
  @book-reviewer                       → 综合审查
```

## 项目结构

```
ThinkAboutCommunism/
├── opencode.jsonc              # 项目级配置（agent + MCP + command）
├── AGENTS.md                   # 本文件：项目指令
├── contents.md                 # 全书目录结构
├── .opencode/
│   ├── skills/                 # 自定义 skill
│   │   ├── book-chapter-brainstorming/SKILL.md
│   │   ├── book-research/SKILL.md
│   │   ├── book-chapter-writing/SKILL.md
│   │   └── book-chapter-review/SKILL.md
│   └── agents/                 # agent 定义文件
│       ├── book-researcher.md
│       ├── book-writer.md
│       └── book-reviewer.md
├── docs/                       # 写作计划和笔记
├── 资料/                       # 按命题组织的储备材料
│   ├── 01-生产循环基础理论/
│   ├── 02-历史演化/
│   ├── 03-组织与生产关系/
│   └── 04-后资本主义/
├── ch00-导论.md ~ ch20-*.md    # 各章书稿
└── 结论.md