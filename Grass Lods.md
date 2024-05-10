# Grass Lod Generation for SSE/SAE/SVR

**WARNING!**

The following guide is **not** for beginners and must be followed to the letter. Any deviation will result in your grass and lods becoming broken and requiring regeneration. I do not go fully into detail on certain areas. If you wish for a more in depth tutorial please, follow the [STEP tutorial](https://stepmodifications.org/wiki/SkyrimSE:Grass_LOD_Guide) of which parts of this guide are adapted from.

## Preamble

Grass lods use a feature of DynDOLOD that allows for it to render grass billboard data within the visible uGRID to increase the visual fidelity and grass draw distance. Thanks to the work of many talented mod authors, this technology is availiable for usage on both 1.5.97 and 1.6.x versions of Skyrim Special Edition (SSE).

Prior to beginning this guide, you should have a freshly generated xLodGen output. Please follow the [main DynDOLOD guide](https://github.com/The-Animonculory/Modding-Resources/blob/main/DynDOLOD.md) up until the point it says to come back to this guide.

## Initial Setup

Thanks to the hard work of various coders within the community, the setup for the generation and usage of grass lods is now the same across both versions of Skyrim.

### Required files
- [No Grass In Objects](https://www.nexusmods.com/skyrimspecialedition/mods/42161)
- [DynDOLOD 3.00](https://www.nexusmods.com/skyrimspecialedition/mods/32382)  
- [DynDOLOD 3.00 Reources](https://www.nexusmods.com/skyrimspecialedition/mods/52897)
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152)
- [Grass Cache Helper NG](https://www.nexusmods.com/skyrimspecialedition/mods/101095) <- **Optional but recommended; DO NOT ACTIVATE YET**

For the No Grass in Objects pre-cacher, place the plugin in the `plugins` folder of where your Mod Organizer 2 (MO2) is installed. Relaunch MO2 and it will appear in the tools area (shown as a spanner and screwdriver).

For the SSEEdit Script, install this into your xEdit `edit scripts` folder like so:
![List Worldspaces with Grass xEdit Script installed into Edit scripts folder of xEdit](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassScriptPlacement.webp)

I **highly** recommend creating a seperate profile in MO2 which just contains your grass and landscape editing mods alongside Engine Fixes and Bug fixes. This will take a lot of time to work out, however it does result in a much quicker generation. Filters in xEdit can be used to help find plugins which edit landscape records (town overhauls, moving buildings, new lands mods etc).

## Grass Cache Generation

Once you have got your modlist configured for grass cache generation, it is now time to create the cache which will be used in the lod generation.

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
- OverwriteMinGrassSize = 67                   ;Optional. This overrides skyrim.ini.
- GlobalGrassScale = 1.15                      ;Grass-size multiplier. A slight increase will make LOD grass a bit more apparent.
- OnlyLoadFromCache = True
```

***

### Bounds Data Recalculation

Any grass records that has no object bounds set will not generate anything during grass pre-caching. To ensure that grass has object bounds data, complete the following steps.

1. Open xEdit and filter your entire load order for grass records as shown in the image below.

![xEdit filtering for grass by record signature](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/FilterGrassRecs.webp)

2. Copy every record that shown into a new esp flagged esl plugin named "Grass bounds data". Ensure the plugin is similar to below, save it and close xEdit.

![New plugin showing grass information on left side of xedit](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GrassRecsPatch.webp)

3. Open the Creation kit and load your "Grass bounds data plugin"
4. Click on `Grass` in the object window and highlight all the grass.
5. Right click and select `Recalculate Bounds`.

![creation kit window showing recalculate bounds highlighted](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/RecalcBoundsCK.webp)

6. Save the plugin and then exit the CK. 
7. Place the new plugin below all of your grass plugin and ensure it is active.

### Running Grass Cache

Grass cache will take a long time and may potentially take a few hours depending upon how many worldspaces you have and how good your system is. To increase the speed, you can try setting your game resolution to be 800x600. This will free up more resources for the grass cache to use.

One you are satisfied that your modlist is ready for generation, click on the `spanner and screwdriver` icon and select, `PreCache Grass`. A pop-up will appear confirming that you wish to do this. Click `Yes` and grab a good book or fluffy animal to pet as this will take a while.

If your game crashes during generation, don't panic. It will continue until it is done. To check the progress of it, you can open the console window by pressing the "`" key.

Once it is completed, a pop-up will appear saying that grass generation has been completed. **If you do not have a mod set to catch files generated during gameplay, the grass will be in the `overwrite` mod at the bottom of your Mod Oragnizer's left pane (assuming you have the mods sorted by `Priority`).** You should see a folder called `grass` with a load of `.cgid` files inside. Create a new mod called `Grass cache` and copy the `grass` folder into there.

## Generating the Grass Lods

### TexGen

Run TexGenx64 and allow the tool to load your mods and then set your lod settings as you wish. Note the output path as to where TexGen is sending the output.

![TexGen settings](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/NewTexGenSettings.webp)

Ensure that either the `Grass` or `Complex Grass` checkbox is checked and that the `Texture size Min` is set to `32`. Not setting this to 32 will result in no grass billboards being created.

Press `Start` and allow the tool to generate the textures. Once completed, it will ask if you want to `Exit` or `Zip&Exit`. I recommend choosing `Exit` as you can achieve much better compression via 7Zip. Copy the data from your output folder into a new mod and activate it.

### DynDOLOD & Occlusion

#### Generation

Ensure that your xLodGen and TexGen outputs are active. Run DynDOLODx64 and allow it to load all your mods. In the top left section where it lists worldspaces, right click and press select all. Load the relevant rules that you want, in this case we’ll load medium rules. Ensure that the `Grass Lod` checkbox is checked and it is set to `Mode 1` and then pick your preferred lod settings. Once you have set them, it should look similar to this.

![DynDOLOD Settings for grass lod generation](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLOD/GLDDLDNew.webp)

Another note on settings. Billboard brightness is one that you adjust if you find that your lods are too bright in game. I have this set lower due to some of the tree mods I use. Ultra trees generates 3D tree lod and can be performance-intensive depending on the tree mods you use. However, Ultra Tree lods do get unloaded wheras the hybrid lods do not. I personally recommend using 3D tree lod as the visual quality difference is substantial for a minor perforamnce defecit. Anything above `1024` on tile size billboard is not recommended as you are beyond the threshold of visual quality to performance. And finally, the rules govern how DynDOLOD will generate things and at what quality. 

  -  *Note: Certain tree mods require specialised tree rules in order for them to render properly in the worldspace. Known mods that require them include: Myrkvior, Trees Addon SE and Skyrim Flora Overhaul. It is likely there are more tree mods that require special rules.* 

DynDOLOD 3.0 now includes Occlusion as part of it's toolset so we no longer need to generate Occlusion via xLodGen. I recommend the settings shown in picture above for generation as these are very similar to the original one's used in xLodGen occlusion.

Once you have configured the settings how you wish, click `OK` and DynDOLOD will begin its generation. This can take a very long time depending on how many worldspaces you have, as well as your system specifications. Once it is completed, a pop-up will appear. As with TexGen, you have the option to either `Save&Exit` or `Save&Zip&Exit`. I recommend choosing `Save & Exit` as you can achieve much better compression via 7Zip.

Copy the data from your output folder into a new mod and activate it. On the right pane, `DynDOLOD.esm` should be moved to be the last ESM after your worldspace mods. In my case, that is Lux so I place it after `Lux - Master Plugin.esm`. `DynDOLOD.esp` should be the second last and `Occlusion.esp` shoud be the last plugin in your load order.

## Final Steps

### Grass Cache Helper [Optional]

Due to how No Grass in Objects handles the grass growing in places via raycasting, this can be performance intensive on certain machines. To alleviate this, a mod called `Grass Cache Helper NG` can be used to allow us to turn off `No Grass in Objects`.

Disable `No Grass in Objects` & enable `Grass Cache Helper NG` [if you're using it] and then refresh Mod Organizer. 

### Testing In Game

You are now ready to test in game and see how it looks. After running the game, you may see some files in folders called `Grass` and `GraassConsole` in your `Overwrite` mod. You can safely ignore these.

**Note**: Depending on which grass mod you use depends on how much FPS you will use. I use [Fantastic Grasses](https://www.nexusmods.com/skyrim/mods/105903) which I have custom patched for bounds and complex grass and encounter minimal FPS loss. Your mileage, as always, may vary.
