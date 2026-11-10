# links.eglny.com — EGLNY Instagram link hub

Stable bio URL for [@lunarnewyeartet](https://www.instagram.com/lunarnewyeartet/). Instagram’s website field is **`https://links.eglny.com`**. Evergreen destinations (eglny.com + Facebook) sit **below the name** on this hub. Featured post tiles go in the grid when a live post has an off-platform URL.

| Item | Value |
|------|-------|
| Bio URL | https://links.eglny.com |
| Repo | [cPALSs/eglny-links](https://github.com/cPALSs/eglny-links) |
| Edit here | `Operations/Sites/eglny-links` |
| Manifest | [`data/ig-links.json`](data/ig-links.json) |

`links.cpalss.com/lunarnewyeartet` redirects here. Org account hub stays at [links.cpalss.com/cpalss](https://links.cpalss.com/cpalss).

## Update workflow (after every EGLNY IG post with a URL)

```
Post goes live on @lunarnewyeartet
  → Caption / first comment / on-image has an off-platform URL?
    → YES:
        1. Fetch thumb → assets/thumbs/lunarnewyeartet/{slug}.jpg
        2. Add row to data/ig-links.json (publishedAt DESC)
        3. git commit + push (when Bao says deploy)
        4. Confirm tile on https://links.eglny.com/
```

```bash
./scripts/fetch-ig-thumb.sh https://www.instagram.com/lunarnewyeartet/p/SHORTCODE/ \
  lunarnewyeartet/slug.jpg
```

If Instagram media fetch fails, copy the pack’s posted JPEG into `assets/thumbs/lunarnewyeartet/` and point `igThumb` at it.

**Include** any post with a destination URL (apply, Tally, Eventbrite, LSS list, Fund The Festival, save-the-date hub, etc.) — not only “link in bio” wording.

## Local preview

```bash
cd Operations/Sites/eglny-links
python3 -m http.server 8766
# http://localhost:8766/
```

## DNS (eglny.com zone · Cloudflare)

| Type | Name | Value | Proxy |
|------|------|--------|-------|
| CNAME | `links` | `cpalss.github.io` | DNS only |

Repo **Settings → Pages → Custom domain**: `links.eglny.com` → enforce HTTPS.
