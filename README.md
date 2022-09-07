# `droidrunco`
Your Android device. Cleaner.

[![Go Report Card](https://goreportcard.com/badge/github.com/lavafroth/droidrunco)](https://goreportcard.com/report/github.com/lavafroth/debloatplusplus)

## Introduction

### What?

`droidrunco` is a cross-platform web UI based application which utilizes `adb` and `aapt` to help the user
remove unwanted system apps ([bloatware](https://en.wikipedia.org/wiki/Software_bloat)) from
their android device without root access. The tool aids removal of such apps on all versions of
Android with x86 or ARM processors. This subsequently increases storage space, reduces
power consumption and hardens the user's privacy against vendor distributed spyware.

### Why?

Despite the existence of projects like [the UAD project](https://github.com/0x192/Universal-Android-Debloater),
there has recently been a lot of trouble correlating package names with an app's label.
Manufacturers including Oppo, Xiaomi and the like use obscure package names for their spyware
apps which make it difficult if not impossible to remove them without playing Russian roulette
and risking a [bootloop](https://en.wikipedia.org/wiki/Bootloop).

### How?

`droidrunco` solves the aforementioned issue by fetching the package names as well as app labels
using the `aapt` binaries. This can help the user get better insights on whether an app is
safe to get rid of.

With that being said, a user still runs the risk of hitting a bootloop if they have absolutely
no idea of what they're doing.

## Installation

### Install ADB
#### Linux
- Debian: `sudo apt install android-sdk-platform-tools`
- Arch: `sudo pacman -S android-tools`
- Red Hat: `sudo yum install android-tools`
- OpenSUSE: `sudo zypper install android-tools`

#### macOS
Install [Homebrew](https://brew.sh/#install) and run the following in the terminal:    
```bash
brew install android-platform-tools
```

#### Windows
Install [Chocolatey](https://chocolatey.org/install#install-step2) and run the following in a PowerShell window with administrator privileges:
```powershell
choco install adb
```

### Install `droidrunco`

`droidrunco` can be installed in either of the following ways:

#### Using precompiled binaries
This is what most users will use since it does not involve setting up a development environment. Download the binary for your operating system from the [releases](https://github.com/lavafroth/droidrunco/releases).

#### Using `go install`
If feeling adventurous, try the following to fetch and compile the bleeding edge version of the code.

```bash
go install github.com/lavafroth/droidrunco@latest
```

#### For developers and tinkers
If you're a skeptic willing to inspect or tinker with the code, clone the repository

```bash
git clone https://github.com/lavafroth/droidrunco.git
```

and in the project directory run

```bash
make
```

## Usage
- Kill any previously running adb servers on the host
```
adb kill-server
```
- Backup the data on your device before you accidentally screw up
- [Enable Developer Options and USB debugging on your device](https://developer.android.com/studio/debug/dev-options#enable)
- From the settings, disconnect from any OEM / vendor accounts (deleting an OEM account package could lock you on the lockscreen because the device can no longer associate your identity)
- Run `droidrunco` (this might need administrative rights depending on the operation system in use)
- Visit http://localhost:8080
- Start typing to search for an app
- Click the trash icon next to the app's entry to wipe it
- If an essential system app gets accidentally removed and `droidrunco` is still running, click the recycle icon next to the entry to restore it

## Video demo
[![Demo thumbnail](https://i.ytimg.com/vi_webp/2ym1zA5J6L4/maxresdefault.webp)](https://www.youtube.com/watch?v=2ym1zA5J6L4)
