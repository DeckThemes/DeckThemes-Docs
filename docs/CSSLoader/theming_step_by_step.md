This page will guide you through creating a theme using CSS Loader

## Prerequisites

- Knowledge of CSS and JSON
    - If you don't know CSS, [W3schools](https://www.w3schools.com/css/default.asp) has some good free documentation on it
- Having CSS Loader installed
    - The process of creating a theme is slightly different between the Steam Deck and Windows versions of CSS Loader.
        - For the Steam Deck version, it's highly recommended to have multiple monitors or an external PC/Laptop
        - For the Steam Deck version, if working from an external PC/Laptop, you need to know how to edit files remotely on the Steam Deck.
            - If you don't know how to do this, an option for this is to use ssh/sftp. First, enable ssh on the Steam Deck using Konsole on desktop mode: `sudo systemctl enable sshd && sudo systemctl start sshd`. Then, on the external PC/Laptop install WinSCP, and enter your Steam Deck IP, username (by default `deck`) and password. Steam Deck IP can be found in system settings, under your WIFI connection.
- Having Visual Studio Code installed
    - Download link for [Visual Studio Code](https://code.visualstudio.com/)
    - It is recommended to install the [CSS Loader](https://marketplace.visualstudio.com/items?itemName=DeckThemes.css-loader-for-vs-code) extension for Visual Studio Code, to help editing the `theme.json`
    - It is recommended to install the [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) extension to more easily spot errors made in css and json files

## Introduction

The Steam Deck (or Big Picture Mode) UI is written entirely as a webpage. This means you can style it the same way as a regular web page too, namely using CSS. CSS defines how a webpage should 'look'. Using CSS, for example you can say 'Make every paragraphs on this page red'.

Steam is using CEF (Chromium Embedded Framework) version 85 under the hood. This makes it very similar in behavior to the regular Chrome/Chromium browser. Just like a regular browser, CEF can open multiple tabs. Steam uses this feature to display different parts of the UI. 

Here's an example of the tabs the Big Picture Mode UI uses:

![Cef Tab Names](./img/cef-tab-names.png){align=left}

- `QuickAccess_uid(number)`: When the :material-dots-horizontal: button is pressed, this tab is displayed. CSS Loader offers a shorthand for this tab called `QuickAccess`.
- `MainMenu_uid(number)`: When the `STEAM` button is pressed, this tab is displayed. CSS Loader offers a shorthand for this tab called `MainMenu`.
- `notificationtoasts_uid(number)`: When a notification shows up in the bottom right, this tab is displayed. You can target this tab using the definition `notificationtoasts.*`.
- `data:text/html(...)`, `(Steam store page name)`: Whenever a webpage is displayed, like the steam store, this tab is used. CSS Loader offers a shorthand for this tab called `store`.
- `Steam Big Picture Mode`: The main content window of BPM. If it isn't in a sidebar menu, it's likely displayed here. CSS Loader offers a shorthand for this tab called `bigpicture`.

<div style="clear: left;" />

## Format of a theme

CSS Loader is made to inject CSS into arbitrary Steam tabs. It does this by loading a definition of which .css files should be injected where. This definitions file is called `theme.json`. More about all available features in this file can be read in the [Features](Features.md) page.

CSS Loader considers all folders in `~/homebrew/themes` that have a `theme.json` in the root of that subfolder themes. Usually, themes have the following structure:

```
homebrew
└── themes
    └── My Epic Theme
        ├── theme.json
        └── shared.css
```

Time to create the file structure for your theme:

1. Open the themes folder
    - On Windows, open `CSSLoader Desktop`, navigate to the `Manage` tab and `Open Themes Directory`
    - On Steam Deck, navigate to `Home(~) > homebrew > themes`
2. Create a new folder. This folder should be the name of your theme.
3. Create a file called `theme.json` in this new folder.
4. Create a file called `share.css` in this new folder.

### Setting up the theme.json

Open up the theme.json inside Visual Studio Code, and copy the following snippet inside of it

```json
{
    "name": "Name of your theme",
    "author": "Your username",
    "version": "v1.0",
    "description": "A description to your theme",
    "target": "Other",
    "manifest_version": 8,
    "inject": {
        "shared.css": ["bigpicture", "QuickAccess", "MainMenu"]
    }
}
```

- `name`: The name of your theme
- `author`: The author of your theme (probably yourself)
- `version`: The version of your theme. It's recommended to [follow semver semantics](https://docs.npmjs.com/about-semantic-versioning)
- `description`: The description of your theme. Can also be input into the site during submitting the theme.
- `target`: The target of your theme. Can also be input into the site during submitting the theme.
- `manifest_version`: Defines the features you can use inside the theme.json. The latest manifest version is 8.
- `inject`: Defines which files gets injected into which tabs. `shared.css` defines the css file to be injected, the array behind it contains which tabs it should be injected into. Please replace `["bigpicture", "QuickAccess", "MainMenu"]` with the tabs you want to inject css into.

After making edits to the `theme.json` (or any .css file), you need to reload your themes before the changes apply. You can let CSS Loader automatically reload using the [file watcher](./Features.md#file-watcher) feature.

## Making CSS

1. Connect to [the CEF debugger](./theming_step_by_step.md)
2. Connect to the tab you want to make edits to
3. [Give advice on how to theme specific elements]
4. Copy your changes to `shared.css` inside your newly created folder on your device.


## Closing

If you need any help, feel free to join [our discord](https://discord.gg/HsU72Kfnpf). More features of the `theme.json` can be found inside the [Features](./Features.md) tab.
