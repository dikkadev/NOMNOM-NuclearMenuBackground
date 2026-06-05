# NuclearMenuBackground

Client-side Nuclear Option mod that lets players replace the main menu background with a local image.

## Install

The easiest way to install and update this mod is with **NOMM**, the Nuclear Option Mod Manager:

- NOMM: https://github.com/Combat787/NOMM
- Latest NOMM download: https://github.com/Combat787/NOMM/releases/latest

You can also install manually from this repository's Releases page. Download the latest `NuclearMenuBackground-v*.zip` archive and extract it into your Nuclear Option `BepInEx/plugins/` folder. The archive already contains the plugin folder layout.

## About this repository

This GitHub repository is a release mirror for NOMNOM/NOMM automatic updates. The canonical source code and development history live in the Forgejo monorepo:

- Source: https://forge.dikka.dev/lab/nuclear_option_mods

## Metadata

- NOMNOM id: `dev.dikka.nuclearmenubackground`
- Author: dikkadev
- Tags: Art, UI
- Release asset format: one `.zip` per release

## Details

`NuclearMenuBackground` is a client-side `Nuclear Option` mod that replaces the main menu background with an image from the player's PC.

If no image is configured, the file is missing, or the image fails to load, the game keeps using its normal default background.

## Features

- Adds a `Browse Background` button to the main menu
- Lets the player pick a local image file with a native file picker
- Stores the selected file path in BepInEx config
- Falls back to the stock `Nuclear Option` menu background automatically

## How It Works

The mod patches `MainMenu.Start`, clones an existing menu button for a small browse action, and swaps any menu `Image` that uses the stock `MainMenuBackground309` sprite.

That makes this project a compact example of the mod structure used in this workspace:

- BepInEx plugin bootstrap in `Plugin.cs`
- Harmony hook and feature logic in `Patches.cs`
- simple config-backed behavior

## Requirements

- `Nuclear Option`
- `BepInEx 5`

BepInEx install guide:

- https://docs.bepinex.dev/articles/user_guide/installation/index.html

## Installation

1. Install BepInEx for `Nuclear Option`.
2. Build the mod or download a release archive.
3. Extract the `NuclearMenuBackground` folder into `BepInEx/plugins/`.

The final layout should look like this:

```text
BepInEx/
  plugins/
    NuclearMenuBackground/
      NuclearMenuBackground.dll
```

## Configuration

Config entries are created automatically after the mod loads.

Main config file:

- `BepInEx/config/dev.dikka.nuclearmenubackground.cfg`

You can configure the mod through the config file directly, but the normal path is to click `Browse Background` from the main menu once the mod is installed.

Example config:

```ini
[General]
## Absolute path to the image used for the main menu background. Leave blank to use the game's default background.
# Setting type: String
# Default value:
Custom Image Path = C:\path\to\Pictures\menu-background.png
```

## Limitations

- This currently targets the stock main menu background sprite only.
- The browse button only appears in the main menu scene.
- If the game changes the menu sprite name in a future update, the target lookup may need to be adjusted.

