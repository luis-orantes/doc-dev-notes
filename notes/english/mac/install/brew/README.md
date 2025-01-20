
# Install Homebrew in Mac




## Introduction

**Homebrew** is a popular package manager for macOS that simplifies the installation, management, and updating of software and libraries directly from the command line.
Its primary purpose is to provide macOS users with a convenient way to install open-source software and development tools that are not readily available through the Mac App Store.
Homebrew automatically handles dependencies, ensuring smooth installations and updates. Its key advantages include saving time with one-line commands, organizing software in a central directory, enabling quick updates via `brew upgrade`, and offering an extensive repository of software through "formulae" (packages) and "casks" (GUI applications).
This makes Homebrew a go-to tool for developers and power users seeking efficiency and control over their macOS environment.




## Instalation

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
