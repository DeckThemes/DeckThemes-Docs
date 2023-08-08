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

## Introduction
