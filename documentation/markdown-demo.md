# Markdown Demo

Every markdown feature the renderer supports, on one page. Write any of this in your own docs and it will look exactly as it does here.

## Headings

The title above is an `h1`; the remaining levels follow.

### Third-level heading

#### Fourth-level heading

## Text formatting

A paragraph with **bold**, *italic*, ***bold italic***, `inline code`, ~~strikethrough~~ and a [link](https://documentation.page/). This sentence runs a little longer so we can check the line height and how comfortably the text wraps once it reaches the edge of the column and continues onto the next line.

## Links

Every flavour of link, to check colour, underline and hover states:

- Inline link: [Documentation Page](https://documentation.page/)
- Reference-style link: [reference link][ref] (defined once, reused)
- Angle-bracket autolink: <https://documentation.page/>
- Email autolink: <hello@documentation.page>
- Bare URLs in text are *not* auto-linked, so wrap them: <https://documentation.page/documentation>
- Relative link to another page: [the Configuration page](/documentation/configuration)
- Link to a heading on another page: [jump to `name`](/documentation/configuration#name)
- Link wrapping `inline code`: [`package.json`](/documentation/configuration)
- Link wrapping **bold text**: [**important link**](https://documentation.page/)
- A [link that is long enough to wrap across more than one line so we can confirm the underline follows the text correctly as it breaks onto a second line](https://documentation.page/) mid-sentence.

A linked image (click through): [![A small logo](/favicon.svg)](https://documentation.page/)

[ref]: https://documentation.page/

## Lists

Unordered, with nesting:

- First item
- Second item
  - Nested one
  - Nested two
- Third item

Ordered:

1. Step one
2. Step two
3. Step three

## Code

Inline `const answer = 42`, then fenced blocks in a few languages:

```js
// JavaScript
const greet = (name) => `Hello, ${name}!`;
console.log(greet("world"));
```

```tsx
// TSX
type Props = { name: string };
export const Hello = ({ name }: Props) => <h1>Hi {name}</h1>;
```

```json
{
  "name": "documentation-page",
  "nested": { "list": [1, 2, 3], "flag": true }
}
```

```
A plain, unhighlighted code block.
```

Headings inside a code block must render literally, and must not affect the real document:

```md
# Not a real heading
## Also not real
```

## Math

Inline math like $E = mc^2$ and $a^2 + b^2 = c^2$ flows within the text, subscripts and all: $x_1, x_2, \ldots, x_n$. Display math is centered on its own line:

$$
\int_0^1 x^2 \, dx = \frac{1}{3}
$$

$$
\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
$$

## Tables

| Feature     | Supported | Notes                |
|-------------|-----------|----------------------|
| Headings    | Yes       | `h1`–`h4`            |
| Code blocks | Yes       | Syntax highlighted   |
| Tables      | Yes       | `border-collapse`    |

## Blockquotes

> A single-line quote.
>
> A second paragraph, with **formatting** inside.

## Alerts

> [!NOTE]
> Useful information the reader should know.

> [!TIP]
> A helpful tip.

> [!IMPORTANT]
> Key information worth highlighting.

> [!WARNING]
> Something to be careful about.

> [!CAUTION]
> The negative consequences of an action.

## Details

<details>
<summary>Click to expand</summary>

Hidden content, revealed on toggle, with `code`, and a short list:

- one
- two

</details>

<details open>
<summary>Open by default</summary>

Add `open` to the tag and the section starts expanded.

</details>

## Horizontal rule

Above the rule.

---

Below the rule.
