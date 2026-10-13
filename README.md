# ThinkerQAQ Blog Content Template

[ThinkerQAQ Blog](https://github.com/ThinkerQAQ/ThinkerQAQ.github.io) 的示例内容仓库。

它只保存内容和内容使用的静态资源，不包含 Astro、构建逻辑或部署代码。

## 目录结构

```text
src/
├── content/
│   ├── articles/
│   │   └── en/
│   ├── notes/
│   ├── note-translations/
│   │   └── en/
│   ├── projects/
│   ├── series/
│   ├── life/
│   └── workout-summaries/
└── data/
    └── content-manifest.json

public/media/
├── articles/
└── life/
```

仓库内提供 Article、Note、Series、Project 及中英文示例，另有**完全虚构的摄影生活记录与健身月度统计**。此仓库是演示数据的唯一维护位置；博客引擎不再携带另一份内容副本。

- `src/content/life/*.md`：摄影图文，含 1、4、9、12 张图片、长文案、草稿与年份归档示例。
- `public/media/life/`：对应的缩略图与原尺寸示例（均为合成图）。
- `src/content/workout-summaries/*.json`：按月聚合的虚构训练天数、时长和容量；不包含任何人的具体训练日、动作、重量或凭据。

全部健身样例带有 `"demo": true`。演示内容不应与私有 BlogContent 混用，也不应被描述为真实同步结果。

## DevTool V2

模板已经包含：

```text
.devtool.toml
AGENTS.md
```

DevTool 负责提供稳定的文档理解与 SCM 能力，仓库本身只保留配置：

```text
document_context
  ├─ document-structure
  │    └─ document.markdown.goldmark
  └─ document-relations
       └─ document.relations.content

scm_checkpoint / scm_publish
  -> scm.github
```

长 Markdown 的标准 Review 流程是：

```text
document_context(review=true)
  -> 完整 Outline + Coverage
  -> next_cursor
  -> 每次读取一个 bounded review unit
  -> covered / remaining
  -> complete=true
  -> 整篇结论
```

较大的 Section 会按照 Heading 层级递归拆分，并受 `review_max_lines` 控制。这样 Agent 不需要一次读取整篇长文，也不需要自己记忆“哪些章节已经看过”。当 Review 需要系列或笔记上下文时，初始调用加上 `related=true`，即可获得 Series、按顺序排列的 sibling Articles、Project 和 Note 关系图；具体相关文档正文仍按需读取。

整个 Agent 工作流仍然不依赖具体的 Markdown Parser、Relation Provider 或 LSP Provider。

首次使用时可以运行：

```bash
devtool config validate
devtool init
```

具体 Agent 工作约束见 [AGENTS.md](./AGENTS.md)。

## 与 Public Engine 一起使用

```bash
git clone https://github.com/ThinkerQAQ/ThinkerQAQ.github.io.git
git clone https://github.com/ThinkerQAQ/blog-content-template.git blog-content-template
```

完整的运行和部署方式见 [ThinkerQAQ.github.io README](https://github.com/ThinkerQAQ/ThinkerQAQ.github.io#readme)。
