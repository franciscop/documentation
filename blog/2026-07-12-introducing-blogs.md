---
title: Your blog is just markdown now
description: Maintaining a blog no longer means a separate site, a static site generator, or deploys. Just write markdown files in your project and push.
date: 2026-07-12
---

# Your blog is just markdown now

Keeping a blog alive is usually where good intentions go to die. You set up a separate site, wrestle with a static site generator, learn its templating language, wire up deploys, and a month later writing a single post feels like a chore you keep putting off.

Documentation Page changes that. Your blog now lives **right next to your code**, as plain markdown files in your project. To publish, you write a `.md` file and push. That's the whole workflow.

## Why this is great

- **No new tools.** It's the same markdown you already write for your readme and docs. No build step, no config, nothing new to learn.
- **It lives with your project.** Posts sit in a `blog/` folder in your repo, so they're versioned, reviewable in pull requests, and never drift out of sync with the thing they're about.
- **Write and forget.** Push a file and it's live, with no separate deploy, no dashboard, no hosting to babysit.
- **It just looks right.** Every post gets a clean page and full social cards generated automatically, so sharing a link looks professional with zero effort.

## Genuinely low effort

Here's a complete post:

```markdown
# We shipped dark mode

It's been the most requested feature for months, and today it's here...
```

That's it. No front matter required: the title comes from the heading, the description and preview image fall back to sensible defaults, and the date can come from the file name. Add those fields only when you want to override them.

The best blog is the one you'll actually keep writing. Now maintaining yours is as easy as dropping a markdown file into your project. Go write something.
