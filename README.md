# My Daily Space — iPhone & iPad web app

This is a small installable Progressive Web App (PWA). It includes:
- Daily task list with categories and completion checkboxes
- Weekly calendar strip with day selection
- Five daily prayer checklist (Fajr, Dhuhr, Asr, Maghrib, Isha)
- Weekly task/prayer completion overview and reflection
- Exportable weekly report
- Local on-device storage and basic offline caching

## Important limitations
- It is not a signed native `.ipa` app. iOS installation is through Safari's **Add to Home Screen**.
- To install it on iPhone/iPad, it must be served from an HTTPS website. Opening `index.html` directly from Files will not enable the full install/offline behavior.
- Data is stored locally in that browser/device. It does not sync between iPhone and iPad.
- Prayer times are not calculated and no push notifications are included yet. The salah area is a checklist.

## Publish free with GitHub Pages
1. Create or sign in to a GitHub account.
2. Create a new public repository, for example `my-daily-space`.
3. Upload all files in this folder to the repository root.
4. In the repository, open **Settings → Pages**.
5. Choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
6. Wait for the published HTTPS URL shown in Pages.
7. On iPhone/iPad, open that URL in **Safari**.
8. Tap **Share → Add to Home Screen → Add**.

## Files
- `index.html` — app structure
- `styles.css` — responsive iPhone/iPad design
- `app.js` — tasks, prayer checklist and weekly reports
- `manifest.webmanifest` — install metadata
- `sw.js` — offline cache
- `icon.svg` — app icon
