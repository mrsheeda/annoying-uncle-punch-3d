# Annoying Uncle Punch 3D (Android)

A native Android app that wraps the game in a full-screen WebView. The 3D game (Three.js r128, bundled as `three.min.js`) lives in
`app/src/main/assets/index.html`, so everything works offline.
(Only the Google Fonts headline font needs internet; without it a system font is used.)
The 3D game needs a device with WebGL.

## Get the APK

**GitLab:** push this folder to a project. The `build_apk` job in `.gitlab-ci.yml` runs and
`app-debug.apk` appears under the job's artifacts.

**GitHub:** the workflow is in `ci/github-actions-android.yml`. In the GitHub web editor, move it to
`.github/workflows/android.yml` (edit the file and change its path), commit, then open
Actions > "Build APK" and download `annoying-uncle-punch-apk` from the finished run.

**Locally (Android Studio or JDK 17 + Android SDK 34):**

    ./gradlew assembleDebug

The APK is at `app/build/outputs/apk/debug/app-debug.apk`. Copy it to a phone, allow
"install unknown apps", and open it.

## Notes
- This is a debug-signed APK, fine for installing on your own devices. For Google Play you
  need a release build signed with your own keystore (`./gradlew bundleRelease`).
- Change the app name in `AndroidManifest.xml` and the package id in `app/build.gradle`
  (`applicationId`) plus the `com/example/unclepunch` folder and `package` line.
- Replace the launcher icons in `app/src/main/res/mipmap-*`.
