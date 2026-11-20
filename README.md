# Null Signal — Tier 1 Demo (v0.3)

A GBA-style pixel-art RPG that teaches cyber security, from first passwords to the Academy entrance.
Tier 1 covers chapters 1–15. Landscape only. It plays on iPhone, Android, tablets and computers.

This folder holds three ways to get the demo to players.

| Folder / file | What it is |
|---|---|
| `www/` | The game as an installable web app. It works offline after the first visit. |
| `android/` | Android Studio project. It builds an `.apk` you can send to anyone with an Android phone. |
| `ios/` | Xcode project for iPhone/iPad, for TestFlight. |
| `.github/workflows/` | Builds the APK and hosts the web version on GitHub, with nothing to install on your Mac. |

---

## Option 1: one link for everyone (recommended)

This option works on iPhone and Android with one link and no app store.

1. Create a free GitHub account, then create a new **public** repository called `null-signal`.
2. Upload everything in this folder **except** `node_modules` (drag the files into "Add file → Upload files").
3. In the repository, open **Settings → Pages**. Under *Source*, choose **GitHub Actions**.
4. Open the **Actions** tab and wait for "Publish web demo to GitHub Pages" to show a green tick (about 1 minute).
5. Your link is `https://<your-username>.github.io/null-signal/`

Send that link to your players. They open it, turn the phone sideways and tap **TOUCH TO JACK IN**.

**Installing it like an app** (full screen, icon on the home screen, plays offline):
- **iPhone:** open the link in **Safari**, tap Share, then **Add to Home Screen**.
- **Android:** open the link in **Chrome**, tap the ⋮ menu, then **Install app** (or *Add to Home screen*).

Progress is saved on each player's own device.

> No GitHub? You can drag the `www` folder onto **app.netlify.com/drop** (free account) for the same result.

---

## Option 2: a real Android app (.apk)

### Without Android Studio (built in the cloud)
After step 2 of Option 1, the **Actions** tab also runs **Build Android APK** (about 5 minutes).
Open the finished run, scroll to *Artifacts*, and download **NullSignal-Tier1-Demo-APK**. Unzip it to get `NullSignal-Tier1-Demo.apk`.

Send the `.apk` to your players (Google Drive, email or WhatsApp). On the phone, tap the file and allow
**"Install unknown apps"** for the app that opened it, then install.
Android shows a warning because the app isn't from the Play Store. That is normal for a test build.

### With Android Studio on your Mac
1. Install Node.js 22+ and Android Studio.
2. In this folder, run `npm install` and then `npm run android`.
3. In Android Studio, choose **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.

---

## Option 3: iPhone app (TestFlight)

Apple only allows iPhone apps to be shared through TestFlight or the App Store. This option needs:
- a Mac with **Xcode**
- an **Apple Developer Program** membership (paid yearly)

Steps:
1. Run `npm install` and then `npm run ios`. Xcode opens the project.
2. Under *Signing & Capabilities*, select your team.
3. Choose **Product → Archive**, then **Distribute App → TestFlight**.
4. In App Store Connect, add testers by email. They install the **TestFlight** app and accept the invite.

Until then, iPhone players can use Option 1 (Add to Home Screen). It looks and plays the same.

---

## Updating the demo later
1. Replace `www/index.html` with the new build.
2. In `www/sw.js`, change the version name `null-signal-t1-v03` (for example to `-v04`) so players get the update.
3. Upload the changes to GitHub. The web link and the APK rebuild automatically.

For a new APK version, also raise `versionCode` and `versionName` in `android/app/build.gradle`.

App ID: `com.martinking.nullsignal` · © Martin King. All rights reserved.
