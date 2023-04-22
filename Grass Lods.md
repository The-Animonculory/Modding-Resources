# Grass Lod Generation for Skyrim Special Edition

**WARNING!**

The following guide is **not** for beginners and must be followed to the letter. Any deviation will result in your grass and lods becoming broken and requiring regeneration.

## Preamble

Grass lods use a feature of DynDOLOD that allows for it to render grass billboard data within the visible uGRID to increase the visual fidelity and grass draw distance. Thanks to the work of DoubleYouC, this technology is availiable for usage on both 1.5.97 and 1.6.x versions of Skyrim Special Edition (SSE).

Prior to beginning this guide, you should have a freshly generated xLodGen output. Please follow the [main DynDOLOD guide](https://github.com/The-Animonculory/Modding-Resources/blob/main/DynDOLOD.md) up until the point it says to come back to this guide.

## Initial setup

Due to the .Net framework not being compatible with SSE builds newer than 1.5.97, there are different set up instructions depending on your game version.

### Set up for 1.5.97

As .Net Framework is natively compatible with this version, you do not need to do anything special.

#### Required files
- [.NET Script Framework](https://www.nexusmods.com/skyrimspecialedition/mods/21294)
- [No Grass In Objects](https://www.nexusmods.com/skyrimspecialedition/mods/42161)
- [DynDOLOD 3.00](https://www.nexusmods.com/skyrimspecialedition/mods/32382)  
- [DynDOLOD 3.00 Reources](https://www.nexusmods.com/skyrimspecialedition/mods/52897)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152)
- [Grass Cache Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/60891) <- **DO NOT ACTIVATE YET**

For the No Grass in Objects pre-cacher, place the plugin in the `plugins` folder of where your Mod Organizer 2 (MO2) is installed. Relaunch MO2 and it will appear in the tools area (shown as a spanner and screwdriver).

For the SSEEdit Script, install this into your xEdit `edit scripts` folder like so:
![List Worldspaces with Grass xEdit Script installed into Edit scripts folder of xEdit](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptPlacement.webp)

I **highly** recommend creating a seperate profile in MO2 which just contains your grass and landscape editing mods alongside Engine Fixes and Bug fixes. This will take a lot of time to work out, however it does result in a much quicker generation. Filters in xEdit can be used to help find plugins which edit landscape records (town overhauls, moving buildings, new lands mods etc).

### Set up for 1.6.xx

As of making this guide, .Net Framework is **NOT** compatible with this version of SSE and there are no plans for it to be updated. This means that you either need to do one of the following.

- Create a specailised instance of Mod Organizer 2 which is just for grass caching. This option is recommended as it enables you to have an isolated testing area to create the cgid files. Follow our [stock game](https://github.com/The-Animonculory/Modding-Resources/blob/main/Stock%20Game%20Setup.md) guide on getting this set up. You will then need to use then use the [Unofficial Skyrim Special Edition Downgrade Patcher](https://www.nexusmods.com/Core/Libs/Common/Widgets/DownloadPopUp?id=318087&game_id=1704) to create a **BEST OF BOTH WORLDS** downgraded version of Skyrim in that instance.

- If you modlist is a bit more complicated, then you will need to create a backup of your modlist and then use the [Unofficial Skyrim Special Edition Downgrade Patcher](https://www.nexusmods.com/Core/Libs/Common/Widgets/DownloadPopUp?id=318087&game_id=1704) to create a **BEST OF BOTH WORLDS** downgraded version of Skyrim. A fully downgraded version **WILL NOT** work with this. As before, I **highly** recommend creating a seperate profile in MO2 which just contains your grass and landscape editing mods alongside 1.5.97 compatible engine fixing plugins (Engine fixes, bug fixes, scrambled bugs etc...)

#### Required mods in 1.6.xx version
- [DynDOLOD 3.00](https://www.nexusmods.com/skyrimspecialedition/mods/32382)  
- [DynDOLOD 3.00 Reources](https://www.nexusmods.com/skyrimspecialedition/mods/52897)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152)
- [Grass Cache Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/60891) <- **DO NOT ACTIVATE YET**

For the SSEEdit Script, install this into your xEdit `edit scripts` folder like so:
![List Worldspaces with Grass xEdit Script installed into Edit scripts folder of xEdit](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptPlacement.webp)

#### Required files in downgraded *best of both worlds* version
- [.NET Script Framework](https://www.nexusmods.com/skyrimspecialedition/mods/21294)
- [No Grass In Objects](https://www.nexusmods.com/skyrimspecialedition/mods/42161)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- A UI mod such as [Dear Diary Dark Mode](https://www.nexusmods.com/skyrimspecialedition/mods/60837) <-**Mandatory as it fixes UI crashing bugs.**
- Your worldspace editing mods

For the No Grass in Objects pre-cacher, place the plugin in the `plugins` folder of where your Mod Organizer 2 (MO2) is installed. Relaunch MO2 and it will appear in the tools area (shown as a spanner and screwdriver).

## Grass Cache Generation

Once you have got your modlist configured for grass cache generation, it is now time to create the cache which will be used in the lod generation. The steps are the same regardless of which game version (V1.5.97 or the downgraded "Best of Both Worlds" version) you are using.

### Game INI file configuration

Before continuing, you need to configure the game file ini's to enable the grass cache to function properly. 

Set the following details in `Skyrim.ini`:

```
[Grass]
bAllowCreateGrass=1
bAllowLoadGrass=0
bEnableGrassFade=0
fGrassFadeRange=14128
```

Set the following details in `SkyrimPrefs.ini`:

```
[Grass]
fGrassMaxStartFadeDistance=6144
fGrassMinStartFadeDistance=0
fGrassStartFadeDistance=6144

[TerrainManager]
fBlockLevel0Distance=57344
fBlockLevel1Distance=147456
fBlockMaximumDistance=327680
fSplitDistanceMult=1.0000
```

### Pre Generation Script & NGIO ini file setup

Before generating your cache, you need to determine what worldspaces require generation of grass cache and which can be ignored. To do this, complete the following.

1. Open xEdit and load all of your plugins.
2. Right click anywhere and press `apply script`
3. Select the `List Worldspaces with Grass` script and run it.
4. Grab a coffee or pet your nearest fluffy animal as this can take a while.
5. Once completed, it will show a textbox similar to the picture below. 

![xEdit Worldspace with grass script output](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptOutput.webp)

6. Open your `No Grass in Objects` mod and open the `GrassControl.Config.txt` file.
7. In between the "" in the `OnlyPregenerateWorldSpaces =` section, copy and paste the data that is shown in the textbox. It is **vital** this data is in between the quotes, otherwise it will not be read. You can see an example of how it should look below.

![Grass Control config text file only pregenerate worldspace section](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/NGIOIni.webp)

8. Change the following lines in the file to read the following:

```
- UseGrassCache = True
- ExtendGrassDistance = True
- ExtendGrassCount = False
- EnsureMaxGrassTypesPerTextureSetting = 15    ;set to max count of grass types for the grass mod. This is for Cathedral Landscapes.
- OverwriteGrassDistance = 6144                ;Optional. This overrides skyrimprefs.ini.
- OverwriteGrassFadeRange = 14128              ;Optional. This overrides skyrim.ini.
- OverwriteMinGrassSize = 67                   ;Optional. This overrides skyrim.ini.
- GlobalGrassScale = 1.15                      ;Grass-size multiplier. A slight increase will make LOD grass a bit more apparent.
- OnlyLoadFromCache = True
- DynDOLODGrassMode = 1
```

### Bounds Data Recalculation

Any grass records that has no object bounds set will not generate anything during grass pre-caching. To ensure that grass has object bounds data, complete the following steps.

1. Open xEdit and filter your entire load order for grass records as shown in the image below.

![xEdit filtering for grass by record signature](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/FilterGrassRecs.webp)

2. Copy every record that shown into a new esp flagged esl plugin named "Grass bounds data". Ensure the plugin is similar to below, save it and close xEdit.

![New plugin showing grass information on left side of xedit](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassRecsPatch.webp)

3. Open the Creation kit and load your "Grass bounds data plugin"
4. Click on `Grass` in the object window and highlight all the grass.
5. Right click and select `Recalculate Bounds`

![creation kit window showing recalculate bounds highlighted](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/RecalcBoundsCK.webp)

6. Save the plugin and then exit the CK. 
7. Place the new plugin below all of your grass plugin and ensure it is active.

### Running Grass Cache

Grass cache will take a long time and may potential take a few hours depending upon how many worldspaces you have and how good your system is. To increase the speed, you can try setting your game resolution to be 800x600. This will free up more resources for the grass cache to use.

One you are satisfied that your modlist is ready for generation, click on the `spanner and screwdriver` icon and select, `PreCache Grass`. A pop-up will appear confirming that you wish to do this. Click `Yes` and grab a good book or fluffy animal to pet as this will take a while.

If your game crashes during generation, don't panic. It will continue until it is done. To check the progress of it, you can open the console window by pressing the "`" key.

Once it is completed, a pop-up will appear saying that grass generation has been completed. **If you do not have a mod set to catch files generated during gameplay, the grass will be in the `overwrite` mod at the bottom of your Mod Oragnizer's left pane (assuming you have the mods sorted by `Priority`).** You should see a folder called `grass` with a load of `.cgid` files inside. Create a new mod called `Grass cache` and copy the `grass` folder into there.

## Configuring the cached data

Owing to it's reliance on the .Net Framework, No Grass in Objects (NGIO) cannot be used on Skyrim versions newer than v1.5.97. Thankfully, [Grass Cache Fixes (CGF)](https://www.nexusmods.com/skyrimspecialedition/mods/60891) allows us to get around this and utilise the cached data in newer versions of the game. It also fixes issues on 1.5.97 with the NGIO mod.

### Converting the CGID files

Before activating the GCF mod, we need to convert our newly created cgid files into gid to ensure we replace the games pre-existing grass data. To do this, complete the following.

1. Backup your newly created `Grass Cache` data. For V1.6.x users, copy this data across to your main modlist and activate it.
2. Open up the GCF mod and copy across the ``1_rename_cgid_to_gid.bat` file into your `Grass Cache` mod, placing it in the `grass` folder amongst the `.cgid` files.
3. Double click the .bat file to convert the files to `.gid`.
4. Verify that the files have all been converted and then remove the bat file.

### Setting DynDOLOD into gid mode

As we have changed the grass data into `.gid`, we need to set DynDOLOD to read that data as the grass cache instead of `.cgid` files. To do this, complete the following.

1. Navigate to where your DynDOLOD is installed and open the `Edit Scripts` folder.
2. Open `DynDOLOD_SSE.ini` and change the following lines:

```
Expert=1
Level32=1 ;Only if using ACMOS
GrassGID=gid
```

## Creating the Grass Lod

### TexGen

Run TexGenx64 and Allow the tool to load your mods and then set your lod settings as you wish. Note the output path as to where TexGen is sending the output.

![TexGen settings](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/NewTexGenSettings.webp)

Ensure that `Grass` checkbox is checked and that the `Texture size Min` is set to `32`. Not setting this to 32 will result in no grass billboards being created.

Press `Start` and allow the tool to generate the textures. Once completed, it will ask if you want to `Exit` or `Zip&Exit`. Choose `Exit` as you can achieve much better compression via 7Zip. Copy the data from your output folder into a new mod and activate it.

### DynDOLOD & Occlusion

#### Generation

Ensure that your xLodGen and TexGen outputs are active. Run DynDOLODx64 and allow it to load all your mods. In the top left section where it lists worldspaces, right click and press select all. Load the relevant rules that you want, in this case we’ll load medium rules. Ensure that the `Grass Lod` checkbox is checked and it is set to `Mode 1` and then pick your preferred lod settings. Once you have set them, it should look similar to this.

![DynDOLOD Settings for grass lod generation](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GLDDLDNew.webp)

Another note on settings. Billboard brightness is one that you adjust if you find that your lods are too bright in game. I have this set lower due to some of the tree mods I use. Ultra trees generates 3D tree lod and can be performance-intensive depending on the tree mods you use. However, Ultra Tree lods do get unloaded wheras the hybrid lods do not. I personally recommend using 3D tree lod as the visual quality difference is substantial for a minor perforamnce defecit. Anything above `1024` on tile size billboard is not recommended as you are beyond the threshold of visual quality to performance. And finally, the rules govern how DynDOLOD will generate things and at what quality. 

  -  *Note: Certain tree mods require specialised tree rules in order for them to render properly in the worldspace. Known mods that require them include: Myrkvior, Trees Addon SE and Skyrim Flora Overhaul. It is likely there are more tree mods that require special rules.* 

DynDOLOD 3.0 now includes Occlusion as part of it's toolset so we no longer need to generate Occlusion via xLodGen. I recommend the settings shown in picture above for generation as these are very similar to the original one's used in xLodGen occlusion.

Once you have configured the settings how you wish, click `OK` and DynDOLOD will begin its generation. This can take a very long time depending on how many worldspaces you have, as well as your system specifications. Once it is completed, a pop-up will appear. As with TexGen, you have the option to either `Save&Exit` or `Save&Zip&Exit`. Choose `Save&Exit`

Copy the data from your output folder into a new mod and activate it. On the right pane, `DynDOLOD.esm` should be moved to be the last ESM after your worldspace mods. In my case, that is Lux so I place it after `Lux - Master Plugin.esm`. `DynDOLOD.esp` should be the second last and `Occlusion.esp` shoud be the last plugin in your load order.

### Setting the game to load the grass cache

Once you have finished generating DynDOLOD and activated it, we are now ready to apply the fixes contained in the CGF mod. To apply the changes, complete the following.

1. Open the CGF mod and open the `Grass Cache Fixes.ini` file.
2. Remove the `;` before the lines titled `bAllowCreateGrass`, `bAllowLoadGrass`, `bEnableGrassFade`, and `fGrassFadeRange`.
3. Open up your `SkyrimPrefs.ini` file and set `fGrassStartFadeDistance` to `6144` and `fGrassFadeRange` to `14128`.
4. Save and close the file.

You are now ready to test in game and see how it looks. **Note**: Depending on which grass mod you use depends on how much FPS you will use. I use [Fantastic Grasses](https://www.nexusmods.com/skyrim/mods/105903) which I have custom patched for bounds and complex grass and encounter minimal FPS loss. Your mileage, as always, may vary.
