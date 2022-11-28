# Setting up Stock Game for Skyrim SE/AE - by Althro

## Summary
Stock game is a feature utilised by quite a Wabbajack modlists for Skyrim to ensure that the original game folder is kept clean. It's important to keep the main game folders clean and compartmentalise modding as much as possible to minimize any potential issues. Stock game functions by creating a copy of your Skyrim install in a new folder and redirecting all the paths in that particular MO2 instance to use that. 

This guide will show you how to set up stock game, setup Mod Organizer 2 for Stock Game, get the paths correct for tools such as xEdit and also cover some common queries. The guide will use Skyrim Anniversary Edition for the setup; however, the same process applies to regular Skyrim Special Edition. This guide assumes you have all the tools such as Creation Kit, Mod Organizer, xEdit and others already downloaded.

## Initial Setup
### Installing Skyrim
The first step in the procedure of setting stock game is ensuring that you have a completely clean and fresh installation of Skyrim. This must not be modified in any way, save for downloading the CC content. We won't cover how to reinstall the game, but it is relatively simple. Make sure you are installing it somewhere outside of Program Files such as `C:\Games`.

Once you have redownloaded the game, run it once to have it download all the CC content. This may take a while depending on your internet speed and might fail a few times. Simply go into the Creation Club section and press the "download all" button.

### Making the Game Root and Copying across the files
To make the Stock Game folder, complete the following.

1. Make a new folder in a location that is on the root of your drive, or in a location such as `C:\Games\`
2. Make another new folder inside of that called "Game Root" or "Stock Game" (I prefer Game Root).
3. Open that folder and then open a new explorer window.
4. Navigate to where your Skyrim is installed. It is typically nested similar to `\steam\steamapps\common\Skyrim Special Edition`.
5. Select everything in the folder **EXCEPT `gpu.txt`** and **copy** it into the folder you just created. **DO NOT MOVE IT.**

![Copy These Files](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/CopyThis.webp)

*Everything that is not gpu.txt.*

### Setting up Mod Organizer 2 to use the Stock Game
*Note: This section is designed for use with the Archive version of Mod Organizer 2. I do not use the installer version, only the archive version*

Open the MO2 archive and copy across all the data inside the zipped file to the master folder which you initially created. **Do not copy it to the game root folder.** Your folder should look like this picture.

![MO2 Main Folder](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/MO2MainFolder.webp)

Double click the ModOrganizer.exe file to open Mod Organizer. Create a new Portable instance and map the game location to be the `Game Root` folder which has your Skyrim install in. **Ensure this is correct by pressing the back arrow to ensure it is mapped correctly. It should look like the picture below**.

![Instance Setup](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/MO2InstanceSetup.webp)

Finish setting up the Instance. 

### Cleaning up the CC content
If you are using version 1.6.X of Skyrim, this comes with new Creation Club content which, at present, is unmanaged by MO2. To clean things up and make the new CC content easier to manage, complete the following.

1. Open MO2 and create a new mod called `Creation Club`
2. Right click on the mod and open it in explorer.
3. Open the `Stock Game` folder and go into the `Data` folder.
4. Select all the files that start with "cc" 
5. Move these files to the `Creation Club` folder
6. Once complete, your folders should look like the picture below.

![CC Cleanup](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/CCCleanUp.webp)

7. Close both folders and press F5 to refresh Mod Organizer. Your Mod Organizer should look like the picture below.

![CC MO2 Mod](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/MO2CCMod.webp)

## Tool Setup

### SKSE
SKSE is a required executable for a **lot** of Skyrim mods and as such is necessary to install. To set it up with stock game, instead of copying the exe and dll's to your base Skyrim install, simply copy them into your stock game folder. Install the scripts as a mod in MO2 and that is SKSE live.

### Engine Fixes
Engine Fixes is like SKSE in that it is very easy to setup. As before, simply copy the part 2 files into your stock game folder.

### Creation Kit
The Creation Kit is similar in terms of ease of use. You will need the main file from [Tweaked Creation Kit Ini](https://www.nexusmods.com/skyrimspecialedition/mods/19817) and I highly recommend using [SSE Creation Kit Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/71371) & [SSE Creation Kit FonixData Lip Sync Fix](https://www.nexusmods.com/skyrimspecialedition/mods/40971) alongside the Creation Kit. To setup the Creation Kit, complete the following steps.

1. Copy the Creation Kit.exe, CreationKit.ini & CreationKitPrefs.ini to the game root folder.
2. Extract and copy the Tweaked ini into the game root folder.
3. Copy the files from Creation Kit Fixes into the game root folder. If you receive a prompt to overwrite files, **do not overwrite**.
4. Install the Lip Sync Fix mod as normal in MO2.
5. Click on your gears icon in MO2, set up the creation kit tool. There is a line below arguments that says "Overwrite Steam AppID". Tick the box and type in the 1946180 value listed below.
6. Run the CK to test and make sure that it works.

### xEdit & xEdit based applications (DynDOLOD, xLodGen)
xEdit and applications based off it require the addition of some arguments to ensure that they can see where the data folder is. The most important argument to add is this one `-D:"C:\Path\To\Folder\Game Root\Data"` replacing the "Path\To\Folder" with the location of your game root folder. It should similar to the pictures below.

![xEdiit Path](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/xEditPath.webp)

![xLodGen Path](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/xLodGenPath.webp)

Once you have added those arguments and saved them, run xEdit to ensure that it can properly read the data folder. If you see a picture like this, xEdit is working.

![xEdit Test](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/xEditCheck.webp)

### Nemesis
For Nemesis to work with Stock Game, you need to adjust one of the lines in the Nemesis ini. To do this, complete the following steps.

1. Open the Nemesis mod and go to the `Ini Files` tab.
2. Select `Nemesis.Ini`
3. In the `SkyrimDataDirectory` line, change `auto` to the location of your data directory.
4. Save the ini file.

The picture below shows how the ini file should look.

![Nemesis Ini](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/NemesisIni.webp)

### Synthesis
Synthesis is relatively simple to configure for Stock Game. Like Nemesis, you just need to tell it where your game data folder is. To configure Synthesis, complete the following steps.

1. Run Synthesis and select the game you are using (in my case Skyrim Special Edition)
2. Click on the `Skyrim Special Edition` text in the top right corner.
3. In the `data folder location` field, add where your stock game is. It should look like the picture below.

![Synthesis Data folder location](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/SynthesisData.webp)

4. Synthesis will auto-save this data and remember it for future times you run it.

### zEdit
zEdit is again a relatively simple tool to configure for Stock Game. Like the previous two tools, you just need to tell it where your game data folder is. To configure zEdit, complete the following steps.

1. Run zEdit and select the tool you want. **Do not run any tool yet**
2. Press the settings cog to open the game profiles configuration.
3. Change the `Path` field to where your stock game is. It should look like the picture below.

![zEdit data location](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/zEditPath.webp)

4. Run the application to ensure that it picks up your data folder.

### Easy NPC

EasyNPC does not require any special setup other than simply making sure the checkbox marked `Use mod directory setting from mod manager when available` is checked.

![Easy NPC settings tick](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/EasyNPCPath.webp)

### PCA SE

PCA SE does not require any special setup other than telling it where the game is.

![PCA tell where it is](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Stock%20Game/PCAPath.webp)

## Conclusion
Whilst Stock Game might seem like a difficult thing to setup, in actuality it's not that tricky. By ensuring you use the correct paths and tell tools where things are, you can have totally seperated instances of modded games.
