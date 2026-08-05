# Configuration

When the [conventions](/documentation/conventions) aren't enough, add a small JSON configuration to take control. Every key is optional and overrides what we would otherwise detect automatically, so you only need the ones you care about.

## Where to put it

We read the **first** of these that exists in your repository:

- `documentation.page.json`: a file at the root of your project.
- The `documentation.page` key inside your **`package.json`**.

Both use exactly the same options, described below. A typical configuration looks like this:

```json
{
  "name": "Statux",
  "title": "Statux • The easy React state management library",
  "description": "A straightforward way of dealing with your global app state",
  "logo": "https://example.com/mylogo.png",
  "menu": {
    "Donate": "https://www.paypal.me/franciscopresencia/19",
    "Github": "https://github.com/franciscop/statux"
  },
  "documentation": ["readme.md", "src/methods", "examples"]
}
```

## name

A very short name to identify the project: just the name, with no tagline or icon. It appears in the browser-tab title and, on paid plans, next to the logo in the navbar, so keep it short. Defaults to your [detected repo name](/documentation/conventions#name).

```json
{
  "name": "Statux"
}
```

## title

A longer identifier that can include your tagline. Unlike `name`, this is where the marketing goes: it's used as the main title in Google search results and as the headline on social share cards. Defaults to `name`.

```json
{
  "title": "Statux • The easy React state management library"
}
```

## description

A short paragraph summarizing what the project does and why it's useful. A sentence or two works best. It's used for the Google search-result description and the social share-card description. Defaults to your [Github repo description](/documentation/conventions#description).

```json
{
  "description": "A straightforward way of dealing with your global app state"
}
```

## logo

An absolute path or URL to your project's logo (`.svg` or `.png` recommended so it stays crisp at any size). It's used as **both** the browser-tab favicon and, on paid plans, the logo next to your project name in the navbar. Defaults to a [detected `favicon`/`logo` file](/documentation/conventions#logo), or the Documentation Page icon if there is none.

```json
{
  "logo": "https://example.com/mylogo.png"
}
```

## social

An absolute path or URL to the image used for social share cards, the preview shown when your docs are linked on Twitter, Slack, Facebook, etc. A wide image (around 1200×630) works best. Defaults to a [detected `social` file](/documentation/conventions#social), then your repo's Github social-preview image, then a generated card.

```json
{
  "social": "https://example.com/social-card.png"
}
```

## menu

The top-right navigation links, shown on **custom domains** (they don't appear on the free `documentation.page/github/...` pages). It's an object mapping each visible label to its URL, in order:

```json
{
  "menu": {
    "Issues": "https://github.com/franciscop/react-test/issues",
    "Contribute": "https://github.com/franciscop/react-test/blob/master/Contributing.md",
    "Donate": "https://www.paypal.me/franciscopresencia/19",
    "Github": "https://github.com/franciscop/react-test"
  }
}
```

Most links point to external URLs, or to your site's own sections (`/documentation`, `/blog`).

### Publishing an HTML page

If a value is instead a path to a local **`.html` file** in your repository, that file is published as its own page and the menu link points to it. This is how you add a hand-written page (a changelog, a demo, a test runner) that isn't part of your markdown docs:

```json
{
  "menu": {
    "Tests": "tests.html",
    "Github": "https://github.com/franciscop/umbrella"
  }
}
```

- **The URL comes from the label**, lowercased and hyphenated: `"Tests"` is served at `/tests`, and `"Release Notes"` at `/release-notes`. The file name plays no part in the URL.
- The page is included in your generated `/sitemap.xml`.
- If the file doesn't exist in the repository, the menu link is left pointing at the raw value rather than breaking the build.

Only `.html` values are published this way; a page is only created when it has a menu entry.

#### Fragments and whole documents

How the file is served depends on what it contains:

- **A fragment** (no `<html>` tag) is wrapped in your site's header and footer, exactly like [`home`](#home-and-landing). Write only the content and it matches the rest of your site, with the menu link highlighted while the reader is on it. Add a `<style>` block for anything specific to the page.
- **A whole document** (it opens with `<!DOCTYPE html>` or `<html>`) is served untouched. Nothing is added, so it is yours to style and script, which is what you want for a demo or a test runner that needs its own assets in `<head>`.

Fragments are the better default. Reach for a whole document when the page needs to control the entire response.

## documentation

Which files and folders make up your documentation. It accepts three shapes, from simplest to most powerful.

### A single file

A string points at one markdown file:

```json
{
  "documentation": "readme.md"
}
```

### An array: one combined page

An array of files and folders, all **concatenated into a single page** in the order given:

```json
{
  "documentation": ["readme.md", "src/methods", "src/jest-matchers", "src/examples"]
}
```

Each entry is resolved relative to the repository root. A `.md` file is included directly; a folder pulls in every `.md` inside it (alphabetically, top-level files first). Matching is case-insensitive.

### An object: multiple pages

An object turns your docs into a **multi-page site**, one page per key. Each **value** is that page's source: a file, a folder, or an array of them, resolved exactly like the single-page forms above:

```json
{
  "documentation": {
    "index": "readme.md",
    "1. Getting Started": "manual/getting-started.md",
    "2. API": ["src/api", "src/methods"],
    "3. Examples": "examples"
  }
}
```

Each **key** becomes the page's name in the sidebar and its URL:

- A leading `N. ` (a number, a dot, and a space) is **stripped**: it only sets the order, so `1. Getting Started` is shown as **Getting Started**. The rest of the key is kept verbatim.
- The URL is that name, lowercased and slugified: `Getting Started` → `getting-started`.
- The special key **`index`** is the landing page, served at `/documentation` itself (no slug). If there is no `index` key, the first entry becomes the landing instead.

So the example above produces:

| Key                  | Source                         | Page URL                         |
|----------------------|--------------------------------|----------------------------------|
| `index`              | `readme.md`                    | `/documentation`                 |
| `1. Getting Started` | `manual/getting-started.md`    | `/documentation/getting-started` |
| `2. API`             | `src/api` + `src/methods`      | `/documentation/api`             |
| `3. Examples`        | `examples`                     | `/documentation/examples`        |

Within each page, the sidebar sub-navigation is built automatically from its `##` headings.

When `documentation` is omitted entirely, we fall back to the [conventions](/documentation/conventions#documentation) (a `documentation/` folder, then `readme.md`).

> [!NOTE]
> `pages` is a deprecated alias for `documentation`. It still works, but new configurations should use `documentation`.

## blog

Publish a blog alongside your docs. Give it the folder (or leave it out and drop a `blog/` folder into your repo). Each markdown file in that folder becomes a post at `/blog/<slug>`, with the index at `/blog` and a *Blog* link added to the navigation.

```json
{
  "blog": "blog"
}
```

Give it an object instead to name each post and set its order by hand, where the key is the URL slug and the value is the file:

```json
{
  "blog": {
    "dark-mode": "blog/2026-07-12-dark-mode.md",
    "hello-world": "blog/2026-01-10-hello-world.md"
  }
}
```

See the dedicated [Blog](/documentation/blog) guide for the per-post front-matter (`title`, `description`, `date`, `social`), the sensible default for each, and how posts are ordered.

## tutorials

Publish tutorials alongside your docs. Give it the folder (or leave it out and drop a `tutorials/` folder into your repo). Each markdown file in that folder becomes a tutorial at `/tutorials/<slug>`, with the index at `/tutorials` and a *Tutorials* link added to the navigation.

```json
{
  "tutorials": "tutorials"
}
```

Give it an object instead to name each tutorial and set its order by hand, where the key is the URL slug and the value is the file:

```json
{
  "tutorials": {
    "getting-started": "tutorials/1-getting-started.md",
    "routing": "tutorials/2-routing.md"
  }
}
```

See the dedicated [Tutorials](/documentation/tutorials) guide for the per-tutorial front-matter (`title`, `description`, `date`, `social`), the sensible default for each, and how tutorials are ordered.

## home and landing

For custom domains you can replace the auto-generated homepage with your own:

- **`home`**: a path to an HTML **snippet** used as the main content of your homepage. We wrap it in the site's navigation and footer so it stays consistent with the rest of your site.
- **`landing`**: a path to a **full, standalone** HTML page, served exactly as-is at the root. Use this when you want complete control over the markup, styles and scripts.

```json
{
  "home": "home.html"
}
```

With either one set, your generated documentation moves to **`/documentation`**. Without them, the root of your domain shows your documentation directly.
