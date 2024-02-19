
# Install Android in Mac




## 1.- Install Java

Install Java LTS 17 from:

https://www.oracle.com/java/technologies/downloads/

> At this moment the latest version of Java LTS is 21 and it isn't compatible with Ionic.




## 2.- Environment

Add the JAVA_HOME environment variable.

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




### 6.- Add path

Add the next paths to your ~/.zshrc file:

```bash
export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/tools:$PATH"

export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/platform-tools:$PATH"

export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/tools/bin:$PATH"
```




### 7.- Remove unwanted API

When downloading the API in step 4, the top API (34) is removed but the build tools aren't.
So, we need to remove it by using the next cli command replacing the numbers by the top build tools in `~/Library/Android/sdk/build-tools`.

Restart the terminal; then run:

```bash
sdkmanager --uninstall "build-tools;34.0.0"
```




### 8.- More paths

Add the path to the second top build tools.
Replace the numbers by the build tools numbers (33.0.1).

```bash
export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/build-tools/33.0.1:$PATH"
```




### 9.- Install CLI

Click on tab `SDK Tools` and select `Android SDK Command-line Tools (latest)`.

> This will download the CLI.

Add the following CLI path:

```bash
export PATH="/Users/<your_username>/Library/Android/sdk/cmdline-tools/latest/bin:$PATH"
```




### 10.- Create device
