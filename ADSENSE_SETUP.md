# AdSense setup checklist

This static site does not include an `ads.txt` file because the AdSense publisher ID is account-specific. After Google approves the site, copy the exact line provided in AdSense into a root-level `ads.txt` file. Do not use a placeholder or another publisher ID.

Before adding ad code, configure Google's consent message for visitors in the EEA, UK, and Switzerland where applicable, update `privacy.html` with the services actually enabled, and keep ads away from generator fields, code output, and Copy/Download controls.

After deployment, verify:

- `https://ispscripts.com/robots.txt`
- `https://ispscripts.com/sitemap.xml`
- `https://ispscripts.com/ads.txt` after adding the account-specific line
- Search Console indexing and mobile usability
- AdSense policy status and consent-message behavior
