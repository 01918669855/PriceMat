# PriceMate Android PWA

## Files
- `PriceMate.html` — your original PriceMate app with PWA links and service-worker registration added.
- `manifest.webmanifest` — Android install metadata and app identity.
- `sw.js` — app-shell caching and offline navigation fallback.
- `icons/` — the original embedded app artwork extracted without redesign.

## Publish with GitHub Pages
1. Create or open your GitHub repository.
2. Upload the complete contents of this folder, keeping the `icons` folder structure.
3. In repository **Settings → Pages**, publish from your chosen branch and folder.
4. Wait for GitHub Pages to publish, then open the HTTPS URL ending in `/PriceMate.html`.
5. Open that URL in Chrome on Android, allow the first load to finish while online, then use Chrome menu → **Install app** (or **Add to Home screen**).

Do not open the HTML directly as `file://` and do not test PWA installation using an ordinary non-HTTPS link. Service workers require HTTPS (localhost is allowed for development).

## Offline use and updates
- Open PriceMate once while online so the service worker can install and cache the app shell.
- After that, the app page can reopen offline. App data such as saved orders remains in the browser's local storage; it is not automatically synchronized between devices.
- When you publish an updated app, change `CACHE_VERSION` in `sw.js` (for example, `pricemate-pwa-v2`) so installed copies refresh their cached app shell.
- Keep the same hosting path for the HTML, manifest, service worker, and icons.

## Important
This is an installable PWA, not an APK. Installation is done from Chrome and does not require Google Play Store. Offline availability covers the app shell and same-origin assets; any future third-party online services or remote resources still require connectivity. Keep regular backups of saved orders.
