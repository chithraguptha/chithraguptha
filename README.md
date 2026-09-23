# Chithraguptha

Chithraguptha is the home of Manvori, a mobile reflection companion that brings together traditional Indian astrology systems, Panchanga context, conversations, and Indian wisdom for personal reflection.

## Public website

The production website is designed for:

- https://www.chithraguptha.site
- https://www.chithraguptha.com

Key public routes:

- / — company and product home
- /privacy — Manvori privacy policy
- /terms — terms of use

The site is intentionally static and can be deployed to Vercel, Cloudflare Pages, Netlify, or GitHub Pages.

## Product structure

**Chithraguptha** is the company/brand.

**Manvori** is the consumer mobile app.

Manvori currently focuses on Ask Manvori chat, Panchanga context, South Indian Kundali, advanced astrology context, Soul Room, and Indian wisdom/reflection. Astrology and traditional wisdom are positioned as cultural/traditional guidance rather than scientific certainty or guaranteed prediction.

## Repositories

- mobileapp — Flutter app
- backend — Go/Gin API and worker services
- infra — Terraform/Azure deployment configuration

## Publishing checklist

Before publishing the Android app:

1. Deploy the website and verify the privacy and terms URLs load over HTTPS.
2. Use the privacy URL in Google Play Console and link it inside the app.
3. Complete the Play Data safety form consistently with the implementation, including analytics and third-party AI/telemetry flows.
4. Replace the development OTP configuration with a real OTP/SMS flow before real user accounts contain valuable data.
5. Set production CORS origins rather than *.
6. Enable Key Vault purge protection and rotate any credentials used during development.
7. Provide Play reviewers with working access instructions/demo credentials where required.
8. Ensure the developer profile, legal entity details, website domain and payment profile are consistent.

## Branding

The public website reuses the Manvori app's existing visual direction: obsidian surfaces, deep maroon, muted gold borders/highlights, and the existing circular app mark from mobileapp/assets/images/logo.png.
