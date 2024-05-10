
# How to build an Ionic Cordova App for Android Production




## 1.- Build

Build the App for production.

```bash
ionic build --prod
```




### 1.1.- Alternative Build

If the previous command doesn't work try:

```bash
ionic build --minifycss
```




### 1.2.- Clean directory

Move to the build directory and delete all map files.

```bash
cd www/build
del *.map
```




## 2.- Obfuscate

Install the obfuscator globally (if you haven't), available in: https://www.npmjs.com/package/javascript-obfuscator
