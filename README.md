# QB Dragon Aim — Android Studio source

Prototype UI project using Kotlin + Jetpack Compose.

## Included
- Animated-style dark red/purple key screen and 3-tab dashboard
- 15 independent preference-backed switches with toggle sound
- Device/app process information panel and a live app-CPU estimate graph
- Free Fire / Free Fire MAX selector
- Honest 30-second optimization progress animation, then opens the selected installed game
- Admin info: QbaoTweakxVft King — PHẠM GIA BẢO

## Important: configure your real key API
Open `app/src/main/java/com/qba/dragonaim/ApiConfig.kt`.
The sample expects:
- POST `https://qbaonew1.onrender.com/api/check-key`
- JSON request: `{"key":"YOUR_KEY"}`
- JSON response: `{"valid":true}` (or `{"success":true}`)

You said you have an API, but the exact endpoint and response schema were not provided. Change `KEY_CHECK_URL` and `isKeyValid()` in `MainActivity.kt` to match your server. The base website URL alone does not establish an API contract. Do not put private server secrets in the Android app.

## Build
1. Open this folder in Android Studio (recent stable version).
2. Allow Gradle sync.
3. Use **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

This is source code, not a prebuilt APK. I have not run an Android/Gradle build in this environment.

## Limitations / safe behavior
- The 15 toggles save app-local preferences only; they do not modify game aim, recoil, memory, or files.
- CPU graph estimates CPU time used by this app process, not total device CPU usage.
- Android does not permit an ordinary app to force-close other apps or freely read all device performance stats.
- The progress animation represents local UI/preparation work; it does not inject code into a game.


## Device check and Shizuku
- Shows Android release/API level before entering the dashboard.
- Adds a real Shizuku permission request flow using the Shizuku API. The app must request permission while the Shizuku service is running to appear as a permission-requesting app in Shizuku's manager UI.
- Adds a skip option. Skipping does not grant root; Admin displays "Chưa xác minh root (đã bỏ qua)".
- The root indicator is a simple local heuristic and cannot guarantee that root is available.
- Adds package visibility declarations for Free Fire and Free Fire MAX. The Open Game button works without root when the selected game is installed and launchable.


## Logo and GitHub Actions
- App launcher icon uses the supplied purple/black “QBAO × SADZ TWEAK MENU” artwork.
- GitHub Actions workflow: `.github/workflows/android.yml`. Upload the ZIP contents to the repository root, then open **Actions** and run **Build Android APK**. The generated APK is available as an artifact.
- This is a UI prototype; switches do not change game memory, aim, recoil, or game files.
