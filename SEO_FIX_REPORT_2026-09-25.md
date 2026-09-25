# SEO and technical-content update — ispscripts.com — 25 September 2026

## Completed locally

- Replaced internal `index.html` links with the canonical root URL `/` across the static site.
- Removed the HTML meta-refresh behavior from `radius/index.html`; the legacy path is now a non-indexable 200 page with a clear link and canonical pointing to the current RADIUS article.
- Removed `index.html` and the legacy `/radius/` path from `sitemap.xml`.
- Added the canonical root URL `https://ispscripts.com/` to the sitemap.
- Improved `subnet-calculator-guide.html` title, description, visible H1, review date, and Article JSON-LD around the queries `how to calculate subnets`, CIDR, network address, and broadcast address.
- Added `radius-server-not-responding-mikrotik-v7.html`, a practical RouterOS v7 troubleshooting article with one-command-at-a-time checks, decision tables, RADIUS counters, PPPoE discovery, firewall, source IP, shared secret, authentication, and accounting diagnosis.
- Added `pppoe-server-mikrotik-v7-configuration-script.html`, a staged RouterOS v7 configuration guide with placeholders, backup/rollback warnings, local-first testing, RADIUS integration, accounting, NAT, verification, and production checklist.
- Added both articles to `blog.html`, `index.html`, and `guide.html` through contextual internal links.
- Added both articles to `sitemap.xml` with `lastmod=2026-09-25`.

## Sources used for the new technical content

- [MikroTik RADIUS documentation](https://help.mikrotik.com/docs/spaces/ROS/pages/328097/RADIUS)
- [MikroTik PPP AAA documentation](https://help.mikrotik.com/docs/spaces/ROS/pages/132350049/PPP+AAA)
- [MikroTik PPPoE documentation](https://manual.mikrotik.com/docs/virtual-private-networks/pppoe/)
- [MikroTik logging documentation](https://help.mikrotik.com/docs/spaces/ROS/pages/328094/Log)
- [RFC 2516 — A Method for Transmitting PPP Over Ethernet](https://www.rfc-editor.org/rfc/rfc2516)
- [RFC 2865 — RADIUS](https://www.rfc-editor.org/rfc/rfc2865)
- [RFC 2866 — RADIUS Accounting](https://www.rfc-editor.org/rfc/rfc2866)

## Validation completed

- All selected pages have exactly one H1 and a title, description, and canonical URL.
- Sitemap parses as XML, contains 30 canonical URLs, contains the root URL, and excludes `/index.html` and `/radius/`.
- All relative internal links resolve to existing local files.
- JavaScript syntax check passed for 50 embedded script files.
- Local HTTP smoke test returned 200 for the root, blog, updated subnet guide, both new articles, legacy endpoint, and sitemap.
- Public sandbox preview loaded the RADIUS article and exposed the official source links and generator CTA.

## Publication note

The GitHub Pages repository is `https://github.com/diaacylan/ispscripts` on `main`. The changes were published successfully to commit `cf5aee418125d18fe1dce8ff117bce6159905bb9` after write permission was enabled, and the live domain verification passed.
