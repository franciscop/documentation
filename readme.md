# Documentation Page content

The content behind [documentation.page](https://documentation.page): its documentation,
blog and tutorials. Everything here is plain markdown, and it is also a working example of
what Documentation Page builds from a repository.

## Layout

| Path                      | What it becomes                                    |
| ------------------------- | -------------------------------------------------- |
| `documentation.page.json` | The site configuration: name, menu, and page order |
| `documentation/`          | The pages under `/documentation`                   |
| `documentation/home.html` | The front page at `/`                              |
| `blog/`                   | The posts under `/blog`, newest first              |
| `tutorials/`              | The posts under `/tutorials`                       |

## Editing

Every page is a markdown file, so a pull request is all it takes to fix a typo or add a
section. Pages appear in the order given by `documentation` in the configuration, and their
headings become the sidebar automatically.

Blog and tutorial posts are read straight from their folder, and the date comes from the
filename (`2026-07-26-my-post.md`). Front matter sets the title, description and share
image when you want something other than the defaults:

```markdown
---
title: Your post title
description: One line, used for search results and share cards
image: /blog/your-post.png
---
```

A post's share card lives next to it with the same basename, so `blog/my-post.md` pairs
with `blog/my-post.png` at 1200x630.

See the [configuration reference](https://documentation.page/documentation/configuration)
for every option.
