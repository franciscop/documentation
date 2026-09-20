# Conventions

This is the most powerful bit: we crawl your repository looking for a handful of useful files and use them to build the website. Whenever possible we recommend following these conventions first, and reaching for [configuration](/documentation/configuration) only when you need to override something.

Everything below is detected automatically from a **public** repository, no config required. Each item links to its matching [configuration](/documentation/configuration) option, which always takes precedence over what we detect.

| key             | detected from                                        | override |
|-----------------|------------------------------------------------------|----------|
| `name`          | The Github repo `name`, cleaned up.                  | [name](/documentation/configuration#name) |
| `title`         | The same as `name` by default.                       | [title](/documentation/configuration#title) |
| `description`   | The Github repo `description`.                       | [description](/documentation/configuration#description) |
| `logo`          | A file named `favicon` or `logo`.                    | [logo](/documentation/configuration#logo) |
| `social`        | A file named `social`, or the Github social preview. | [social](/documentation/configuration#social) |
| `documentation` | A `documentation/` folder, otherwise `readme.md`.    | [documentation](/documentation/configuration#documentation) |
| `blog`          | A `blog/` folder.                                    | [blog](/documentation/configuration#blog) |
| `tutorials`     | A `tutorials/` folder.                               | [tutorials](/documentation/configuration#tutorials) |
| `llms`          | An `llms.txt` file, otherwise built from your docs.  | [llms](/documentation/configuration#llms) |
| `menu`          | Not detected, configuration only.                    | [menu](/documentation/configuration#menu) |

## name

Your project's short identifier. It comes from the Github repository name, tidied up: emoji are stripped, dashes become spaces, and each word is capitalized, so the repo `my-cool-lib` becomes **My Cool Lib**. It's the shortest possible label for your project, with no tagline or icon, and appears in the browser-tab title (and, on paid plans, next to the logo in the navbar). Override it with the [`name`](/documentation/configuration#name) option.

## title

A longer identifier that can carry your tagline. It defaults to the same value as `name`, but this is where the marketing goes: it's used as the main title in Google search results and as the headline on social share cards. Set the [`title`](/documentation/configuration#title) option to give search engines and link previews something richer than the bare project name.

## description

A short paragraph summarizing what the project does and why it matters, taken straight from your repository's Github description. It appears in the Google search snippet and the social share-card description. Emoji are stripped and whitespace normalized. Override it with the [`description`](/documentation/configuration#description) option.

## logo

We look for a file named `favicon` or `logo` with a `.svg`, `.png`, `.jpg`, `.jpeg` or `.ico` extension, preferring files closer to the repository root. The image becomes **both** the browser-tab favicon and (on paid plans) the logo shown next to your project name in the navbar. If none is found, we fall back to the Documentation Page icon. Point at a specific file or URL with the [`logo`](/documentation/configuration#logo) option.

## social

The social image is used for social share cards, the preview that appears when your docs are linked on Twitter, Slack, Facebook, and so on (the Open Graph and Twitter image). We look for a file named `social` with a `.jpg`, `.png`, `.webp` or `.avif` extension; failing that we use your repository's Github social-preview image, and as a last resort an automatically generated card. Set the [`social`](/documentation/configuration#social) option to use a specific image.

## documentation

If you don't set [`documentation`](/documentation/configuration#documentation) explicitly, we pick the source of your docs automatically:

1. A **`documentation/`** folder, if present.
2. Otherwise your **`readme.md`**.

A folder is read recursively and every `.md` file inside it is concatenated into a single page, in order: alphabetically, with top-level files before nested ones. Because the order is alphabetical, prefixing files with numbers (`1. Intro.md`, `2. Usage.md`) is the easiest way to control the sequence. For full control over which files and folders are included, and to split your docs into multiple pages, use the [`documentation`](/documentation/configuration#documentation) option.

## blog

If your repository has a top-level **`blog/`** folder, its markdown files are published as a blog automatically: the index at `/blog`, each post at `/blog/<slug>`, and a *Blog* link added to the navigation. Point at a different folder with the [`blog`](/documentation/configuration#blog) option, and see the [Blog](/documentation/blog) guide for the per-post front-matter (`title`, `description`, `date`, `social`) and how posts are ordered.

## tutorials

If your repository has a top-level **`tutorials/`** folder, its markdown files are published as tutorials automatically: the index at `/tutorials`, each tutorial at `/tutorials/<slug>`, and a *Tutorials* link added to the navigation. Point at a different folder with the [`tutorials`](/documentation/configuration#tutorials) option, and see the [Tutorials](/documentation/tutorials) guide for the per-tutorial front-matter (`title`, `description`, `date`, `social`) and how tutorials are ordered.

## llms

Your site automatically serves an [`/llms.txt`](https://llmstxt.org/), a single clean markdown file of your entire documentation that AI assistants can read in one request. By default we build it from the same markdown we render, so it stays in sync with every push and needs no setup.

To take over the file yourself, add an **`llms.txt`** to your repository (we prefer one closer to the root, like the `logo` and `social` files) and we serve it verbatim at `/llms.txt` instead of the generated one. Point at a specific file with the [`llms`](/documentation/configuration#llms) option.

## menu

The top-right navigation menu is the one thing here that is **not** auto-detected. It's used on custom domains and must be set with the [`menu`](/documentation/configuration#menu) option.
