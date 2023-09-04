# Profiles

Profiles are themes that store configuration of other themes. This way, an entire set of themes and their configuration can be shared or stored in a Profile theme.

When enabling a Profile, it will enable all themes in the Profile's configuration, and overwrite the configuration of those themes with the configuration stored in the Profile.

When disabling a Profile, it will disable all themes in the Profile's configuration.

## Creating a Profile

First, enter the CSS Loader QAM menu

1. Open the Quick Access Menu
2. Select the 'Plug' tab
3. Select 'Css Loader'

Then

1. Open the 'Selected Profile' dropdown near the top
2. Scroll to the bottom of the opened menu and select 'New Profile'
3. Give the profile a name and select 'Create'
    - This will store all currently active themes and their configuration in a new profile

## Using a Profile

Installed or created profiles show up in the dropdown 'Selected Profile' near the top of the QAM CSS Loader menu. Opening this dropdown allows a user to pick a profile to switch to. This will disable all the users themes, then load the theme data stored in the profile.

Profiles update automatically whenever any configuration changes: they will keep track of what the user enables and disables, and save it inside the profile.

## Sharing a Profile

!!! warning "Image usage with Profile"
    If the Profile was created with a theme using a custom image, you are required to put this image in the Profile's directory for it to be shared properly.

0. For steam deck users: Go into desktop mode
1. Open dolphin (linux) and navigate from the home tab to the `homebrew` directory, then to the `themes` directory. 
    - The technical path name for this would be `~/homebrew/themes`
    - For CSS Loader Desktop users, open CSS Loader Desktop, go to `Manage Themes` then select `Open Themes Directory`
2. Find a directory with the same name as your Profile
    - From CSS Loader v1.9.0 onwards, the folder name of a profile ends in `.profile`
3. Right click this directory, and compress as .zip

You can now share this .zip file with friends. This will give an identical setup to when the Profile was created. Note the themes used in the Profile have to be downloaded first

### Sharing to deckthemes.com
These Profiles can also be shared to the theme repository. See [the submission docs](/Submission#zip) for more details. The gist of it is as follows:

1. Navigate to [DeckThemes](https://deckthemes.com/submit)
2. Log in with discord
3. Press the upload arrow in the top right
4. Set the `Upload Method` dropdown to `Upload Zip`
5. Upload your Profile zip
6. Submit!