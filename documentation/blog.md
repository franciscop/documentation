# Blog

Documentation Page can publish a blog straight from markdown files in your repository: no separate site, no static-site generator, no deploys. Posts live next to your code, are versioned with it, and go live when you push.

## Enabling it

A blog turns on automatically if your repo has a top-level **`blog/`** folder. You can also point at a different folder (or specific files) with the `blog` option in your [configuration](/documentation/configuration#blog):

```json
{
  "blog": "blog"
}
```

Once enabled, the blog index is served at **`/blog`**, each post at **`/blog/<slug>`** (the slug is the file name, lowercased and hyphenated, so `2. Dark mode.md` is served at `/blog/2-dark-mode`), and a _Blog_ link appears in the navigation.

## Writing a post

Each post is a markdown file. Optionally, start it with a metadata block (liquid/YAML front-matter) between `---` fences:

```markdown
---
title: We shipped dark mode
description: The most requested feature is finally here.
date: 2026-07-12
social: /assets/dark-mode.png
---

# We shipped dark mode

It's been the most requested feature for months...
```

Every field is optional: leave one out and we pick a sensible default, described below. From whatever you provide, the full set of **social tags** (Open Graph and Twitter) is generated for you, so shared links look right everywhere.

## title

The post's title, used in the heading, the browser tab and the social card. Defaults to the post's first heading, or a title built from the file name.

```md
---
title: We shipped dark mode
---

# Today's update ...
```

## description

A short summary, used for the social card and search engines. Defaults to your project's description.

```md
---
description: The most requested feature is finally here.
---

# Today's update ...
```

## date

The publication date, shown on the post. Defaults to the `YYYY-MM-DD` prefix of the file name, if it has one.

```md
---
date: 2026-07-12
---

# Today's update ...
```

## social

A path (made absolute automatically) used for the social share card. Defaults to your project's social image.

```md
---
social: /assets/dark-mode.png
---

# Today's update ...
```

## Ordering

Posts are sorted by file name. If you prefix them with a `YYYY-MM-DD` date, the **newest** ones are shown first, so a blog reads the way you'd expect:

```
blog/
  2026-07-12-dark-mode.md
  2026-05-02-v2-release.md
  2026-01-10-hello-world.md
```

The file name is also the URL, so that post is served at `/blog/2026-07-12-dark-mode`.

## Naming each post

To choose the URLs yourself, give `blog` an object instead of a folder. Each key is the slug and each value is the file, so you keep the dated file names while serving clean URLs, in exactly the order you list them:

```json
{
  "blog": {
    "dark-mode": "blog/2026-07-12-dark-mode.md",
    "v2-release": "blog/2026-05-02-v2-release.md",
    "hello-world": "blog/2026-01-10-hello-world.md"
  }
}
```

That post is now at `/blog/dark-mode`. This is also the way to rename a post without breaking its URL, or to publish only some of the files in a folder.
