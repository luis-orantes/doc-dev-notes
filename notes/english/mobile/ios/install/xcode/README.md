
# Install Xcode in Mac




## 1.- Install Xcode

Open the App Store and search for Xcode and install the App.
You will need to sign in with your Apple ID account.

> You will probably need to have your Mac updated to the latest version of macOS.
> If your Mac is old and it can't update to the latest macOS version, download an older version of Xcode (the top that works in your Mac) from https://xcodereleases.com/

When the package is downloaded double click on it and drag the uncompressed Xcode to the Application folder.




### Config Xcode

After installation, open Xcode at least once to agree to the terms and conditions and to install any additional required components.




#### Switch the Active Developer Directory

Use xcode-select to switch the active developer directory to the full Xcode installation:

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```




#### Verify the Change

You can verify that the change was successful by checking the path of the active developer directory:

```bash
xcode-select -p
```

This should now point to `/Applications/Xcode.app/Contents/Developer`.




## 2.- Install Homebrew

Check if you already have Homebrew installed by checking its version.

```bash
brew -v
```

If you have it installed, update your brew before installing anything.


```bash
brew update
```

If you don't have it installed, run the following command in the terminal.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```




### Troubleshooting

If you face any trouble when installing Homebrew please refer to the official installation guide at https://docs.brew.sh/Installation.




## 3.- Install Ruby

### Use Homebrew to Install a New Ruby Version

> The macOS system Ruby is typically older and can sometimes lead to issues.
> Homebrew allows you to install a newer, separate version of Ruby.

Check the version of Ruby you have installed by default in you mac by running:

```bash
ruby -v
```

Now install Ruby:

```bash
brew install ruby
```

Move to your home directory.

```bash
cd ~
```

Add the next path to your ~/.zshrc file

<!-- Intel path: /usr/local/opt/ruby -->

```bash
export PATH="/opt/homebrew/Cellar/ruby/3.4.1/bin:$PATH"
```
> The numbers after `ruby` will change according to your Ruby version.

Restart the terminal.

> It is important that the variable `$PATH` comes after the folder path to force the OS to run the new version of Ruby and not the default version.

Restart the terminal and check that new version of Ruby has been installed.
Check that it matches with the new installed ruby version.

```bash
ruby -v
```




## 4.- Install CocoaPods

Install CocoaPods using the new Ruby version:

```bash
gem install cocoapods
```

Add the next path to your ~/.zshrc file

<!-- Intel path: /usr/local/lib/ruby/gems/3.2.0/bin -->

```bash
export PATH="/opt/homebrew/lib/ruby/gems/3.4.0/bin:$PATH"
```

> The numbers after `gems` will change according to your Ruby version.

Restart the terminal and check that cocoapods is reachable.

```bash
pod --version
```




### Initialize CocoaPods (if it's a new installation): *** probably not needed, do more tests

If you've just installed CocoaPods for the first time, you might need to set up the master repo. Do this with:

```bash
pod setup
```




## 5.- (Optional) Test Xcode with an Ionic project

```bash
ionic start menu sidemenu
cd menu
npm i @capacitor/ios
npx cap add ios
ionic build
npx cap sync ios
npx cap run ios
```

The last command will open Xcode with the menu project.
Run it with the emulator to see if it works.
