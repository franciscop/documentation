# Compare with

How Documentation Page differs from other ways of publishing docs. The short version: we generate a site from the markdown already in your repo, with no build step and nothing to maintain.

## Github Pages

Github Pages is great, but it's a static-site host: you run a generator (often Jekyll) that builds HTML into your repository or a branch. That means a build step to maintain, generated files polluting your repo, and configuration to keep working over time.

With Documentation Page there is nothing to build and nothing extra committed to your repo: you write markdown, we render it on demand. The trade-off is that your site is hosted by us rather than by Github; if you'd rather self-host, see [Leaving Documentation Page](/documentation#leaving-documentation-page).

## Static Sites

Tools like docs frameworks and site generators are powerful, but they ask you to learn their system, adopt their file layout, and run their build. Documentation Page follows _your_ structure instead: a single `readme.md`, a `documentation/` folder, or a small [configuration](/documentation/configuration) file when you want more control.

## A hand-built site

You always get the most control by building the site yourself, at the cost of doing (and maintaining) all of it. Documentation Page aims for the sweet spot: a polished, searchable, mobile-friendly site for the price of writing markdown, with an [upgrade path](https://documentation.page/#pricing) for custom domains and branding when you need it.
