# Tauri + SvelteKit + TypeScript + Tailwind + Shadcn + Mobile

This template should help get you started developing with Tauri, SvelteKit, Tailwind, Shadcn, Mobile in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) + [Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode) + [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) + [Tailwind](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) + [ShadcnSvelte](https://marketplace.visualstudio.com/items?itemName=Selemondev.vscode-shadcn-svelte)

## Getting started

### Tauri Prerequisites (For compilation)

Install [Bun](https://bun.sh/)

Install [Rust](https://rust-lang.org/tools/install/)

And execute `rustup target add aarch64-linux-android armv7-linux-androideabi i686-linux-android x86_64-linux-android`, if terminal doesn't have rust-up in it, try restarting your computer.

Follow os specific instructions for Tauri.
For [Windows](https://tauri.app/start/prerequisites/#windows)
For [Linux](https://tauri.app/start/prerequisites/#linux)
For [MacOS](https://tauri.app/start/prerequisites/#macos)

### Android Prerequisites

**For Arch Linux:**

`yay -S android-studio` or if you have chaotic-aur, `sudo pacman -S android-studio`
`yay -S jdk-android-studio` for archlinux-java
`archlinux-java set android-studio`

**For Non-Arch Linux:**
Download and install [Android Studio](https://developer.android.com/studio)

Set enviroment variable
Linux (bash): `export JAVA_HOME=/opt/android-studio/jbr`
MacOs: `export JAVA_HOME="/Applications/Android Studio.app/Contents/jbr/Contents/Home"`
Windows (powershell): `[System.Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\Program Files\Android\Android Studio\jbr", "User")`


In we suggest you to restart your computer after setting all enviroment variables.

***Continue on android studio (For both arch and non-arch)**
- Open android studio
- Create a empty project
- From top left, select Tools > SDK Manager > SDK Tools
- Enable `NDK (Side by side)`, `Android SDK Command-line Tools (latest)`, `Android SDK Platform-Tools`
- Press OK

Set enviroment variables again...

**For Linux:**
`export ANDROID_HOME="$HOME/Android/Sdk"`
`export NDK_HOME="$ANDROID_HOME/ndk/$(ls -1 $ANDROID_HOME/ndk)"`
**For MacOS:**
`export ANDROID_HOME="$HOME/Library/Android/sdk"`
`export NDK_HOME="$ANDROID_HOME/ndk/$(ls -1 $ANDROID_HOME/ndk)"`
**For Windows:**
`[System.Environment]::SetEnvironmentVariable("ANDROID_HOME", "$env:LocalAppData\Android\Sdk", "User")`
`$VERSION = Get-ChildItem -Name "$env:LocalAppData\Android\Sdk\ndk" | Select-Object -Last 1`
`[System.Environment]::SetEnvironmentVariable("NDK_HOME", "$env:LocalAppData\Android\Sdk\ndk\$VERSION", "User")`

### IOS Prerequisites (MacOS only)

Install ios targets

`rustup target add aarch64-apple-ios x86_64-apple-ios aarch64-apple-ios-sim`

Install homebrew if not

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

`brew install cocoapods`

### Start in developer mode

`bun run tauri android dev`
`bun run tauri ios dev`

If emulator not run automatically and dev mode hang in:
```
󰪢 0s 󰜥 󰉋  ••/tauri-shadcn-svelte-template 󰜥 󰘬 main 
    bun run tauri android dev
$ tauri android dev
        Info Using Android Studio's default Java installation: /opt/android-studio/jbr
        Info Using installed NDK: /home/erdem/Android/Sdk/ndk/29.0.14206865
```
state, then you can try:
`$ANDROID_HOME/emulator/emulator -list-avds`
see your avd, and you run it by:
`$ANDROID_HOME/emulator/emulator -avd Medium_Phone_API_36.1`

after that you can run `bun run tauri android dev` with ease.

For more comprehensive guide you can visit [tauri docs](https://tauri.app/start/prerequisites/)