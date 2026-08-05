# Branding

Make your documentation feel like your own project: point your [`logo`](/documentation/configuration#logo), add a [custom domain](/documentation#custom-domain), and replace the auto-generated homepage with your own [`home`](/documentation/configuration#home-and-landing) page.

> [!NOTE]
> `home` and `landing` are meant for a **simple** landing page for your project. If you find yourself reaching for a build system, a multi-page marketing site, or other complex tooling, please [reach out](https://francisco.io/) and we will help you find a good setup. It is often simpler to leave your main website as it is and scope the docs to `docs.yourproject.com` or `yourproject.com/documentation`, rather than recreating a complex site here.

## Custom homepage

Set [`home`](/documentation/configuration#home-and-landing) to an HTML file in your repository. It is injected into the page's `<main>` and wrapped in your site's navigation, so the header stays consistent. Everything inside is plain HTML that you lay out and style yourself.

> [!TIP]
> Add a `<style>` block anywhere in your snippet. It is included as-is, so your own CSS applies immediately, and you can style the page however you like.

### What you get for free

You are not starting from a blank page. Your snippet inherits the site's typography (font, text color and line height) and its design tokens, and these are styled for you:

- **Buttons**: add `class="button"` to a link or button, and `class="button primary"` for the highlighted one.
- **Links**: prose links are colored and underlined, while anything with `class="button"` keeps its button look.
- **Code**: `<code>` and `<pre><code class="language-js">` get the monospace font, the tinted background and full syntax highlighting, the same as in your documentation.
- **Forms**: inputs, textareas and labels.
- **Media**: images and videos never overflow their container.

Everything else is yours to lay out. Note that margins are reset to zero, so headings and paragraphs have no spacing until you give them some.

The available tokens include `--primary`, `--text`, `--text-soft`, `--card`, `--fill`, `--line`, `--code-bg`, `--font-body` and `--font-mono`. Using them keeps your page consistent with the rest of your site:

```css
.hero {
  background: var(--card);
  border: 1px solid var(--line);
  color: var(--text-soft);
}
```

Your own CSS is applied after all of this, so any of it can be overridden.

```html
<style>
  .hero {
    display: grid;
    gap: 1.5rem;
    padding: 4rem 1rem;
    text-align: center;
  }
  .hero h1 {
    font-size: 3rem;
  }
</style>

<section class="hero">
  <h1>Your Project</h1>
  <p>A short tagline about what it does.</p>
  <a href="/documentation">Read the docs</a>
</section>
```

## Full control

For complete control over the whole page, including the `<head>`, custom fonts and scripts, use [`landing`](/documentation/configuration#home-and-landing) instead of `home`. It is served exactly as-is at the root of your domain, with no navigation added.
