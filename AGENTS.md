# Agent Guide

This repository stores blog content and content-owned static assets. Site runtime, rendering, build, publishing, and deployment logic belong in the separate blog engine repository.

## Document review workflow

Use DevTool's stable `document_context` capability as the normal path for understanding long Markdown documents.

For a whole-document review:

1. Call `document_context` with `review=true` to obtain the complete outline plus explicit review coverage.
2. Follow `next_cursor` until `complete=true`; each continuation returns exactly one top-level section body plus covered/remaining sections.
3. Make whole-document conclusions only after the traversal reports complete coverage.
4. Re-read only affected sections after edits; do not use one large raw read as the primary understanding mechanism for long articles.
5. Keep structural claims grounded in returned outline, exact ranges, and review coverage.

For a focused lookup, use `section` with `include_content=true`. For short focused edits, a direct file read is acceptable when the full relevant context fits comfortably in one read.

When article review depends on surrounding content, use `related=true` on the initial `document_context` call. This exposes deterministic relationships such as the parent Series, ordered sibling Articles, Project links, explicit related Notes, and configured Note scopes.

Use the relationship graph for discovery, then read only the related documents needed for the review objective. Do not ingest every related Note body automatically.

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
  ├─ document-structure service
  │    └─ configured document provider
  └─ document-relations service
       └─ configured relation provider
```

Provider choice belongs in `.devtool.toml`. Agent instructions must not depend on Goldmark, `document.relations.content`, Marksman, Serena, or another concrete provider.

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
