
# Install Homebrew in Mac




## Introduction

**Homebrew** is a popular package manager for macOS that simplifies the installation, management, and updating of software and libraries directly from the command line.
Its primary purpose is to provide macOS users with a convenient way to install open-source software and development tools that are not readily available through the Mac App Store.
Homebrew automatically handles dependencies, ensuring smooth installations and updates. Its key advantages include saving time with one-line commands, organizing software in a central directory, enabling quick updates via `brew upgrade`, and offering an extensive repository of software through "formulae" (packages) and "casks" (GUI applications).
This makes Homebrew a go-to tool for developers and power users seeking efficiency and control over their macOS environment.

### Formulae vs Casks

**Formulae** are used to install command-line tools, libraries, and other terminal-based software, such as `git`, `wget`, or programming environments like `python`.
They are lightweight and optimized for terminal use without a graphical interface.
On the other hand, **casks** are designed to install macOS applications that come with a graphical user interface (GUI), such as `Google Chrome`, `Slack`, or `Visual Studio Code`.
Casks automate the process of downloading, installing, and moving GUI-based apps to the Applications folder, eliminating the need for manual installation.

### Apple Notarization Policy

The `--no-quarantine` flag in Homebrew is used during the installation of certain applications to bypass macOS's **quarantine system**, which is part of Gatekeeper, a security feature that flags downloaded files as potentially unsafe until verified.
Normally, macOS applies a quarantine attribute to files downloaded from the internet, requiring them to be explicitly approved by the user before running.
This can cause issues with some Homebrew-installed software that lacks Apple notarization or a valid developer signature, even if the software is safe and verified by Homebrew.
Using `--no-quarantine` prevents this attribute from being applied, allowing trusted but unsigned software to run without additional prompts or manual approval.
This flag is typically needed for command-line tools, open-source utilities, or cross-platform applications that are not notarized for macOS but are distributed through trusted sources like Homebrew.
However, it should only be used when you trust the software's origin.

Example:

```bash
brew install rar --no-quarantine
```




## Installation

Check if you already have Homebrew installed by checking its version.

```bash
brew -v
```

If you have it installed, update your brew before installing anything.


```bash
brew update
```

If you don't have it installed, run the following command in the terminal.
You will need admin password.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```




### Troubleshooting

If you face any trouble when installing Homebrew please refer to the official installation guide at https://docs.brew.sh/Installation.
