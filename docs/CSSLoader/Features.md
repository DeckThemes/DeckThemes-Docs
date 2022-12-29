# Features

?> The [source code of CSS Loader](https://github.com/suchmememanyskill/SDH-CssLoader) can be found here

# 🖌️ Simple Themes
*Requires Manifest Version 1+*

Themes are folders with CSS files and a single `theme.json` file inside. The `theme.json` determines how everything will be displayed and any options if the theme has them. The CSS Loader loads themes from `/home/deck/homebrew/themes`.

![SimpleTheme](img/simpletheme.png)

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template/tree/main/Sample%20Simple%20Theme)

For a simple theme, the `theme.json` should look something like this.

```json
{
  "name": "Theme Title",
  "author": "GitHubUsername",
  "target": "Library",
  "manifest_version": 4,
  "description": "This is an example description.",
  "version": "v1.0",
  "inject": {
    "shared.css": ["SP"]
  }
}
```

- The name element describes the theme name. This is also used as the folder name for the theme store.
- The author element describes the theme author.
- An optional version field can be added. If no version field is found, the version defaults to `v1.0`.
- The manifest version tells the CSS Loader which version of `themes.json` you are using. The current version is `4`.
- An optional description can be added to show a text description in the theme store.
- The inject tab is a dictionary of relative CSS file paths as keys, and a list of tabs you want the CSS to be injected into.
- The target field describes what part of the UI your theme themes. This is only useful for submitting a theme. The following options are available, but more can be added by creating an issue:
  - System-Wide
  - Background
  - Keyboard
  - Home
  - Background
  - Library
  - Store
  - Friends and Chat
  - Media
  - Downloads
  - Settings
  - Lock Screen
  - Tweak
  - Other

# 🖼️ Complex Themes
*Requires Manifest Version 2+*

![ComplexTheme](img/complextheme.png)

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template/tree/main/Sample%20Advanced%20Theme)

A complex theme is a theme with patches. Patches are menus that apply additional CSS depending on the selection. The `theme.json` for a complex theme should look something like this.

```json
{
  "name": "Colored Toggles",
  "version": "v1.2",
  "author": "SuchMeme",
  "target": "System-Wide",
  "description": "this is an example description",
  "manifest_version": 2,
  "inject": {
    "shared.css": ["QuickAccess", "SP", "MainMenu"]
  },
  "patches": {
    "Theme Color": {
      "default": "Orange",
      "type": "dropdown",
      "values": {
        "Orange": {},
        "Lime": {
          "colors/lime.css": ["QuickAccess", "SP", "MainMenu"]
        },
        "Red": {
          "colors/red.css": ["QuickAccess", "SP", "MainMenu"]
        },
        "Magenta": {
          "colors/magenta.css": ["QuickAccess", "SP", "MainMenu"]
        },
        "Gradient RGB": {
          "colors/gradient_rgb.css": ["QuickAccess", "SP", "MainMenu"]
        },
        "Gradient Deck": {
          "colors/gradient_deck.css": ["QuickAccess", "SP", "MainMenu"]
        }
      }
    }
  }
}
```

> The patches section is a dictionary of patch names as key. The value is a dictionary where keys are it's options and their value is the applied CSS, similar to the "inject" section. The special key "default" is required to indicate a default option.

Patches allow for choosing between a dropdown, a checkbox (toggle), or a slider for patch selection using the `type` field.

## 🔽 Dropdown
*Requires Manifest Version 2+*

`"type": "dropdown"`

This is the default value. This type gives a dropdown of all keys in the `values` dictionary. Choosing an option injects only the CSS specified within the selected value.

![dropdown](img/dropdown.jpg)

## 🎚️ Slider
*Requires Manifest Version 2+*

`"type": "slider"`

This type gives a slider with the labels of the points of all keys in the `values` dictionary. Choosing an option injects only the CSS specified within the selected value.

![slider](img/slider.jpg)

## ✅ Checkbox (Toggle)
*Requires Manifest Version 2+*

`"type": "checkbox"`

This type represents the `values` field as a toggle. This type is unique in the sense that it limits what options you can put in the `values` dictionary. You need to have a `Yes` and a `No` option in the `values` dictionary, otherwise, the type falls back to a dropdown. When the toggle is on, `Yes` is selected, otherwise, `No` is selected.

![checkbox](img/checkbox.jpg)

## 🚫 None
*Requires Manifest Version 3+*

`"type": "none"`

Displays an arrow with the patch name. Has no functional use. For use with components.

# ➕ Additional Features

## 📁 Local Files

You can access files locally from CSS if you use the correct URL. You can access files like fonts, images, and more by using the following URL.

`/themes_custom/{your_theme_name}/{image_path}`

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template/tree/main/Sample%20Background%20Theme)

## 📦 Adding Dependencies
*Requires Manifest Version 3+*

Dependencies are useful if you want to bundle another theme or want to make small modifications to an existing theme. All dependencies get enabled alongside your theme.

In the `themes.json` file, specify a field called `"dependencies"`. This is a dictionary in which the keys are the name of the theme you want to be dependencies, with their values being another dictionary. This dictionary's keys are the name of any patch this theme has, and the value is the name of a value in the patch. If you don't want to modify any patch value, write `{}` as the value.

```json
"dependencies": {
    "Switch Like Home": {
        "No Friends": "Yes"
    },
    "Clean Gameview": {}
}
```

> If a theme has a dependencies field like the one above, it will enable both Switch Like Home and Clean Gameview. Switch Like Home's 'No Friends' patch gets forced to 'Yes'.

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template/tree/main/Sample%20Dependency%20Theme)

## 🗃️ Components

Components are a way to attach extra parts to a selectable patch option. Inside a patch, you can make a `"components"` field (its value is a list), and put the components inside.

### 🎨 Color Picker
*Requires Manifest Version 3+*

![Color picker](img/color-picker.jpg)

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Theme-Template/tree/main/Sample%20Color%20Picker%20Theme)

The color picker component injects a CSS variable with a user-specified color.

```json
"components": [
    {
        "name": "Background Picker",
        "type": "color-picker",
        "on": "_",
        "default": "#000",
        "css_variable": "test-main-color",
        "tabs": ["QuickAccess"]
    }
]
```

- `name` refers to the name of the component shown to the user
- `type` refers to the type of component
- `on` refers to what patch value the component should be displayed on
- `default` refers to what default hex color the color picker should default to
- `css_variable` refers to the name of the CSS variable that will be injected
- `tabs` refers to what tabs the CSS variable will be injected into

### 📷 Image Picker
*Requires Manifest Version 4+*

![imagepicker](img/image-picker.jpg)

[Here is an example.](https://github.com/suchmememanyskill/Steam-Deck-Themes/tree/main/static-background)

The image picker component injects a user-supplied file using a file picker into a CSS variable as `url(path/to/file)`. Only files from `~/homebrew/themes` can be selected.

```json
"components": [
    {
        "name": "Image Picker",
        "type": "image-picker",
        "on": "_",
        "default": "ThemeName/background.jpg",
        "css_variable": "test-main-image",
        "tabs": ["SP"]
    }
]
```

- `name` refers to the name of the component shown to the user
- `type` refers to the type of component
- `on` refers to what patch value the component should be displayed on
- `default` refers to what default file path the image picker should default to (relative to `~/homebrew/themes`)
- `css_variable` refers to the name of the CSS variable that will be injected
- `tabs` refers to what tabs the CSS variable will be injected into

## 🔠 CSS Variables
*Requires Manifest Version 5+*

Instead of creating a single file that just stores 1 css variable, a shorthand is available to do it directly in the `theme.json`.

```json
"inject": {
  "shared.css": ["SP"],
  "--my-cool-css-var": ["#FFF", "SP"]
}
```

By putting 2 dashes in front of a key in any inject section, CSS Loader will read the first variable of the key's value, and inject that into the remaining array elements as tabs.