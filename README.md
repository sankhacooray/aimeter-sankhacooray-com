# aimeter

One-screen download page for **Claude Meter**, the macOS menu bar app that shows Claude plan
usage. App source: [bsc2fast/claude-meter-macos](https://github.com/bsc2fast/claude-meter-macos).

Target URL: **aimeter.sankhacooray.com**, served by a Cloudflare Worker (static assets only),
the same setup as `cook`. Repo: `aimeter-sankhacooray-com`.

## Files

| Path | Purpose |
|------|---------|
| `public/index.html` | The whole page; CSS and the copy-button JS are inline |
| `public/og.png` | 1200×630 share image, rendered from `og/og.html` |
| `public/icon*.png`, `icon.svg`, `apple-touch-icon.png`, `manifest.webmanifest` | Icons + PWA manifest |
| `wrangler.toml` | Worker config + custom domain |

The download button points to `releases/latest/download/ClaudeMeter.zip`, so new app
releases need no site change.

## Share image

Edit `og/og.html`, then render it and bump `?v=N` on the `og:image`/`twitter:image` URLs in
`public/index.html` so WhatsApp/Slack refetch it:

```
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
  --force-device-scale-factor=1 --window-size=1200,630 --virtual-time-budget=5000 \
  --screenshot=public/og.png "file://$PWD/og/og.html"
```

## Preview / deploy

```
python3 -m http.server 4795 --bind 127.0.0.1 -d public
CLOUDFLARE_ACCOUNT_ID=9a1da48a0f61e7cebcba39517856d87e npx wrangler deploy
```

After deploying, curl the page, `og.png` and the icons to confirm 200s and the right types.
