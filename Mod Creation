# Mod Creation

## Table of Contents



## Skyrim Anniversary Edition Modding (+ Scripting)
- This guide is for those that want a clean modding and scripting environment. 

#### Pre-Installation
- Get VC++ here: https://aka.ms/vs/16/release/vc_redist.x64.exe

### Install Skyrim
- Install Skyrim (NOT in Program Files, ex: X: Games) and set it so it [only updates when you launch it](https://help.steampowered.com/en/faqs/view/71AB-698D-57EB-178C#disable).

- Run once. Go ahead and let the Creation Club content download. 
- You don't have to start a new game. Press Quit.

### Install Creation Kit + Fixes
- Download `Skyrim Special Edition: Creation Kit` on Steam. 
- Open Creation Kit. Say NO to Scripts unpacking. Exit Creation Kit. 
- Go to your Skyrim directory/Data: `X:\Games\steamapps\common\Skyrim Special Edition\Data`. Copy that `Scripts.zip` file. 
- Go to a folder like `My Documents`, and create a new folder like `SkyrimFresh`. Paste and unpack `Scripts.zip` there. 
- Delete `Scripts.zip` in that `SkyrimFresh` folder.
- You'll now see `DialogueViews` and `Source`.
- Rename ``Source`` to ``Scripts``. Open that folder. Rename ``Scripts`` to ``Source``. So it has to be `Scripts > Source`. NOT Source > Scripts.
- Go back to where you see `DialogueViews` and `Scripts`.
- Add both `DialogueViews` and `Scripts` into a .zip file. You can name it ``CKScripts.zip`` (or 7z). You can delete both the `DialogueViews` and `Scripts` folders after successfully placing them into a .zip file.
- Download `SSE CreationKitFixes` and `FaceFXwrapper` https://www.nexusmods.com/skyrimspecialedition/mods/20061 and add them to your `SkyrimFresh` folder.
- Download `SSE Creation Kit Fixes Update` https://www.nexusmods.com/skyrimspecialedition/mods/71371 and add it to your `SkyrimFresh` folder.
- Download `Tweaked Creation Kit ini` https://www.nexusmods.com/skyrimspecialedition/mods/19817 and add it to your `SkyrimFresh` folder. 
 - Note: Only get `CK Custom ini`. 
- Download `FonixData.cdf` https://www.nexusmods.com/newvegas/mods/61248/ and add it to your `SkyrimFresh` folder. 

### Download SKSE
- Get the one for Anniversary Edition https://skse.silverlock.org/ and add it to your `SkyrimFresh` folder. Extract it in there. 
- Open the contents of that new skse folder until you see `src`, `data`, etc. Inside the `Data` folder, you will find a `Scripts` folder with more contents. Right-click `Scripts` and zip it. Name it ``SKSEScripts.zip`` and move that to your ``SkyrimFresh`` folder.

### Install MO2
- Grab the latest archive release here: https://github.com/ModOrganizer2/modorganizer/releases
- Paste all the contents somewhere like X:/MO2. 

### Stock Game
- Create a folder called `Stock Game` in your X:/MO2 folder. 
- Go to your Skyrim directory, where `SkyrimSE.exe` is.
- Copy everything in there. Paste them inside the `Stock Game` folder you made in the MO2 directory.

### Continue MO2 Installation
- Open up `ModOrganizer.exe`. Press the `Create new instance` button. `Create a portable instance`.
- When asked to select what game to manage, press `Browse...`.
- Select your new `Stock Game` folder.
- Press `Next`, finish that install.
- Go to `Tools > Settings > Theme` in MO2.
- Change theme to 1809 Dark Mode. Because *eyes*. Press OK.

### SkyrimFresh Folder
- Drag `CKScripts.zip` and `SKSEScripts.zip` into the Downloads tab in MO2, and install both. Place these after the DLCs and Creation Club content, and before any mods you make. `CKScripts` go before `SKSEScripts`.
- Open the skse folder. Copy the skse dll, skse loader.exe, skse steam loader.dll into the `Stock Game` folder.
- Open the `CK64Fixes Release` folder. Copy all contents and paste into the `Stock Game` folder.
- Open the `SSE Creation Kit Fixes Update` folder. Copy all contents and paste into the `Stock Game` folder. Replace the files.
- Create a new folder in `Stock Game/Data` named `Sound`. Inside it, create a new folder named `Voice`. Open the `FonixData` folder in `SkyrimFresh` and drag `Processing` into `Voice`.
- Open `FaceFXWrapper`. Drag `Tools` into `Stock Game`.
- Copy `CreationKitCustom.ini` and paste into `Stock Game`.

### Creation Club Content
- Create an empty mod and call it `Creation Club Content`.
- <img src="https://imgur.com/NbNG66i.png"></img>
- Enable it and put it above `CKScripts` and `SKSEScripts`.
- Right-click that new mod you made, and open it in explorer.
- Go into the `Data` folder in `Stock Game`.
- Move (do not copy) all of the CC content into the `Creation Club Content` folder you made.
- ![image](https://user-images.githubusercontent.com/92814468/179336537-54735f55-dab7-48a4-b98e-7fb109d51a63.png)
- Refresh MO2, and voila.
- ![image](https://user-images.githubusercontent.com/92814468/179336621-40eedb70-6671-4b3a-abef-241976c11e52.png)


#### IF going to use Visual Studio Code, skip NotePad++. 
### NotePad++
- Get v7.4.2 of Notepad++ http://download.notepad-plus-plus.org/repository/7.x/7.4.2/ Disable auto-update. (Select Don't use AppData)
- Install Papyrus++ https://www.nexusmods.com/skyrim/mods/64895/?tab=files
- Open Notepad++
- Copypaste Autocomplete  https://gist.githubusercontent.com/st4rdog/3470de541941d3e9b5b1/raw/02be3fa5e622535243b02e34cacdd7e79f2421e5/papyrus.xml into a new notepad file. Save as 'Papyrus.xml'  into Notepad++\plugins\APIs folder. 
- ScriptCompile.bat, edit this in Skyrim directory > Papyrus Compiler. Save.
``cd %2
"%~dp0PapyrusCompiler" %1 -f="TESV_Papyrus_Flags.flg" -i="%~dp0..\Data\Scripts\Source" -o="%~dp0..\Data\Scripts"
pause``
- Press F5 (Run) in Notepad++. Paste this, but modify to your liking. WITH QUOTES. Press SAVE (shortcut can be CTRL F5), not Run. And then Cancel.
``"D:\Games\steamapps\common\Skyrim Special Edition\Papyrus Compiler\ScriptCompile.bat" "$(FILE_NAME)" "$(CURRENT_DIRECTORY)"``
- It's important that you add your mod's Source folder into Plugins > Papyrus++ > Settings > Import directories. 

### Visual Studio Code (if not using NotePad++)
- Download here: https://code.visualstudio.com/
- You can choose a different directory to install it in.
- Setup: Check all boxes under *Other:* in *Select Additional Tasks*. 
- Open VS Code. Go to File > Preferences > Extensions (CTRL+SHIFT+X).
- Look up `Papyrus` by Joel Day. Install.
- Look up `Workspace Explorer` by Tom Saunders. Install.
- Now, go to File > Preferences > Settings (CTRL+,).
- Look up `papyrus skyrim`. Scroll down to Special Edition's *Mod Directory Path*. Based on this guide, it's `D:\MO2\mods`. Add that to the field.
- You will paste that line into another field. Now, look up `explorer` and scroll down to *Workspace Storage Directory*. Paste there. Saving is automatic.
- Close VS Code. We have to replace template files.
- This may be different for you, but go to ``C:\Users\Anna\.vscode\extensions``. 
- Install the latest Pyro release. https://github.com/fireundubh/pyro/releases Not the Source code.
- Back to that .vscode\extensions folder, open *joelday.papyrus-lang-vscode-2.23.1* Open the *pyro* folder. Delete everything in there. Open the latest pyro release you just downloaded. Copy everything and paste them into your pyro folder.
- Now, go into ``C:\Users\Anna\.vscode\extensions\joelday.papyrus-lang-vscode-2.23.1\resources\sse``.
- Open skyrimse.ppj with VS Code. 
- If you see a message in a blue bar that mentions Restricted Mode, click *Manage*. Scroll down to *Trusted Folders & Workspaces*. Click *Add Folder*. You can just add the drive where all of your Skyrim + modding files are saved. If they're all in D: Drive, for example, you select that. And then press *Trust*.
- TIP: If your Visual Studio Code's text in the scripts don't have any color, that means your configurations mentioned here aren't set up correctly.
- Back to skyrimse.ppj: Delete all the text in that file.
- Copy the wonderful mrowrpurr's ppj file: https://gist.githubusercontent.com/mrowrpurr/e164735e14ee6d07daf4f4217caf3714/raw/40a0684d55e139d4c1437b1a7e2ac0997bf36c0b/skyrimse.ppj
- Paste that into your skyrimse.ppj, you will need to change the directory under: `` <!-- <Import>@ModsFolder\SKSE64\Scripts\Source</Import> -->`` and SAVE. Mine says:
 ``<Import>D:\MO2\mods\CKScripts\Scripts\Source</Import>
 <Import>D:\MO2\mods\SKSE Scripts\Scripts\Source</Import>``
- Now, open tasks.json in that same folder.
- Delete all text again.
- Copy mrowrpurr's tasks.json: https://gist.githubusercontent.com/mrowrpurr/e164735e14ee6d07daf4f4217caf3714/raw/40a0684d55e139d4c1437b1a7e2ac0997bf36c0b/tasks.json
- Paste that text into your tasks.json, change the gamepath directory, and SAVE.
- With VS Code open, click on what looks like a scroll on your VS Code toolbar: 
![Papyrus](https://cdn.discordapp.com/attachments/803257955029352518/931558126891720815/14598224c7cb9384de2fc3c9b1402908.png).
- Click on the three dots here: ![Papyrus](https://cdn.discordapp.com/attachments/803257955029352518/931558480328949760/62279b5a23636b5787500448e713ad1b.png).
- Select *Generate Skyrim Special Edition Project Files*.
- Go to the main directory of the mod you are working on. Ex: Mod123's folder, where you typically see *meshes, scripts, textures, seq* in mods. A workspace has now been created for you.
- To change which workspace you are in, press `CTRL+SHIFT+E` and if you look below, there's a *WORKSPACES* tab. You can move this tab to the top.
#### Visual Studio Code Notes
- How to compile: Run > Build Task.
- You WILL need to return to your mod's skyrimse.ppj to change some values. Thanks to mrowrpurr, they're pretty clear:" CHANGE THE MOD NAME HERE".
- Set up your debugging: when you have one of your mod's scripts open, click on ![Papyrus](https://cdn.discordapp.com/attachments/803257955029352518/931574029217828884/6b41099efb62089166a1ca330feea893.png). And then the play button ![Papyrus](https://cdn.discordapp.com/attachments/803257955029352518/931574329651654757/5abfe5c1dd4544dad433ba9ce44157cb.png). Select Install SKSE Plugin. Go to MO2, refresh, and enable Papyrus Debug Extension.
- When you test things in-game, it's SKSE you need to choose. 
- If you are in-game and want to see debug logs, you will need to press that play button. An indication of a successful connection looks like this: ![Papyrus](https://cdn.discordapp.com/attachments/803257955029352518/931575185218367588/38573e2b0313caf79bceae9a624252cd.png). If you don't see your debug console, hit View > Debug Console.


### Needs to be updated, ignore for now
- Go to Tools > INI Editor. In skyrim.ini, look for *papyrus*. Change the settings to reflect the following:
 ``bEnableLogging = 1, bEnableTrace = 1, bLoadDebugInformation = 1`` and hit Save.
- In MO2's Executables settings, for Creation Kit, you will need to make sure that your mod is selected in *Create files in mod instead of overwrite.*
SKSE

