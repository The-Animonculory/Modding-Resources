# Grass Lod Generation for Skyrim Special Edition

**WARNING!**

The following guide is **not** for beginners and must be followed to the letter. Any deviation will result in your grass and lods becoming broken and requiring regeneration. 

## Preamble

Grass lods are a new technology that allow for you to use a generated cache of grass data to increase visual fidelity and grass draw distance. Through the use of DynDOLOD and Grass cache fixes, this technology can now be used on both V1.5.97 and V1.6.xx of Skyrim Special Edition (SSE).

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
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152) -> Installed into your xEdit `edit scripts` folder like so
![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptPlacement.webp)
- [Grass Cache Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/60891) <- **DO NOT ACTIVATE YET**

For the No Grass in Objects pre-cacher, place the plugin in the `plugins` folder of where your Mod Organizer 2 (MO2) is installed. Relaunch MO2 and it will appear in the tools area (Shown as a spanner and screwdriver).

I **highly** recommend creating a seperate profile in MO2 which just contains your grass and landscape editing mods alongside Engine Fixes and Bug fixes. This will take a lot of time to work out, however it does result in a much quicker generation. Filters in xEdit can be used to help find plugins which edit landscape records (town overhauls, moving buildings, new lands mods etc).

### Set up for 1.6.xx

As of making this guide, .Net Framework is **NOT** compatible with this version of SSE. This means that you either need to do one of the following.

- If you are running a lite modlist with very few worldspace changing mods, I have created a [Wabbajack installer](https://github.com/The-Animonculory/Modding-Resources/blob/main/Grass%20Cache%20Gen.wabbajack?raw=true) which is set up ready for generation. This uses the Stock game feature to preserve the integrity of your base game installation. You only need to add the mods you are using to it and resolve any major conlficts that are present. 

- If you modlist is a bit more complicated, then you will need to create a backup of your modlist and then use the [Unoffical Skyrim Downloader](https://www.nexusmods.com/skyrimspecialedition/mods/61756) to create a **BEST OF BOTH WORLDS** downgraded version of Skyrim. A fully downgraded version **WILL NOT** work with this. Please use the previous set up. I **STRONGLY** recommend using the Stock Game format for this to preserve the integrity of your base game installation. You can read more about how to set-up [in this guide](https://github.com/The-Animonculory/Modding-Resources/blob/main/Stock%20Game%20Setup.md).

As before, I **highly** recommend creating a seperate profile in MO2 which just contains your grass and landscape editing mods alongside Engine Fixes and Bug fixes.

#### Required mods in 1.6.xx version
- [DynDOLOD 3.00](https://www.nexusmods.com/skyrimspecialedition/mods/32382)  
- [DynDOLOD 3.00 Reources](https://www.nexusmods.com/skyrimspecialedition/mods/52897)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152) -> Installed into your xEdit `edit scripts` folder like so
![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptPlacement.webp)

- [Grass Cache Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/60891) <- **DO NOT ACTIVATE YET**

#### Required files in downgraded *best of both worlds* version
- [.NET Script Framework](https://www.nexusmods.com/skyrimspecialedition/mods/21294)
- [No Grass In Objects](https://www.nexusmods.com/skyrimspecialedition/mods/42161)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- A UI mod such as [Dear Diary Dark Mode](https://www.nexusmods.com/skyrimspecialedition/mods/60837) <-**Mandatory as it fixes UI crashing bugs.**
- Your worldspace editing mods

## Grass Cache Generation

Once you have got your modlist configured for grass cache generation, it is now time to create the cache which will be used in the lod generation. The steps are the same regardless of which game version (V1.5.97 or the downgraded "Best of Both Worlds" version) you are using.

### Pre Generation Script & INI file setup

Before generating your cache, you need to determine what worldspaces require generation of grass cache and which can be ignored. To do this, complete the following.

1. Open xEdit and load all of your plugins.
2. Right click anywhere and press `apply script`
3. Select the `List Worldspaces with Grass` script and run it.
4. Grab a coffee or pet your nearest fluffy animal as this can take a while.
5. Once completed, it will show a textbox similar to the picture below. 

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptOutput.webp)

6. Open your `No Grass in Objects` mod and open the `GrassControl.Config.txt` file.
7. In between the "" in the `OnlyPregenerateWorldSpaces =` section, copy and paste the data that is shown in the textbox. It is **vital** this data is in between the quotes, otherwise it will not be read. You can see an example of how it should look below.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/NGIOIni.webp)

8. Change the following lines in the file to read the following:

- `UseGrassCache = True`  
- `OverwriteGrassDistance = 12000`  
- `OverwriteGrassFadeRange = 8000`  
`OnlyLoadFromCache = True`  
- `DynDOLODGrassMode = 1`  

    *Note*: To improve performance, you can set the `OverWriteGrassDistance` and `OverwriteGrassFadeRange` to be lower. For the former, a setting of 8000 is a bit more than vanilla and may improve your performance. If you just wish to cache the grass but not for DynDOLDOD, change the `DynDOLODGrassMode` back to `=0`. `SuperDenseMode` is another section that you can alter if you wish to tone down the grass amount. I leave this set at `7` as it gives a good balance of performance to visuals; however, setting this to `6` can help improve performance.

### Bounds Data Recalculation

Any grass records that has no object bounds set will not generate anything during grass pre-caching. To ensure that grass has object bounds data, the following should be completed.

Firstly, open xEdit and filter your entire load order for grass records as shown in the picture below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/FilterGrassRecs.webp)

Once the filter has finished applying, copy every record that is shown into a new esp flagged esl plugin. Name it something like "Grass Bounds Data" and save it. Your plugin should only contain similar to what is below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassRecsPatch.webp)

Close xEdit and then open up the Creation Kit. Load your newly created grass plugin, click on `Grass` in the object window and highlight all the grass, right click and then select `Recalculate Bounds`.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/RecalcBoundsCK.webp)

Save the plugin and then exit the CK. Place the new plugin below all of your grass plugin and ensure it is active.

### Running Grass Cache

Grass cache will take a long time and may potential take a few hours depending upon how many worldspaces you have and how good your system is. To increase the speed, you can try setting your game resolution to be 800x600. This will free up more resources for the grass cache to use.

One you are satisfied that your modlist is ready for generation, click on the `spanner and screwdriver` icon and select, `PreCache Grass`. A pop-up will appear confirming that you wish to do this. Click `Yes` and grab a good book or fluffy animal to pet as this will take a while.

If your game crashes during generation, don't panic. It will continue until it is done. To check the progress of it, you can open the console window by pressing the "`" key.

Once it is completed, a pop-up will appear saying that grass generation has been completed. **If you do not have a mod set to catch files generated during gameplay, the grass will be in the `overwrite` mod at the bottom of your Mod Oragnizer's left pane (assuming you have the mods sorted by `Priority`).** You should see a folder called `grass` with a load of `.cgid` files inside. Create a new mod called `Grass cache` and copy the `grass` folder into there.

### Fixing grass data w/ Grass Cache Fixes

Now at this point, in the past, we would go on to create our grass lods and use No Grass in Objects (NGIO) to control that. However, we now have a better solution in the form of [Grass Cache Fixes](https://www.nexusmods.com/skyrimspecialedition/mods/60891) (GCF). This mod allows us to use grass lods on both V1.5.97 and V1.6.xx without needing the .Net Framework mod.

NGIO is a great mod, however it has some issues in that it uses a form of raycasting which, on computers with less than 10GB of vram, can cause stuttering and large performance drops. Where GCF fixes this is that it replaces the base game grass data with the newly generated cached grass and doesn't allow the game to create any new grass.

### Setting up GCF

To get GCF working correctly with our new grass cache, complete the following.

1. V1.6.xx users, copy your Grass Cache mod into your non "Best of Both Worlds" version of your modlist and activate it.
2. Make a copy of your grass cache and place it somewhere safe.
3. Create a new mod called `Grass Data` and copy your grass cache into there. Make sure that the data matches in both this mod and your `Grass Cache` mod.
4. Activate GCF in your MO2 left pane.
5. Open the CGF mod and copy the `1_rename_cgid_to_gid.bat` file into your `Grass Data` mod, placing it in the `grass` folder amongst the `.cgid` files. 
6. Double click to run the bat file. Once it has finished, verify that all the files are `.gid` and not `.cgid`.

## Grass Lod creation

### TexGen

Run TexGenx64 and Allow the tool to load your mods and then set your lod settings as you wish. Note the output path as to where TexGen is sending the output.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GLDTXGN.webp)

Ensure that `Grass` checkbox is checked and that the `Texture size Min` is set to `32`. Not setting this to 32 will result in no grass billboards being created.

Press `Start` and allow the tool to generate the textures. Once done, the tool will open a pop-up. Press `Exit` or `Zip&Exit` if you wish to have the output zipped up for easier addition to a mod-manager or redistribution. In this case, we're choosing `Zip&Exit` as that allows us to add the output as a new mod in MO2 easier. Add the output as a new mod in Mod Organizer 2, and then activate it.

### DynDOLOD & Occlusion

#### Enabling advanced mode and Lod32

In order to have DynDOLOD start in advanced mode each time and enable the Lod32 setting **required by A Clear Map of Skyrim**, you need to edit a line in the `DynDOLOD_SSE.ini` file. Navigate to where your DynDOLOD is located, open up the `Edit Scripts` folder, and then the DynDOLOD folder. Open the `DynDOLOD_SSE.ini` file and change the following lines:  

`Expert=1`
`Level32=1`

Save the .ini file and reopen MO2.

#### Generation

Ensure that your xLodGen and TexGen outputs are active. Run DynDOLODx64 and allow it to load all your mods. In the top left section where it lists worldspaces, right click and press select all. Load the relevant rules that you want, in this case we’ll load medium rules. Ensure that the `Grass Lod` checkbox is checked and it is set to `Mode 1` and then pick your preferred lod settings. Once you have set them, it should look similar to this.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GLDDLD.webp)

Another note on settings. Billboard brightness is one that you adjust if you find that your lods are too bright in game. I have this set lower due to some of the tree mods I use. Ultra trees generates 3D tree lod and can be performance-intensive depending on the tree mods you use. However, Ultra Tree lods do get unloaded wheras the hybrid lods do not. I personally recommend using 3D tree lod as the visual quality difference is substantial for a minor perforamnce defecit. Anything above `1024` on tile size billboard is not recommended as you are beyond the threshold of visual quality to performance. And finally, the rules govern how DynDOLOD will generate things and at what quality. 

  -  *Note: Certain tree mods require specialised tree rules in order for them to render properly in the worldspace. Known mods that require them include: Myrkvior, Trees Addon SE and Skyrim Flora Overhaul. It is likely there are more tree mods that require special rules.* 

DynDOLOD 3.0 now includes Occlusion as part of it's toolset so we no longer need to generate Occlusion via xLodGen. I recommend the settings shown in picture above for generation as these are very similar to the original one's used in xLodGen occlusion.

Once you have configured the settings how you wish, click `OK` and DynDOLOD will begin its generation. This can take a very long time depending on how many worldspaces you have, as well as your system specifications. Once it is completed, a pop-up will appear. As with TexGen, you have the option to either `Save&Exit` or `Save&Zip&Exit`. Again, the choice is yours however in this guide we'll choose to zip it up as well.

Add the zipped output file as a new mod in MO2, name it `DynDOLOD Output` and activate the mod. On the right pane, `DynDOLOD.esm` should be moved to be the last ESM after your worldspace mods. In my case, that is Wyrmstooth so I place it after `Wyrmstooth.esm`. `DynDOLOD.esp` should be the second last and `Occlusion.esp` shoud be the last plugin in your load order.

### Setting the game to load the grass cache

Once you have finished generating DynDOLOD and activated it, we are now ready to apply the fixes contained in the CGF mod. To apply the changes, complete the following.

1. Open the CGF mod and open the `Grass Cache Fixes.ini` file.
2. Remove the `;` before the lines titled `bAllowCreateGrass`, `bAllowLoadGrass`, `bEnableGrassFade`, and `fGrassFadeRange`.
3. Open up your `SkyrimPrefs.ini` file and set `fGrassStartFadeDistance` to `6144` and `fGrassFadeRange` to `14128`.
4. Save and close the file.

You are now ready to test in game and see how it looks. **Note**: Depending on which grass mod you use depends on how much FPS you will use. I use [Realistic Grass Field](https://www.nexusmods.com/skyrimspecialedition/mods/36588) alongside the [ENB Complex Grass](https://www.nexusmods.com/skyrimspecialedition/mods/67304) patch for it and encounter minimal to no FPS loss. Your mileage, as always, may vary.
