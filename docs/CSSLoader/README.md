<h1 align="center" class="center">
  <img src="/CSSLoader/img/logo.png" alt="CSS Loader logo, based on paint-roller from Font Awesome" width="200">
  <br>
  CSS Loader - Docs
</h1>
<p align="center">
  <a href="https://discord.gg/HsU72Kfnpf"><img src="https://img.shields.io/discord/1051660079033745478?color=%235865F2&label=discord" /></a>
  <br>
  <br>
  <img src="/CSSLoader/img/Phantom.jpg" alt="CSS Loader screenshot with Phantom and Obsidian" width="80%">
</p>

## 🎨 Creating a Theme

Development for the CSS Loader is intended to be as simple as possible. That being said, we understand not everyone understands how to edit CSS files. If you have any suggestions for how we can make this guide easier to understand, please feel free to create an issue.

### 📋 Prerequisites

- Some experience in CSS and JSON
- Installed CSS Loader
- (Optional) Installed a Chromium-based browser

### 📂 Template

There is [a template repository](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template) you can use for creating your first theme. It contains all the files you need to get started and is pre-configured to work with the CSS Loader.

### 🪁 Getting Started

CSS Loader considers all folders in `~/homebrew/themes` that have a `theme.json` or `theme.css` in the root of that subfolder. Usually, themes have the following structure:

```
homebrew
└── themes
    └── My Epic Theme
        ├── theme.json
        └── shared.css
```

The `theme.json` contains information on how CSS Loader should inject the CSS you provide. For information on how to construct a `theme.json` and see everything it can do, see the [Features](CSSLoader/Features.md#features) page. [A visualizer site](CSSLoader/Visualizer.md#visualizer) is also available to help construct `theme.json` files.

To more easily edit and test CSS, you can use the [CEF Debugger](CSSLoader/Cef_Debugger.md#🌐-cef-debugger) to make edits live on your deck.

For information on submitting a theme, see [Submit To DeckThemes.com](Submission.md#submit-to-deckthemescom)