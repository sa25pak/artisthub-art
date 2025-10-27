# Mobile App Publishing Plan for ArtistHub.art

This document outlines options and step-by-step actions to make the web marketplace available as apps on Google Play (Android) and Apple App Store (iOS).

## Two recommended approaches

1) Progressive Web App (PWA) — fastest path (web-first, single codebase)
   - Convert the website to a PWA (add web app manifest + service worker)
   - Advantages: One codebase, instant updates, installable on Android and iOS (limited) and can be wrapped for stores.
   - Limitations: iOS has restrictions (no push notifications, limited background sync), and App Store policies sometimes require a native wrapper for full store listing.

2) Native / Cross-platform (React Native or Flutter) — best store experience
   - Reuse web backend APIs and build a native frontend in React Native or Flutter.
   - Advantages: Full native performance, native push notifications, richer permissions and features, easier acceptance to both stores.

## Minimum deliverables for both stores
- Developer accounts
  - Google Play Console account (one-time fee: $25).
  - Apple Developer Program (annual fee: $99).
- App icon assets (multiple sizes), feature graphic (Play Store), screenshots for various device sizes, short and long descriptions, privacy policy URL, support URL, contact email.
- App signing keys (Android: upload key / keystore; Apple: provisioning profiles and certificates).
- Privacy policy URL and data handling documentation (GDPR/CCPA if applicable).

## PWA -> Store paths
- Android: Use Trusted Web Activity (TWA) to publish a PWA to Play Store (wraps the PWA in a small native shell). Tools: Bubblewrap.
- iOS: Users can add to home screen, but App Store requires native wrapper if you want to publish. Consider building a thin native wrapper in Capacitor or Cordova for iOS and submit to App Store.

## Native app path (React Native / Flutter)
- Create a new repo or monorepo structure (e.g., /mobile) with native project scaffolding.
- Implement screens reusing web components and REST/API layer.
- Implement authentication, image upload, caching, and push notifications (FCM for Android, APNs for iOS).
- CI/CD: GitHub Actions or Fastlane for building and uploading artifacts (AAB for Play, IPA for TestFlight/App Store).

## Store submission checklist (high-level)
1. Prepare builds and test on real devices.
2. Create app entries in Play Console and App Store Connect.
3. Fill store listing: title, short description, long description, promotional assets, screenshots, categories, privacy policy link.
4. Upload signed binaries (AAB for Android; IPA via TestFlight for iOS).
5. Complete questionnaire (privacy, content rating, target audience, ads/in-app purchases).
6. Submit for review; address review feedback.

## Example next steps I can take for you
- Add a PWA manifest + basic service-worker to the repo and update the HTML to register it (fastest path). I will create files: `manifest.webmanifest` and `service-worker.js`, and update `art_marketplace.html` to register the service worker and manifest.
- Or scaffold a React Native project and push a `/mobile` directory (this is larger and needs your confirmation).

## Estimated effort
- PWA + TWA (Android) + small iOS wrapper: ~1–2 days of work to reach a publishable state (depends on polishing and privacy/in-app requirements).
- Full React Native / Flutter native app (both stores): ~1–3 weeks depending on features, CI/CD, and store metadata.

---

If you'd like, I will add a PWA manifest and service worker to the repository and wire them into `art_marketplace.html` so the site is installable and can be wrapped for Play Store using TWA. Say "Add PWA files" and I'll push those files now.
