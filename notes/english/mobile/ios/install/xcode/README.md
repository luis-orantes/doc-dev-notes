
# Install Xcode in Mac




## 1.- Install Xcode

Open the App Store and search for Xcode and nstall the App.
You will need to sign in with your Apple ID account.

> You will probably need to have your Mac updated to the latest version of macOS.
> If your Mac is old and it can't update to he latest macOS version, download an older version of Xcode (the top that works in your Mac) from https://xcodereleases.com/

When the package is downloaded double click on it and drag the uncompressed Xcode to the Application folder.




### Config Xcode

After installing, open Xcode at least once to agree to the terms and conditions and to install any additional required components.




#### Switch the Active Developer Directory

Use xcode-select to switch the active developer directory to the full Xcode installation:

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```




#### Verify the Change
