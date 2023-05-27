# Install

## Linux or Steam Deck
CSS Loader is available trough [Decky's](https://github.com/SteamDeckHomebrew/decky-loader) built in store

### Installing Decky
[Decky has install instructions on the Decky repository](https://github.com/SteamDeckHomebrew/decky-loader#-installation)

### Installing CSS Loader
1. Open the Quick Access menu
2. Select the tab with the icon of a power plug
3. Select the store icon in the top right
4. Search for 'CSS Loader' and press Install


-----

## Windows

### Standalone
CSS Loader standalone does not use Decky to run. Instead, it runs as a single background application.

!!! warning "Using local images or fonts"
    Windows contains an oddity that makes it impossible to create a symlink without elevated permissions or developer mode. CSS Loader requires a symlink to support local images or fonts.

    Enable developer mode on Windows as follows:

    1. Open Settings
    2. Select 'Privacy & Security'
        - On Windows 10, this menu is called 'Updates & Security'
    3. Select 'For developers'
    4. Toggle 'Developer Mode' to On

    If CSS Loader is already installed, reboot your machine for this to take effect. Developer Mode can be disabled after the backend has at least booted up once.

1. Download the latest .msi release from [Github](https://github.com/beebls/CSSLoader-Desktop/releases)
2. Run the .msi file and follow the on-screen instructions
    - After launching `CSSLoader Desktop` for the first time, you are prompted to install the backend.

### Uninstall Standalone
1. Open task manager and kill `CssLoader-Standalone-Headless.exe`
2. Press the key combination (windows key) + R, and in the opened run box type `shell:startup` and press enter
3. Delete `CssLoader-Standalone-Headless.exe`
4. Open "Apps & Features" in settings, search for `CSSLoader Desktop` and uninstall it.