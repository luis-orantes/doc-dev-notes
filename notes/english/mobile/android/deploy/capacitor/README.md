
# How to build an Ionic Capacitor App for Android production




## 1.- App Version

Set the app version for Android in file:

```bash
android/app/build.gradle
```

For instance:

```gradle
defaultConfig {
    ...
    versionCode 1
    versionName "1.0.0"
    ...
}
```

## 2.- Build Ionic

If the `www` directory exists, delete and run

```bash
ionic build --prod
```

## 3.- Obfuscate

obfuscate: install it globally, available in: https://www.npmjs.com/package/javascript-obfuscator

```bash
cd www

javascript-obfuscator main.700104971f02d9e9.js

del main.700104971f02d9e9.js

ren main-obfuscated.700104971f02d9e9.js main.700104971f02d9e9.js

cd ..
```

> Notice that the file that starts with `main` is the one that should be obfuscated.
> There is only one of them.

## 4.- Sync Android

sync with the android folder

```bash
npx cap sync android
```

## 5.- (OPTIONAL) Test

Test the app on device

If you have AdMob set for production,
you could run the app in plane mode.

```bash
npx cap run android
```




## 6.- Bundle

Generate the Android App Bundle (.aab file) for an Ionic Capacitor project using the CLI without opening Android Studio.

```bash
cd android
./gradlew bundleRelease
```

The generated `.aab` file will typically be located in the following directory relative to your project root:

> preferible delete any file before running the command, just to be sure it is generating correctly.

```bash
android/app/build/outputs/bundle/release/app-release.aab
```

## 7.- (OPTIONAL) keystore

Create the keystore.

If you don't already have a keystore.
In this command, alias_name = key (which means the name where the key is stored).

> A key store may contain several alias_name but it is recommended to have only one by key store and one key store per App.

It needs path to C:\Program Files\Java\jdk1.8.0_171\bin

Leave fields empty and when it ask you if data are correct type "yes"

```bash
keytool -genkey -v -keystore appName.keystore -alias key -keyalg RSA -keysize 2048 -validity 10000
```

## 8.- Sign

Sign the bundle

In this command, alias_name = key (which means the name where the key is stored).

> A key store may contain several alias_name but it is recommended to have only one by key store and one key store per App.

```bash
    jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore O:\keystores\brain\premium2\brainPremium2.keystore app-release.aab key

    zipalign -v 4 app-release.aab app-release-done.aab
```

`app-release-done.aab` is the file ready to be uploaded to the Play Store.

> Google Play requires AAB files but Amazon is usind APK
