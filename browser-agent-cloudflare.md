# Browser-agent brief: update redsunrising.co.uk for Klangfigur

You are working in the user's authenticated Cloudflare dashboard. Update the existing website at `https://redsunrising.co.uk` for the Klangfigur iPhone and Android release. This is an existing company website: do not create another zone, change nameservers, transfer the domain, replace the entire site, or disturb pages for other apps.

## Known current state

These live URLs currently return HTTP 200:

- `https://redsunrising.co.uk/`
- `https://redsunrising.co.uk/apps/tuner/`
- `https://redsunrising.co.uk/apps/tuner/privacy/`
- `https://redsunrising.co.uk/apps/tuner/support/`
- `https://redsunrising.co.uk/support/`
- `https://redsunrising.co.uk/privacy/`

The site identifies the publisher as Red Sun Rising LTD, company number SC831204, and uses `help@redsunrising.co.uk`. Preserve those company details and the existing design/navigation.

The live tuner pages are outdated: they call the product “Chladni Tuner,” describe it as iPhone-only/in development, and the app privacy page does not describe optional Apple/Google purchases. The app is now named **Klangfigur**, supports iPhone and Android, has Chladni included free, and offers **Constellations** as an optional permanent paid visual skin.

## Safety boundary

- First identify exactly what serves the domain: Cloudflare Pages, Workers, static assets, Git integration, redirects, or another origin.
- Record the project/worker name, production branch and connected source repository before editing.
- If it is Git-integrated, update the source repository rather than making an untracked dashboard-only copy. Preserve existing structure and styling.
- If the source repository is not accessible in the authenticated browser, stop and report its exact organisation/repository/branch. Do not replace the full site with a direct upload.
- Do not modify DNS, email routing, SSL settings, nameservers, unrelated routes, company details, or other app pages.
- A normal deployment of the scoped page edits below is authorised. Stop if Cloudflare proposes deleting/replacing a project, changing billing, or modifying the domain configuration.

## Required page changes

### `/apps/tuner/`

Change the public product name to **Klangfigur** and describe it as a visual chromatic tuner for iPhone and Android.

Use this core copy, adapted to the existing page structure:

> Klangfigur is a visual chromatic tuner that lets you see a note settle into tune. As your pitch approaches the centre, scattered particles resolve into a Chladni-style figure. Chladni is included free. Constellations is an optional one-time visual purchase that turns each note into a responsive night-sky figure. Microphone audio is analysed live on your device and is never recorded or uploaded.

Remove “In development for iPhone.” Do not claim the apps are already downloadable until their store pages are actually live. If store URLs do not exist yet, say “Coming to iPhone and Android” or omit store badges. Keep links to the tuner support and privacy pages.

### `/apps/tuner/privacy/`

Update the title/heading to **Klangfigur privacy policy**, the revision date to the current date, and scope it to Android and iPhone.

Keep the existing microphone, local preferences/custom tunings, support correspondence and no-advertising/no-analytics disclosures. Add:

> If you buy an optional visual skin, Apple or Google processes the transaction under its own privacy policy. Klangfigur receives product and entitlement information needed to unlock and restore the purchase. Red Sun Rising LTD does not receive or store your payment-card details.

Do not say the app sends no data over the internet without qualification, because StoreKit/Google Play Billing communicates with the platform store. It remains correct to say microphone audio and tuner preferences are not sent to Red Sun Rising LTD.

### `/apps/tuner/support/`

Change product naming to Klangfigur and confirm it covers both iPhone and Android. Keep `help@redsunrising.co.uk`. Add brief help for microphone permission, playing a clear sustained note, reducing background noise, and using Restore Purchases when a previously bought skin appears locked.

### Home page and `/support/`

Change visible “Chladni Tuner” references to **Klangfigur** and describe it as an iPhone and Android app. Preserve all unrelated apps and company content.

## Verification and deployment

Before deployment, inspect the diff and confirm only the scoped product/privacy/support/home references changed. Deploy through the project's established production workflow. Then verify:

1. All six URLs above return HTTP 200 over HTTPS.
2. Navigation and CSS still load.
3. The live product page says Klangfigur and iPhone/Android.
4. The live app privacy page includes the Purchases section and `help@redsunrising.co.uk`.
5. No page still says “In development for iPhone” or presents Chladni Tuner as the current product name.
6. Other app pages remain intact.

Return the project/repository/branch identified, commit and deployment identifiers if available, the exact pages changed, and the verification results.
