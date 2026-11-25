# GoEasy.lk – "Launching soon" page

Static page with a live countdown to **1 January 2027, 12:00 AM Sri Lanka time**.
After that moment it shows "We're live!".

Files:
- `index.html`: the page (all CSS and JS inside)
- `404.html`: same page, so any wrong link still shows it
- `favicon.svg`: browser tab icon
- `CNAME`: tells GitHub Pages to use `goeasy.lk`

## Put it on GitHub Pages

1. Create a public repo (e.g. `goeasy-site`) and upload these files to the root of the `main` branch.
2. Repo **Settings → Pages**: Source = "Deploy from a branch", Branch = `main`, folder `/ (root)`. Save.
3. Under **Custom domain**, enter `goeasy.lk` and save. (The `CNAME` file already holds it.)
4. Recommended: verify the domain first in your GitHub account **Settings → Pages → Add a domain** (adds a TXT record). This stops anyone else claiming it.

## DNS (at the goeasy.lk domain provider)

Remove the old Netlify records for `@` and `www`, then add:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | YOUR-GITHUB-USERNAME.github.io |

**Do not touch MX or TXT records for email**, or info@goeasy.lk will stop working.
If the domain's nameservers point to Netlify DNS, either change the records inside Netlify DNS
or move the nameservers back to the domain provider first.

5. When DNS has spread (minutes to a few hours), go back to **Settings → Pages** and tick **Enforce HTTPS**
   (can take up to 24 hours to appear).

## Editing

- Launch time: in `index.html`, `const LAUNCH = Date.UTC(2026, 11, 31, 18, 30, 0);`
  (months start at 0, so 11 = December; 18:30 UTC = midnight in Sri Lanka).
- Phone, WhatsApp, email and social links are plain text in `index.html`.
- After editing `index.html`, copy it to `404.html` too.
