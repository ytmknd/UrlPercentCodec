# URL Encoder / Decoder

A single-page web app that converts URLs containing Japanese (or other non-ASCII) text to percent-encoded form (`%E6%97%A5…`) and back.

Everything runs in the browser. There is no build step, no server, and no data leaves your machine.

## Usage

Open `index.html` in a browser.

1. Paste a URL or text into the **Input** box.
2. Click **Encode** to convert non-ASCII characters to `%XX` sequences, or **Decode** to convert `%XX` sequences back to readable text.
3. Use **Copy** to copy the result, or **Move result to input** to chain another conversion.

Example:

```
https://ja.wikipedia.org/wiki/日本語
→ https://ja.wikipedia.org/wiki/%E6%97%A5%E6%9C%AC%E8%AA%9E
```

## Behavior notes

- **Encode** uses `encodeURI`, so URL delimiters such as `: / ? & = #` are left as they are and only the other characters are escaped.
- **Decode** uses `decodeURIComponent`, so escaped delimiters such as `%2F` or `%3F` also become `/` and `?`. The decoded URL may therefore have a different structure from the original.
- If the input has no `%XX` sequences, Decode leaves it unchanged and says so. If the sequences are malformed or the bytes are not valid UTF-8, an error is shown.

## Internationalization

The UI language follows `navigator.language`: Japanese when it starts with `ja`, English otherwise. All strings live in the `MESSAGES` object in `index.html`; to add a language, add an entry there and extend the language check.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS, JavaScript) |
| `README.md` | This file |
