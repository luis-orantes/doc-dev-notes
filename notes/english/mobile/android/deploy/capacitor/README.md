
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
