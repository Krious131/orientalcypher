# Building the APK

## Option A: GitHub (no installs)
1. Create a new GitHub repo and push this folder to it.
2. Open the repo's Actions tab, run "Build APK" (it also runs on every push).
3. When it finishes (~5 min), download `orbital-cipher-debug-apk` from the run's Artifacts.
4. Unzip it, copy `app-debug.apk` to your phone, and install it (allow "install unknown apps").

## Option B: Android Studio
1. `npm install && npm run build && npx cap sync android`
2. `npx cap open android`
3. Build > Build APK(s). Output: android/app/build/outputs/apk/debug/app-debug.apk

## Option C: command line (needs JDK 21 + Android SDK)
    npm install && npm run build && npx cap sync android
    cd android && ./gradlew assembleDebug
