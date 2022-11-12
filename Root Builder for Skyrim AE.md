# Setting up Root Builder for Skyrim AE

## Intro

You might have seen that you can now get Skyrim AE from more places than just the Steam Store. It's now available via GOG and Epic Games Store, however this does present some challenges. If you want your list to support both Steam and EGS/GOG (Note: I only cover GOG in this guide, EGS is similar but may have some differences), you can no longer use Stock Game as that effectively 'store-locks' your list. Instead, you need to use a tool called "Root Builder" which is already being used in the Cyberpunk lists on Wabbajack.

## What is Root Builder?

Root Builder is a plugin extension for Mod Organizer 2 made by Kezyma that allows you to manage data folder files from within Mod-Organizer. The [official guide](https://kezyma.github.io/?p=rootbuilder) goes over a lot of what it does in more detail than we will here. Put simply, you can now do the following within Mod-Organizer:

- Manage SKSE
- Install mods that previously required to go into the game data folder (Engine Fixes, ENB Binaries etc)
- Manage different versions of the game.

## Using Root Builder

### How do I set it up?

Root Builder is very simple to set up and can be installed and working in a matter of minutes.

1. Download [Root Builder](https://www.nexusmods.com/skyrimspecialedition/mods/31720) 

2. Extract the files into `x:\Path\To\MO2\plugins`.

3. Launch Mod Organizer 2 and click on the `spanner and screwdriver`.

4. Select `Root Builder` and then click on `Root Builder`

![Selecting Root Builder in mo2](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Root%20Builder/RootbuilderMo2Access.webp)

5. You will see a screen similar to the following below.

![Root Builder main screen](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Root%20Builder/RootbuilderConfig.webp)

6. Ensure that `Installer` is ticked (We need this to install mods into Root properly)

7. Close Root Builder.

### Installing mods with Root Builder

Most mods will install just fine with root builder, however it is important to verify that files are moving into root properly. Let's take an ENB for example. 

![ENB shot](https://raw.githubusercontent.com/The-Animonculory/ADT/main/.github/ENBRootBuild.webp)

As you can see in the picture above, this is how it should look. The files which would normally be placed in the game data folder are located in the `Root` folder. 

Now, let's look at SKSE. As with ENB, you would normally install this to your game data folder. However, in this case it's placed in the Root folder as well. To get the game to launch with SKSE, you need to add it as an executable, as shown in the picture below.

![Adding SKSE as an exe](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Root%20Builder/SkseAddEXERoot.webp)

### Creation Club configuration

If for some reason, you do not wish to use all the AE creation club content and only wish to have a certain amount, you will need to create a custom `Skyrim.ccc` file. To configure this, complete the following.

1. Navigate to where your Skyrim is installed (in my case it's `C:\Games\GOG Galaxy\Games\Skyrim Anniversary Edition`)

2. Copy the Skyrim.ccc file and paste it somewhere temporary.

3. Open the file with your preferred editor, in my case VS Code.

4. Remove the references to the Creation Club ESM/ESL files you do not want used.

5. Save the file.

6. Create a new mod in Mod Organizer 2 and call it "CC content config"

7. Create a folder within it called `Root`

8. Paste your newly edited `Skyrim.ccc` file in there.

9. You have now configured which CC content the game will load.

### Tool Setup

#### xEdit based tools [GOG only]

Due to GOG not being natively supported with the tools yet, you have to add some arguments to get it to recognise and load the data properly. The following arguments are needed in order to get xEdit based tools to load plugins properly: 
- `-D:"X:\GOG Galaxy\Games\Skyrim Anniversary Edition\Data"` 
- `-I:"X:\Users\User\Documents\My Games\Skyrim Special Edition GOG\Skyrim.ini"` 
- `-P:"X:Path\To\MO2\profiles\Profile Name [GOG]\Plugins.txt"`

## Compiling with Root Builder [For Wabbajack List Authors]

There are certain compiler settings you need to pick in order for your installer not to get massive. Make sure that you are flagging the following as shown in the picture below.

![WJ flagging compilation settings](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/Root%20Builder/WJ3CompSets.webp)

This will allow for your modlist to support both GOG and Steam versions of Skyrim AE and also have a smaller footprint due to no stock game.
