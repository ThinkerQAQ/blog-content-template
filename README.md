# ThinkerQAQ Blog Content Template

Example content repository for [ThinkerQAQ Blog](https://github.com/ThinkerQAQ/ThinkerQAQ.github.io).

Clone it next to the public engine:

```bash
git clone https://github.com/ThinkerQAQ/ThinkerQAQ.github.io.git
git clone https://github.com/ThinkerQAQ/blog-content-template.git blog-content
```

The two repositories should look like this:

```text
blog/
├── ThinkerQAQ.github.io/
└── blog-content/
```

## Repository layout

```text
src/content/
├── articles/
├── notes/
├── note-translations/
├── projects/
└── series/

public/media/
└── articles/
```

`src/content/**` contains the blog content. `public/media/**` contains assets referenced by that content.

This repository only provides sample content. The Astro site, schemas, validation, BlogCTL, build logic, and deployment live in [ThinkerQAQ.github.io](https://github.com/ThinkerQAQ/ThinkerQAQ.github.io).
