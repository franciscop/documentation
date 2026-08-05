# How it works

A quick tour of what happens between your repository and the website your readers see.

## Reading the repo

Your repository must be **public** so we can read it (contact us if you need a private one). When someone opens your project, we call the Github API to fetch:

- the repo metadata (name, description, homepage, default branch),
- the full file tree of your default branch (`master` or `main`),
- the specific markdown, config, logo and blog files we need.

From those we detect everything described in [Conventions](/documentation/conventions), apply any [Configuration](/documentation/configuration), and render your markdown to HTML.

## Caching

To stay fast, respect Github's rate limits, and serve many projects at once, we **cache** each project after building it. This means a change you push can take up to the plan's refresh window to appear:

- **Free**: up to 24h.
- **Paid**: faster refresh (down to near-immediate on higher tiers). See [pricing](https://documentation.page/#pricing).

## Navigation

The sidebar navigation is generated from the headings of your rendered documentation. Your `##` and `###` headings become the sections and sub-sections, each linked by an anchor, so readers can jump around and share deep links. Multi-file docs are merged first, then parsed as one.

## Full-text search

Every page and heading is indexed so readers can search your documentation from the sidebar (press `/` to focus the box). Results link straight to the matching section.
