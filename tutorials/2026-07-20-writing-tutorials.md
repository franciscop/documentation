---
title: Add tutorials to your project
description: Tutorials work just like the blog. Drop markdown files in a tutorials folder in your project, push, and each one becomes a clean, shareable page.
date: 2026-07-20
social: /assets/preview.png
---

# Add tutorials to your project

Docs explain what your project does. Tutorials walk someone through doing a real thing with it, start to finish. Now you can publish them the same way you publish everything else here: as plain markdown that lives next to your code.

## How it works

Create a `tutorials/` folder in your project and add a markdown file for each guide. Push, and every file becomes its own page, with a `/tutorials` index that lists them all. There is no build step and nothing new to configure.

```markdown
# Deploy your first site in 5 minutes

Start by creating an account, then point your repository at...
```

That is a complete tutorial. The title comes from the first heading, and the description and preview image fall back to sensible defaults, so the social card looks right with no extra work.

## Ordering and front matter

Tutorials are sorted by file name, so a numeric prefix keeps a series in the right order:

```
tutorials/
  1-getting-started.md
  2-configuration.md
  3-going-to-production.md
```

Want to override the defaults? Add front matter at the top of any file:

```markdown
---
title: Going to production
description: A checklist for your first real deploy.
tag: Guide
date: 2026-07-20
---
```

## Point somewhere else

By default we look for a `tutorials/` folder, but you can set the `tutorials` option in your configuration to a different folder or a specific list of files, exactly like the `blog` option. Write the guide, push, and it is live.
