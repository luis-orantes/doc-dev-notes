
# Install Android in Mac




> These instruction notes require installing software using **Homebrew**.
If you haven't installed it yet, follow the steps provided in [this link](https://github.com/luis-orantes/doc-dev-notes/tree/main/notes/english/mac/install/brew).
If you already have **Homebrew** installed, remember to update it by running `brew update` before installing anything.




## Install Java

Install Java LTS 17 by running:

```bash
brew install openjdk@17
```

<!-- link to install manually
https://www.oracle.com/java/technologies/downloads/
-->

> At this moment the latest version of Java LTS is 21 and it isn't compatible with Ionic.




## MacOS Java Wrappers

MacOS expects Java installations to be located in `/Library/Java/JavaVirtualMachines`.
By creating the symlink, you align the Homebrew-installed JDK with macOS's expectations.
Run the follwing command:

```bash
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-17.jdk
```




## Environment

Add the JAVA_HOME environment variable.

Move to your home directory.

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

# path to the Java cli
export PATH=$JAVA_HOME/bin:$PATH
```

Restart the terminal.




## Android Studio

Install Android studio by running:

```bash
brew install --cask android-studio
```

<!-- link to install manually
https://developer.android.com/studio/install
-->




### Download apis

Create an empty project selecting the second top API.

> Which at this moment is API 34.

> This will download that API.

We will also need the empty project to open the SDK manager.

Open the SDK manager in `tools->SDK manager` and stay in `SDK platfoms` in the menu, and check `show package details`.

In the Android SDK at the left menu select `Android SDK` unselect the top API (36) and select the second top API (35).
Select `platform` and `Google Play ARM 64 v8a System Image`.




## Add environment variables

Add the next environment variables to your .zshrc file in your home directory.

```bash
export ANDROID_SDK_ROOT="$HOME/Library/Android/sdk"
```




## Add path

Add the next paths to your ~/.zshrc file:

```bash
export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/platform-tools:$PATH"
```




## Install Android SDK Command-Line Tools

Open Android Studio.
Go to Preferences: **Android Studio > Settings** (or Command + ,).
Navigate to **Languages & Frameworks > Android SDK**.
In the SDK Manager, go to the SDK Tools tab.
Check the box for Android SDK Command-line Tools (latest).
Click Apply, then OK to install.

Add the next paths to your ~/.zshrc file:

```bash
export PATH="$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$PATH"
```




## Remove unwanted API

When downloading the API in step 4, the top API (35) is removed but the build tools aren't.
So, we need to remove it by using the next cli command replacing the numbers by the top build tools in `~/Library/Android/sdk/build-tools`.

Restart the terminal; then run:

```bash
sdkmanager --uninstall "build-tools;35.0.0"
```




## More paths

Add the path to the second top build tools.
Replace the numbers by the build tools numbers (34.0.1).

```bash
export PATH="$ANDROID_SDK_ROOT/Library/Android/sdk/build-tools/34.0.1:$PATH"
```

Restart the terminal and run `aapt`. It should be reachable.




## Install CLI

Click on tab `SDK Tools` and select `Android SDK Command-line Tools (latest)`.

> This will download the CLI.

Add the following CLI path:

```bash
export PATH="/Users/<your_username>/Library/Android/sdk/cmdline-tools/latest/bin:$PATH"
```




## Create device

In Android Studio go to `tools->Device manager` and click on `Device`.

In the just opened right side Select `phone->Galaxy Nexus`(720x1280)
and click in next select the API 34 image and name the AVD `14api34`.
Where 14 stands for the Android version and 34 for the API version.

> These are the minimal required dimensions for a phone screenshot in Google Play.

Click on `Show Advanced Settings`.

Select the option `Emulated Performance -> Boot option -> Cold boot`.

> The default option is `quick boot` which leads to faster starting of the emulator but because the OS doesn't restart it may lead to instability.
`Cold boot` guarantees that the emulator is restarted completely in every boot.




### (Optional) Extra devices

You may need to use the following dimensions for getting the screenshots required by Google Play.
For doing this you may just need to edit the AVD

* Tablet 7": 7" WSVGA (Tablet) 600x1024.
* Tablet 10": Nexus 10 (2560x1600).
* (Not required) Chrome book: TODO=> ***




### (Optional) iPhone devices

You may use the Android emulator to take the screenshots for the iPhone.
When editing the AVD size click on `New Hardware Profile` and fill the info using the following data:

* iPhone 14 Pro Max 6.7": 1290x2796.
* iPhone 6 Plus 5.5": 1242x2208.
* iPad: TODO=< ***

*** TODO=< remove buttons for screenshots
