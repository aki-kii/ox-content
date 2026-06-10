---
title: Excluding Files
description: Skip template files and drafts from page generation, navigation, and search.
---

# Excluding Files

By default every Markdown file under `srcDir` is processed as a page. Use `exclude` to
skip files such as templates, partials, or drafts. Matched files are excluded from page
generation, navigation, and search indexing.

```ts
import { oxContent } from "@ox-content/vite-plugin";

export default {
  plugins: [
    oxContent({
      srcDir: "content",
      exclude: ["**/_*.md", "drafts/**"],
    }),
  ],
};
```

Patterns are matched against paths relative to `srcDir` using POSIX-style separators,
so the same pattern works on every platform. The matcher uses `picomatch`, so all the
usual `*`, `**`, and brace patterns are supported.

Common use cases:

- `**/_*.md` — files that start with an underscore (Jekyll/Astro-style partials)
- `drafts/**` — entire `drafts/` directory
- `**/*.draft.md` — files with a `.draft.md` suffix
