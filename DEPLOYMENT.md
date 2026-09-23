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
