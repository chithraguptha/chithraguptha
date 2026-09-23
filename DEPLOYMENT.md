# Public Site Deployment

## Domain layout

- Company site: https://www.chithraguptha.site
- Company alias: https://www.chithraguptha.com
- API: https://api.chithraguptha.site
- Privacy: https://www.chithraguptha.site/privacy
- Terms: https://www.chithraguptha.site/terms

The site is static HTML. Deploy the repository root to Vercel, Cloudflare Pages, Netlify, or GitHub Pages.

## Vercel

1. Import chithraguptha/chithraguptha.
2. Framework preset: Other.
3. Build command: none.
4. Output directory: .
5. Add www.chithraguptha.site and chithraguptha.site, plus the .com hostnames if desired.
6. Pick one canonical hostname and redirect the alternate domains to it.

## DNS

Point the selected apex/www records to the hosting provider. Keep api.chithraguptha.site on the backend infrastructure; do not route API traffic to the static site host.

## Logo

The source-of-truth Manvori mark is mobileapp/assets/images/logo.png. The public site references /assets/logo.png. Copy that exact file from the mobileapp repository into this repository. The connected GitHub API cannot write binary PNG blobs directly.

## Pre-launch verification

Check /, /privacy, /terms and /assets/logo.png over HTTPS. Replace the legal/support placeholder with the monitored production contact before publishing.

## Google Cloud startup verification

Google Cloud currently says applicants should have a Google Cloud billing account ID and that the business email used in the application should match the startup public website domain. Keep the company email/domain identity aligned. Do not claim incorporation, funding, or other legal status unless it is true and supportable.

## Google Play

Use /privacy as the single governing privacy-policy URL and link the same policy inside Manvori. Complete Play Console Data safety declarations to match the implementation, including analytics, crash reporting, authentication, conversations, profile/birth data and third-party AI/service providers.

Before release, replace development OTP behavior with real authentication and add the final legal/support contact.


## GitHub Pages (recommended)

The repository includes `.github/workflows/pages.yml` and a `CNAME` for `www.chithraguptha.site`.

1. Merge this PR into `main`.
2. In GitHub, open **Settings → Pages** for `chithraguptha/chithraguptha`.
3. Under **Build and deployment**, choose **GitHub Actions**.
4. After the workflow completes, set the custom domain to `www.chithraguptha.site` if GitHub has not already detected it from the CNAME.
5. Enable **Enforce HTTPS** once the certificate is available.

### DNS for `chithraguptha.site`

For the apex domain, configure GitHub Pages A records at your DNS provider:

- `@` → `185.199.108.153`
- `@` → `185.199.109.153`
- `@` → `185.199.110.153`
- `@` → `185.199.111.153`

For `www`, create:

- `CNAME` `www` → `chithraguptha.github.io`

GitHub recommends using `www` alongside an apex domain and will handle the corresponding redirect when both are correctly configured. Do not point `www` at the apex domain; point it directly at the GitHub Pages hostname. DNS changes can take time to propagate. citeturn0search0turn0search1

### `.com` domain

Keep `www.chithraguptha.site` as the canonical Pages domain. At the `.com` registrar/DNS provider, configure `www.chithraguptha.com` and `chithraguptha.com` as redirects to `https://www.chithraguptha.site`. Do not add the `.com` domain as another GitHub Pages CNAME unless you specifically want to make it the canonical Pages domain.

### Verify

After DNS propagation:

```bash
dig www.chithraguptha.site CNAME +short
dig chithraguptha.site A +short
```

Then visit:

- https://www.chithraguptha.site/
- https://www.chithraguptha.site/privacy
- https://www.chithraguptha.site/terms

GitHub Pages supports HTTPS for correctly configured custom domains; certificate provisioning can take time. citeturn0search3
