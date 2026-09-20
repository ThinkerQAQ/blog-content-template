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
│   └── series/
└── data/
    └── content-manifest.json

public/media/
└── articles/
```

仓库内已经放了一组最小示例，用来展示 Article、Note、Series、Project 以及中英文内容之间的关系。

与 Public Engine 一起使用：

```bash
git clone https://github.com/ThinkerQAQ/ThinkerQAQ.github.io.git
git clone https://github.com/ThinkerQAQ/blog-content-template.git blog-content
```

完整的运行和部署方式见 [ThinkerQAQ.github.io README](https://github.com/ThinkerQAQ/ThinkerQAQ.github.io#readme)。
