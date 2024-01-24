
# Install Android in Mac




## 1.- Install Java

Install Java LTS 17 from:

https://www.oracle.com/java/technologies/downloads/

> At this moment the latest version of Java LTS is 21 and it isn't compatible with Ionic.




## 2.- Environment

```bash
cd ~
```

Create an empty file configuration (if it doesn't exist).

```bash
touch .zshrc
```

Open this file and add the next line:

```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-17.jdk/Contents/Home
```

Restart the terminal.




## 3.- Android Studio

Download and install Android Studio from:
https://developer.android.com/studio/install




### 4.- Download apis

Create an empty project selecting the second top API.

> Which at this moment is API 33.

> This will download that API.

We will also need the empty project to open the SDK manager.

Open the SDK manager in `tools->SDK manager` and stay in `SDK platfoms` in the menu, and check `show package details`.

In the Android SDK at the left menu select `Android SDK` unselect the top API (34) and select the second top API (33).
Select `platform` and the `Google APIs system image` of your OS (ARM or Intel, according to your type of processor).

> Ionic capacitor runs from Android 5.1 API 22 but it will show only a white screen in the emulator because that API version doesn't come with Chrome.
> In practice, in a device, the App will be shown correctly since vendors will install chrome by default.




### 5.- Add environment variables

Add the next environment variables to your .zshrc file in your home directory.

```bash
export ANDROID_SDK_ROOT="$HOME/Library/Android/sdk"
```
