# URRT Task Board V2.1 (Android WebView)

Lightweight offline task board for the UIU Rescue Rover Team. The Android app is a Java Activity hosting a local HTML/CSS/JavaScript interface in WebView; it is not a native Android UI.

## V2.1 visual refinement

- Refined task cards, priority accent rails, status chips, team panels, toolbar, critical-deadline panel, and add-task form.
- Updated header logo asset path to `app/src/main/assets/logo.png`. Place the team logo image at that exact path; use PNG format and preferably a square transparent image.
- No new task-management features or data-schema changes.
- Android app version `2.1.0` (versionCode 3).

## V2 changes

- Hybrid interface: dark command header/navigation with a light task workspace and teal accents.
- Task priority: Critical, High, Medium, Low. New tasks default to Medium; legacy tasks without a priority are migrated in memory to Medium and saved on the next write.
- Priority-first task ordering within each subteam.
- Global task search across task title, assignee, and subteam name.
- Status and priority filters, with a one-tap clear action.
- Admin-only JSON backup generation and paste-based restore.
- Existing V1 localStorage keys and task structure retained: `urrt_v4`, `urrt_config`, `urrt_logs`, `urrt_accounts`.
- Android app version `2.1.0` (versionCode 3).

## Build with GitHub Actions

The workflow `.github/workflows/build-apk.yml` builds a debug APK when pushed to `main` or manually dispatched.

1. Push the repository contents to GitHub.
2. Open **Actions → Build URRT Android APK**.
3. Run the workflow or push a commit to `main`.
4. Download the `URRT-Task-Board-debug-APK` artifact.

The workflow expects the project at `URRT_Android_App/` in the repository root.

## Backup and restore

1. Log in as Team Lead.
2. Open **Backup / Restore**.
3. Select **Generate backup**. The JSON is selected in the text area; copy it using the tablet's text-selection menu and store it privately.
4. To restore, paste a previously generated JSON backup into the text area and select **Restore backup**.

A backup includes board data, settings, activity logs, and locally stored lead account records. Account passwords are Base64-encoded in the existing V1 implementation; Base64 is reversible and is not password hashing. Treat backup JSON as sensitive. Restore replaces the current local data on that device.

## Important limitations

- Data is stored locally in the app WebView. This build does not synchronize across devices or users.
- Lead login and join-code checks are client-side gates, not secure authentication or authorization. Anyone with access to the app's local storage or source can bypass them.
- Backups are manual. Keep copies outside the app; clearing app data can erase the board.
- This project targets Android API 17 minimum and uses legacy-compatible JavaScript/CSS. Actual rendering should still be checked on the target Android 4.2.2 tablet because vendor WebView implementations vary.
- The workflow builds a debug APK, not a Play Store release-signed APK.


V2.3: V2.1 button/control styling retained. Gloss applied to team/task cards only; compact assign/deadline date row added. Uses ES5 and float-based layout for Android 4.2.2 WebView.


V2.5 UI refinement: task finder controls use full-width floated layout (no flexbox); glossy control surfaces; login remembers lead name but clears password on open/close; custom month calendar picker for assign date/deadline; assign date defaults to today. Uses ES5-compatible JavaScript and legacy WebView CSS.
