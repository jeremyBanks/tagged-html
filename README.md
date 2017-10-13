# tagged-html

A tiny library for safely templating small amounts of HTML using template strings.

```javascript
import * as HTML from 'tagged-html';

const foods = ["🍉", "🥝", "🥗"];
document.body.appendChild(HTML.fragment`
  <p>Hello, world! Have some fruit:</p>
  <ul>
    ${foods.map(food => HTML`<li>${food}</li>`));
  </ul>
`);
```

<code>HTML\`...\`</code>, <code>HTML.escape(...)</code>, and <code>HTML.unsafeRaw(...)</code> return an HTML object that must be converted to a string by calling `.toString()`, or interpolated into one of these tag functions as an intermediate value.

<code>HTML.string\`...\`</code> returns the HTML as a string.

<code>HTML.element\`...\`</code> parses the HTML and returns an Element if it contains exactly one, else throws an error.

<code>HTML.fragment\`...\`</code> parses the HTML and returns the contents as a DocumentFragment.

Interpolated values (except for <code>HTML\`...\`</code> objects) are HTML-encoded, so they are safe inside text and attribute bodies, but should not be used elsewhere. **Do not interpolate values into `<script>` tags or other JavaScript contexts.**

