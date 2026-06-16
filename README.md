# HELMA Viewer

Public static viewer for HELMA InfoScreen.

This repository is intended to be published with GitHub Pages. It reads slide
data from `HELMA_API_URL`, renders the fullscreen infoscreen, and polls for
updates every 10 seconds by default.

## Configure

Edit `config.js`:

```js
window.HELMA_API_URL = "https://example.com/helma/presentation";
window.HELMA_API_TOKEN = "";
window.HELMA_BRANDING_IMAGE = "https://example.com/background.png";
window.HELMA_POLL_MS = 10000;
```

For a public GitHub Pages viewer, prefer an unauthenticated `GET` endpoint. Do
not place a write token in this public repository.

## API contract

The viewer uses:

```text
GET HELMA_API_URL
```

The endpoint should return either:

```json
[
  { "name": "Slide", "duration": 8, "elements": [] }
]
```

or:

```json
{
  "data": [
    { "name": "Slide", "duration": 8, "elements": [] }
  ],
  "updated": 123456789
}
```

The API must allow CORS requests from the GitHub Pages domain.

## GitHub Pages

Recommended repository name:

```text
HELMA-viewer
```

After pushing, enable GitHub Pages:

1. Go to repository settings.
2. Open **Pages**.
3. Set source to **Deploy from a branch**.
4. Use branch `main`, folder `/ (root)`.

The viewer URL will usually be:

```text
https://techgruppa.github.io/HELMA-viewer/
```

