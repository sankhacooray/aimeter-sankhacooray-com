# aimeter

One-screen download page for **Claude Meter**, the macOS menu bar app that shows Claude plan
usage. App source: [bsc2fast/claude-meter-macos](https://github.com/bsc2fast/claude-meter-macos).

Target URL: **aimeter.sankhacooray.com**, served by a Cloudflare Worker (static assets only),
the same setup as `cook`. Repo: `aimeter-sankhacooray-com`.

## Files

| Path | Purpose |
|------|---------|
| `public/index.html` | The whole page; CSS and the copy-button JS are inline |
| `public/og.png` | 1200×630 share image (a render of the page itself) |
| `public/icon*.png`, `icon.svg`, `apple-touch-icon.png`, `manifest.webmanifest` | Icons + PWA manifest |
| `wrangler.toml` | Worker config + custom domain |

The download button points to `releases/latest/download/ClaudeMeter.zip`, so new app
releases need no site change.

## Preview / deploy

```
python3 -m http.server 4795 --bind 127.0.0.1 -d public
CLOUDFLARE_ACCOUNT_ID=9a1da48a0f61e7cebcba39517856d87e npx wrangler deploy
```

After deploying, curl the page, `og.png` and the icons to confirm 200s and the right types.
