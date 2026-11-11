# URRT Task Board — Android 4.2.2 APK project

Offline Android WebView wrapper for the legacy-compatible task board.

## Build APK without Android Studio (GitHub Actions)

1. Extract this ZIP.
2. Create a new GitHub repository.
3. Upload the complete `URRT_Android_App` folder contents, including its hidden `.github` folder.
   The repository root must contain the `URRT_Android_App` folder.
4. Commit to the `main` branch, or open **Actions** and run **Build URRT Android APK**.
5. Wait for the workflow to finish successfully.
6. Open the completed workflow run and download artifact `URRT-Task-Board-debug-APK`.
7. Extract the artifact ZIP; it contains `app-debug.apk`.
8. Copy the APK to the tablet over USB and install it. Enable **Settings → Security → Unknown sources** if prompted.

## Cloud build environment

GitHub Actions installs JDK 17, Gradle 8.2, Android SDK Platform 34 and Build Tools 34.0.0.
No Android Studio is required on your laptop.

## Limitations

- Minimum Android API 17 (Android 4.2+); test on the actual tablet.
- HTML is bundled locally; no network is needed to display the board.
- App WebView localStorage is separate from browser localStorage.
- Clearing app data or uninstalling can erase board data. Export/backup is not implemented.
- Join-code and lead login are client-side gates, not secure authentication.
- This workflow creates a debug APK, not a production-signed release.
