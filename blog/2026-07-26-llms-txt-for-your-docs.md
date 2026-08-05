---
title: Your docs now ship an /llms.txt
description: If your project is on a custom domain, Documentation Page automatically generates an /llms.txt so AI assistants can read your whole documentation in one clean file.
date: 2026-07-26
social: /blog/2026-07-26-llms-txt-for-your-docs.png
---

# Your docs now ship an /llms.txt

People read your documentation, and now so do AI assistants. The problem is that a rendered HTML page is noisy for a model: navigation, scripts, styles and markup all get in the way of the actual content. The [llms.txt standard](https://llmstxt.org/) fixes this with a simple idea: serve a single markdown file at `/llms.txt` that lays out your documentation in a clean, complete form a model can ingest cheaply and accurately.

If your project is on a custom domain, Documentation Page now generates that file for you, automatically.

## How it works

We already read the markdown from your repository and render it into your site. For `/llms.txt` we reuse the exact same source: we concatenate the raw markdown of every documentation page into one file and serve it at the root of your domain. That gives you:

- **No setup.** There is no config to add and no build step to run. It turns on with your docs.
- **Always in sync.** The file is generated on demand from your repository, so it reflects your latest push (within your [refresh rate](/documentation/how-it-works#caching)).
- **Real markdown, not scraped HTML.** The model gets your actual source, with headings, links and code blocks intact, instead of trying to parse a web page.

Point any assistant at `https://yoursite.com/llms.txt` and it has your entire documentation in a single request.

Even without it, your site is already readable. Every page on Documentation Page is server-side rendered, so the HTML arrives complete, with no client-side JavaScript needed to see the content. Crawlers, screen readers and a plain `curl` all get your docs. `/llms.txt` simply goes one step further and hands everything over in a single, markup-free file.

## See it in action

Crossroad, a small React routing library, is hosted on a custom domain. You can read its documentation the usual way at [crossroad.page/documentation](https://crossroad.page/documentation), and the exact same content, as one clean markdown file for machines, lives at:

[https://crossroad.page/llms.txt](https://crossroad.page/llms.txt)

Open it and you will see the whole thing: headings, prose and code, ready to paste into a prompt or hand to an assistant.

## Get it for your project

`/llms.txt` is served on custom domains, alongside a generated `/sitemap.xml`. Put your docs on your own domain and your project speaks fluent LLM with no extra work on your side.

[See the plans and get a custom domain](https://documentation.page/#pricing).
