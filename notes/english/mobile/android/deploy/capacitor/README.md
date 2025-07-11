
# How to build an Ionic Capacitor App for Android production




## 1.- Prepare Project

Delete the `~/android` directory.

```bash
rm -rf android
```

If you are using Git and you have a branch with the production configurations, switch to that branch.

```bash
git switch play-production
```

If you haven't, set the production **id** and **name** in the file `~/capacitor.config.ts`.

> When changing the **id** in Android it is required the Android folder to be regenerated.

Generate the Android folder again.

```bash
npx cap add android
```




## 2.- (OPTIONAL) Configure Ads

If you haven't, configure the AdMob plugin to show real ads. For instance.

```typescript
static IS_TESTING_ADMOB: boolean = false;
```

Open the '~/android/app/src/main/AndroidManifest.xml' file and add the permission to show personalized ads by adding this line after the `</application>` tag closes and before the `</manifest>` tag closes (in line 39).

```xml
<uses-permission android:name="com.google.android.gms.permission.AD_ID" />
```

Add the application ad ID after the `<application>` tag closes (in line 11).

```xml
<!-- Add the following meta-data for AdMob -->
<meta-data
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY"
/>
```

Where the Xs and the Ys are numbers and it should be replaced by your application ID.

> TIP: Is more convenient to keep the manifest file open in Visual Studio with all the configurations done before generating the `~/android` folder.
Undo the changes by pressing `Contro+Z` or 'CMD+Z' one time to recover the changes and save them to make it effective.




## 3.- Generate Assets

If the `~/assets` folder doesn't exist, create it and place your `icon.png` (1024x1024 pixels) there.

```bash
rm -rf assets
```

> Only place the icon. The `splash.png` file should not be present in that directory.

> Please don't confuse this folder with the one in `~/src/assets`, as that is a different folder.

Generate the assets for Android:

```bash
npx @capacitor/assets generate --android

```




## 1.- App Version

Set the app version for Android in file:

```bash
~/android/app/build.gradle
```

For instance:

```gradle
defaultConfig {
    ...
    versionCode 20100
    versionName "2.1.0"
    ...
}
```

### Convention Suggestion

We suggest to use the following convection for **versionName**:

```
Major change.Minor Change or fix.Build
```

Construct the **versionCode** out of the version **versionName** by setting the **Minor Change or fix** and **Build** going from 0 to 99 as the example above.

> This to keep consistent the numbering of versions between iOS and Android since in iOS you can have multiple builds but in Android you need to create a new version in the case you need to upload a new build for the same App version. In iOS it is mandatory to have a versioning of three digits. Also, it is helpful to deduct the App version easily from the **versionCode** in Android.

> Note: this convention only applies to Apps and not to libraries. Libraries should use the standart convection of: Major change.Minor Change.fix




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
