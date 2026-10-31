# aimeter

See README.md for files, share-image rendering and deploy (`CLOUDFLARE_ACCOUNT_ID=9a1da48a0f61e7cebcba39517856d87e npx wrangler deploy`).

## Lighthouse
<!-- lighthouse-optimized: 2026-10-31 -->
- Baseline (mobile): performance 99, accessibility 100, best-practices 100, SEO 100.
- Fixed: Google Fonts CSS loads non-blocking (`media=print` + onload, `<noscript>` fallback); dropped unused JetBrains Mono 500; `public/_headers` gives PNG/SVG a 30-day cache.
- Left: remaining findings come from the shared sankha-analytics.js / gtag and the Cloudflare Insights beacon (handled centrally).
