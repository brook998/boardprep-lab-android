# Vidhyashram BoardPrep Lab — Android APK wrapper

This is a lightweight Android WebView app that opens the live GitHub Pages site:

https://brook998.github.io/boardprep-lab/

## How updates work
The APK loads the live website on launch using Android WebView's normal network-first cache mode. Website content, question banks, and most interface changes can therefore be updated through GitHub Pages without issuing a new APK. The APK itself only needs replacement when the Android wrapper changes (for example, app identity, permissions, native features, or navigation behaviour).

The app needs an internet connection for the live site. This is not a fully offline copy of the website. Existing site-side offline support may still work for resources already cached by its service worker.

## Build the APK without Android Studio
1. Upload the contents of this project into a GitHub repository (or a folder in a repository).
2. Make sure `.github/workflows/build-apk.yml` is uploaded at the repository's `.github/workflows/` path.
3. Open the repository's **Actions** tab.
4. Select **Build BoardPrep Lab APK**.
5. Tap **Run workflow**.
6. When the run finishes successfully, open it and download the `BoardPrepLab-Android-APK` artifact.
7. Extract the artifact ZIP; it contains `app-debug.apk`. Install it on Android. Android may ask you to allow installation from that source.

## Important
- This creates a sideloadable debug APK for testing and direct distribution, not a Play Store release.
- Keep the same `applicationId` and signing key for future APK upgrades. A debug APK built by GitHub Actions may use a different temporary debug key on later runs, so do not treat repeated debug builds as guaranteed in-place upgrades. For stable upgrades, configure a persistent release signing key in GitHub Actions secrets and build a signed release APK.
- Students must allow installation of APKs from the browser/file manager they use.
- Student progress is stored by the website in that app's WebView storage on that device. Clearing app data or uninstalling may remove it. It is not automatically shared with teachers.
- The APK points to the current live site URL. If the website is down or the device has no internet, the main experience may not load.
