# Prime One — Android APK project

Prime One is packaged as a native Android WebView app. The original uploaded Prime One HTML app is bundled locally in `app/src/main/assets/index.html`, so the main interface does not depend on a hosted website. The supplied fantasy-knight artwork is used for the launcher icon and in-app favicon. Embedded cover art has been moved into optimized local image assets so the main HTML stays small enough for GitHub browser uploads.

## Build the APK on GitHub

1. Create a new GitHub repository.
2. Upload the **contents** of this project folder (the `.github` folder must be included at the repository root).
3. Open the repository's **Actions** tab.
4. Select **Build Prime One APK** and press **Run workflow**, or push to `main` / `master`.
5. When the run finishes, open it and download the `Prime-One-APK` artifact. Extract it to get `app-debug.apk`.
6. Transfer the APK to your Android phone and install it. Android may ask you to allow installation from that source.

## Device permissions

- On first launch, Android may ask for notification permission.
- Tap **Files** in Prime One, then **Grant full storage access**. Android Settings opens; enable **Allow access to manage all files** and return to the app.
- Android may separately prompt for media or document selection where relevant.

Android does not permit an app to silently grant itself permissions. `MANAGE_EXTERNAL_STORAGE` is a special-access permission and Google Play heavily restricts its use; this project is intended for personal installation/testing or another distribution path where the permission is permitted.

## Added device file tools

The floating **Files** control opens a native-backed file browser for shared storage (up to 2,500 matching files per search). Common image files can be previewed (up to 12 MB each). Text files can be edited and saved. The trash control moves a file into Prime One's private recycle-bin folder; items can be restored to their original path or permanently deleted. If a file already exists at the original path, restore is safely refused rather than overwriting it. The app excludes Android's protected `Android/data` and `Android/obb` trees from its browser.

The recycle bin is private to this app installation. Clearing app data or uninstalling Prime One can remove its contents. It is not a replacement for a separate backup.

## Existing Prime One features

The original bundled HTML app is preserved, including its music player interface and the existing equalizer, playlist/library, tag/artwork editing and cloud connection flows. Google Drive / Google Photos features still require their supported Google sign-in and API configuration; this wrapper does not create Google credentials or bypass provider permissions.

## Technical notes

- Package: `com.primeone.player`
- Minimum Android: 8.0 (API 26)
- Build: Android Gradle Plugin 8.7.3 / Gradle 8.9 / Java 17
- APK produced by GitHub Actions: `app/build/outputs/apk/debug/app-debug.apk`
- The GitHub Actions workflow builds a debug APK. For public distribution, configure a release signing key securely in GitHub Actions secrets and review Android/Google Play policy requirements.
