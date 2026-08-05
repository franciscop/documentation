# Tutorials

Documentation Page can publish tutorials straight from markdown files in your repository: step-by-step guides that live next to your code, are versioned with it, and go live when you push. It works just like the [Blog](/documentation/blog), for learning-oriented content.

## Enabling it

Tutorials turn on automatically if your repo has a top-level **`tutorials/`** folder. You can also point at a different folder (or specific files) with the `tutorials` option in your [configuration](/documentation/configuration#tutorials):

```json
{
  "tutorials": "tutorials"
}
```

Once enabled, the tutorials index is served at **`/tutorials`**, each tutorial at **`/tutorials/<slug>`** (the slug is the file name, lowercased and hyphenated, so `3. File uploads.md` is served at `/tutorials/3-file-uploads`), and a *Tutorials* link appears in the navigation.

## Writing a tutorial

Each tutorial is a markdown file. Optionally, start it with a metadata block (liquid/YAML front-matter) between `---` fences:

```markdown
---
title: Getting started
description: Build and run your first app in a couple of minutes.
date: 2026-07-12
social: /assets/getting-started.png
---

# Getting started

In this tutorial you will build your first app from scratch...
```

Every field is optional: leave one out and we pick a sensible default, described below. From whatever you provide, the full set of **social tags** (Open Graph and Twitter) is generated for you, so shared links look right everywhere.

## title

The tutorial's title, used in the heading, the browser tab and the social card. Defaults to the tutorial's first heading, or a title built from the file name.

```md
---
title: Getting started
---

# Your first steps ...
```

## description

A short summary, used for the social card and search engines. Defaults to your project's description.

```md
---
description: Build and run your first app in a couple of minutes.
---

# Getting started ...
```

## date

The publication date, shown on the tutorial. Defaults to the `YYYY-MM-DD` prefix of the file name, if it has one.

```md
---
date: 2026-07-12
---

# Getting started ...
```

## social

A path (made absolute automatically) used for the social share card. Defaults to your project's social image.

```md
---
social: /assets/getting-started.png
---

# Getting started ...
```

## Ordering

Tutorials are sorted by file name. Prefix them with a number to present them as a sequence, from the first steps through to the advanced topics:

```
tutorials/
  1-getting-started.md
  2-routing.md
  3-deploying.md
```

A `YYYY-MM-DD` date prefix works too, and shows the **newest** first (the same as the [Blog](/documentation/blog)).

The file name is also the URL, so that first tutorial is served at `/tutorials/1-getting-started`.

## Naming each tutorial

To choose the URLs yourself, give `tutorials` an object instead of a folder. Each key is the slug and each value is the file, so you keep the numbered file names while serving clean URLs, in exactly the order you list them:

```json
{
  "tutorials": {
    "getting-started": "tutorials/1-getting-started.md",
    "routing": "tutorials/2-routing.md",
    "deploying": "tutorials/3-deploying.md"
  }
}
```

That first tutorial is now at `/tutorials/getting-started`. This is also the way to rename a tutorial without breaking its URL, or to publish only some of the files in a folder.
