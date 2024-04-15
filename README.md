![alune_header](https://github.com/TeamFightTacticsBots/Alune/assets/60011425/dd30ed87-c5ca-42eb-810a-da07f6502cf5)
<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12-green" />
  <img src="https://img.shields.io/badge/TFT_Set-11-blue" />
</p>

Teamfight Tactics (TFT) bot for the mobile version. Farms pass experience, events, and tokens.

**Table of Contents**
1. [Features](#features)
   1. [Existing](#existing)
   2. [Planned](#planned)
   3. [Potential](#potential)
2. [Setup](#setup)
   1. [Android Emulator](#android-emulator)
   2. [Bot](#bot)
3. [Running](#running)
   1. [Emulator](#emulator)
   2. [Bot](#bot-1)
4. [Development](#development) 

## Features

The purpose is to farm the TFT pass experience and League event tokens. The bot is "good enough".
We will never support playing ranked with it. We also do not encourage you to learn from its decisions.

### Existing

1. Uses ADB to be able to support every emulator or phone and runs in the background
2. Can start up TFT and queues for normal games
3. Buys experience and shop cards (currently only Heavenly units)
4. Rolls and buys augments
5. Walks around on carousel rounds

### Planned

1. More traits
2. Using optional OCR for economy-based decisions (i.E. Saving up to 50 gold)
   1. Includes rolling store cards
3. A configuration file and or interface
   1. ADB port
   2. Which traits to buy
   3. Logging level
   4. Whether to use OCR
4. Randomization of various sleep intervals
5. Surrendering as early as possible
6. Vote on one of the gates at the start of the game

### Potential
1. Giving items to units 
2. Picking up item orbs
3. Selling item anvils

## Setup

### Android Emulator

1. Download any Android emulator you find trustworthy that also has reasonable ADB support.  
   1. **We do not recommend a specific emulator**, but tested examples are the AVD that comes with Android Studio, Google Play Games PC Developer Build, and LDPlayer9.  
   2. Some emulators may need adjustment of the port our ADB utility connects to. The place to adjust it is [here](./alune/adb.py) in `_connect_to_device`.
2. Install the TFT APK by downloading it from [APKMirror](https://www.apkmirror.com/apk/riot-games-inc/teamfight-tactics-league-of-legends-strategy-game/) and dragging it into your emulator.  
   1. If drag and drop does not work, review your emulator's documentation on how to install APK files.  
   2. **We discourage using Google Play** since it adds overlays the bot does not check for. Also, not entering your Google credentials in emulators is generally good security practice.
3. Start the TFT app and log in to your Riot account.  
   1. If you get a warning about needing to try again later, try a linked social log-in (Google, Facebook, Xbox).

### Bot

1. Download and install [Python 3.12](https://www.python.org/downloads/) for your operating system
2. Open a shell of your choice (Defaults: PowerShell on Windows, Zsh on MacOS, Bash on Linux)
3. Clone this repository: `git clone https://github.com/TeamFightTacticsBots/Alune.git`
4. Go into the repository: `cd Alune`
5. Create a virtual Python environment: `python -m venv alune-venv`
6. Activate the virtual environment.  
   1. PowerShell: `alune-venv\Scripts\Activate.ps1`, Zsh/Bash: `alune-venv/bin/activate`  
   2. This should put `(alune-venv)` in the front of your shell prompt string.
7. Install the project dependencies: `pip install .`
   1. If you want to install for a development environment, use `pip install .[lint]`

## Running

### Emulator

1. Make sure your emulator runs and is interactable.

> [!NOTE]
> While the bot will handle almost any scenario the app may run into, it will never log in for you.
> You do not need to start TFT for the bot to be able to run, but it is a good idea to check if you are logged in.

### Bot

1. If not already active, activate the virtual environment - see setup step 6.  
   1. If you use PyCharm or VS Code, you can use the in-built terminal, which does this automatically for you.
2. Run `python main.py`

## Development

### Linting

The project uses automatic formatting. Use the following lint commands available to you after installation:
```bash
black .
isort .
flake8
pylint main.py alune
```
