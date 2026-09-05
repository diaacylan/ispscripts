# ISP Scripts deployment notes

## Changes in this package

- Added `favicon.ico` at the site root.
- Added `favicon.svg` as the scalable favicon source.
- Added favicon links to all 22 top-level HTML documents.
- Added `radius/index.html` as a noindex fallback that sends visitors to `/radius-explained-for-isp-operators.html` using an HTML refresh and a normal link.
- Left `CNAME`, `robots.txt`, and `sitemap.xml` unchanged.

## Important: true HTTP 301 for `/radius`

GitHub Pages does not provide Apache/Nginx rules for an arbitrary server-side 301. The `radius/index.html` file prevents the old URL from remaining a hard 404, but it is an HTML fallback rather than a true HTTP 301.

For a real permanent redirect, configure a redirect at Cloudflare (or another proxy/DNS service that supports URL forwarding):

- Match path: `/radius`
- Destination: `https://ispscripts.com/radius-explained-for-isp-operators.html`
- Status: `301 Permanent Redirect`
- Preserve query string: enabled

After deployment, verify:

```bash
curl -I https://ispscripts.com/favicon.ico
curl -I https://ispscripts.com/radius
curl -I https://ispscripts.com/radius-explained-for-isp-operators.html
```

Expected results after the Cloudflare rule is active:

- `favicon.ico`: `200`
- `/radius`: `301` with a `Location` header pointing to the RADIUS article
- Target article: `200`
