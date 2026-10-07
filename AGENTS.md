# Agent Guide

This repository stores blog content and content-owned static assets. Site runtime, rendering, build, publishing, and deployment logic belong in the separate blog engine repository.

## Document review workflow

Use DevTool's stable `document_context` capability as the normal path for understanding long Markdown documents.

For a whole-document review:

1. Call `document_context` with the document path and no section content to obtain the complete outline, frontmatter, and exact section ranges.
2. Review each relevant top-level section with `section` and `include_content=true`.
3. Track coverage across all top-level sections before making whole-document conclusions.
4. Re-read only affected sections after edits; do not use one large raw read as the primary understanding mechanism for long articles.
5. Keep structural claims grounded in the returned outline and section ranges.

For short focused edits, a direct file read is acceptable when the full relevant context fits comfortably in one read.

## Content rules

- `src/content/**` is the source of truth for Articles, Notes, Series, and Projects.
- Keep Chinese and English counterparts aligned when both exist.
- Preserve frontmatter and series relationships.
- Do not introduce repository-local Markdown parsers, document-index scripts, or provider-specific Agent workflows. Generic document intelligence belongs in DevTool.
- Use Mermaid for topology, lifecycle, flow, and sequence diagrams when spatial relationships matter.
- Prefer direct technical prose over drafting-process narration such as “前面我们讲了” or “接下来再看”.

## DevTool architecture

This repository should remain configuration-only with respect to DevTool capabilities:

```text
document_context
  -> document-structure service
  -> configured document provider
```

Provider choice belongs in `.devtool.toml`. Agent instructions must not depend on Goldmark, Marksman, Serena, or another concrete provider.

## SCM workflow

When DevTool SCM tools are available, use:

```text
change one coherent thing
  -> scm_checkpoint
  -> continue
  -> concentrated verification
  -> scm_publish
```

Do not merge without explicit user approval.
