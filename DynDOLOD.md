# DynDOLOD 3.0 for Skyrim SE/AE - by Althro

## Intro
So you’ve got your modlist all nice and ready and are now onto the process of creating lods for your game. But how do I do them, and how do I make sure my shows my updated trees and terrain?

Well, you’re in luck as this guide goes over how to do it. We’ll not be covering all the settings, rather just how to run it and what you’ll need to run it. We also cover A Clear Map of Skyrim settings and how to get a pretty map using the latest version. Grass Lods are covered, however these **only work on Skyrim version 1.5.97**.

**Note: This guide is only for Mod Organizer 2 users.**

## What you will need

Here is a list of things you will need: 

- The latest [xLodGen and SSE Tamriel Extended.esm](https://stepmodifications.org/forum/topic/13451-xlodgen-terrain-lod-beta-81-for-fnv-fo3-fo4-fo4vr-tes5-sse-tes5vr-enderal-enderalse/)  
- [DynDOLOD 3.00](https://www.nexusmods.com/skyrimspecialedition/mods/32382)  
- [DynDOLOD 3.00 Reources](https://www.nexusmods.com/skyrimspecialedition/mods/52897)
- [Unique Map Weather Framework](https://www.nexusmods.com/skyrimspecialedition/mods/59919) (Optional)
- [A Clear Map of Skyrim and Other Worlds](https://www.nexusmods.com/skyrimspecialedition/mods/56367) (**BOTH FILES**)

## The Main Steps

### Installing Everything
xLodGen, ACMOS Road Generator Tool and DynDOLOD should be installed to the `tools` folder of wherever your Mod Organizer is. In this case, it’s `Tinvaak\Tools`. Once they are there, open your Mod Organizer. Create a new mod named `Grass Cache`.  Add the x64 versions of xLodGen, TexGen and DynDOLOD as executables. We use the x64 as we are modding Skyrim SE and it is a 64-bit game. Note: You must add `-sse` to the arguments section for xLodGenx64, TexGenx64 and DynDOLODx64; otherwise they will fail to run. 

For xLodGen, after the `-sse` line, you **must** add the argument `-o:"x:\Path\To\Output"` to ensure that the generated files go to the correct location and also regen the vanilla meshes. This output folder **cannot be in a folder that is read by MO2 to create the virtual file system**. Place it somewhere like `C:\Games\xLodGen Output`. You may need to zip the output afterwards to ensure that it can be installed as a mod by MO2. An example of how it should look is below.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/xLodGenPath.webp)

Install DynDOLOD 3.0 resources, checking all of the options aside from “Low-Res LOD Textures” and “Holy Cow”. If you are using Skyrim SE V1.6 or newer, you can leave the "Whiterun Exterior Grass" option unchecked. You can use the Low-Res LOD if you wish, but I think it’s best not to. Once you have it installed, you want it placed relatively high in your left pane. I have it positioned in the following location:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DDResourcesLocation.webp)

Once you have installed and positioned DynDOLOD resources, install Unique Map Framework. Ensure that you select the correct version of Skyrim you are modding. In this case, I am using version 1.6 so select the `1.6.x` option. Next, you want to install A Clear Map of Skyrim (ACMOS). Tick the options as shown in the picture below to ensure that the correct settings are installed.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/ACMOSInstall.webp)

Finally, you’ll want to install the `SSE-Terrain-Tamriel Extended` ESM. This is only needed during xLodGen and can be placed anywhere in the left pane of MO2. I tend to place it above the xLodGen Output. Once installed, activate it only when doing xLodGen and place it below the last worldspace ESM in your load order. In my case, this is `Wyrmstooth`.
  
  -  *Note: Your ESMs will all be **bold** in MO2's Plugin list, even though they may not necessary be named with an `.esm` extension.*

### xLodGen
Once you have all of that installed and the output paths set, activate `SSE-Terrain-Tamriel Extended` and move it to the correct position in the right pane as mentioned in the previous section.

  -  *Note: Some mods such as Majestic Mountains and Cathedral Landscapes come with files for Lod Generation. You will want to have these files activated during the process of running xLodGen. Majestic Mountains Lods in particular needs to be active all the way through.*

Then select xLodGenx64 from the executables dropdown in MO2 and press `Run`. It will proceed to load your entire load order. When it is done, a Dialogue box will open similar to the following:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/xLodGenSettings.webp)

Right click in the `Worldspace` area and press `Select All`. Ensure that only Terrain Lod is selected and then apply your Lod settings. I use custom lod settings for Lod4 to Lod16 which deliver the best performance to quality ratio. For Lod32, you **must** use the ACMOS settings which are shown in the picture below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/ACMOSxLodSettings.webp)

Press the `Generate` button and allow xLodGen to run and do its work. When complete, it will say “Lod Generation completed”. You can then close the program. 

### A Clear Map of Skyrim Road Generator Tool

Navigate to where you have installed the ACMOS road gen tool and open the program. You will greeted by a screen similar to the one below: 

[alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/ACMOSRoadGen.webp)

Click `browse` and navigate to where your xLodgen output folder is. Select the folder and press `Generate`. If a prompt appears asking if you wish to overwrite, press `Yes`. Allow the tool to run and do its work. Once it is done, it will offer you the option to zip the output. say "Yes" and let it zip the folder. Once it has finished zipping it will say "All Done!" and you can the close the program.

Navigate to where your xLodgen output folder is and create a zip folder of it if it is not zipped. Press the `Add mod from file` button and navigate to where your zipped xLodGen output is. Press the `open` button and install it as a new mod. Activate the mod and then deactivate `SSE-Terrain-Tamriel` and any other mods that you activated for the xLodGen process.

### TexGen
Run TexGenx64 and Allow the tool to load your mods and then choose the following settings. **If you are doing grass lods, tick the grass checkbox.** Note the output path as to where TexGen is sending the output.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/TexGenSettings.webp)

Press `Start` and allow the tool to generate the textures. Once done, the tool will open a pop-up. Press `Exit` or `Zip&Exit` if you wish to have the output zipped up for easier addition to a mod-manager or redistribution. In this case, we're choosing `Zip&Exit` as that allows us to add the output as a new mod in MO2 easier. Add the output as a new mod in Mod Organizer 2, and then activate it.

### DynDOLOD & Occlusion

#### Enabling advanced mode and Lod32

In order to have DynDOLOD start in advanced mode each time and enable the Lod32 setting **required by ACMOS**, you need to edit a line in the `DynDOLOD_SSE.ini` file. Navigate to where your DynDOLOD is located, open up the `Edit Scripts` folder, and then the DynDOLOD folder. Open the `DynDOLOD_SSE.ini` file and change the following lines:  

`Expert=1`
`Level32=1`

Save the .ini file and reopen MO2.

#### Generation

Ensure that your xLodGen and TexGen outputs are active. Run DynDOLODx64 and allow it to load all your mods. In the top left section where it lists worldspaces, right click and press select all. Load the relevant rules that you want, in this case we’ll load medium rules. Set your settings to be the same as this:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/DynDOLODSettings.webp)

Another note on settings. Billboard brightness is one that you adjust if you find that your lods are too bright in game. I have this set lower due to some of the tree mods I use. Ultra trees generates 3D tree lod and can be performance-intensive depending on the tree mods you use. However, Ultra Tree lods do get unloaded wheras the hybrid lods do not. I personally recommend using 3D tree lod as the visual quality difference is substantial for a minor perforamnce defecit. Anything above `1024` on tile size billboard is not recommended as you are beyond the threshold of visual quality to performance. And finally, the rules govern how DynDOLOD will generate things and at what quality. 

  -  *Note: Certain tree mods require specialised tree rules in order for them to render properly in the worldspace. Known mods that require them include: Myrkvior, Trees Addon SE and Skyrim Flora Overhaul. It is likely there are more tree mods that require special rules.* 

DynDOLOD 3.0 now includes Occlusion as part of it's toolset so we no longer need to generate Occlusion via xLodGen. I recommend the settings shown in picture above for generation as these are very similar to the original one's used in xLodGen occlusion.

Once you have configured the settings how you wish, click `OK` and DynDOLOD will begin its generation. This can take a very long time depending on how many worldspaces you have, as well as your system specifications. DynDOLOD 3.0 is multi-threaded now so on machines with multiple cores, it may complete faster than you think, if you've used DynDOLOD before. Once it is completed, a pop-up will appear. As with TexGen, you have the option to either `Save&Exit` or `Save&Zip&Exit`. Again, the choice is yours however in this guide we'll choose to zip it up as well.

Add the zipped output file as a new mod in MO2, name it `DynDOLOD Output` and activate the mod. On the right pane, `DynDOLOD.esm` should be moved to be the last ESM after your worldspace mods. In my case, that is Wyrmstooth so I place it after `Wyrmstooth.esm`. `DynDOLOD.esp` should be the second last and `Occlusion.esp` shoud be the last plugin in your load order unless you have Synthesis in which that would be last.

## Seasonal Lods

With the advent of Seasons of Skyrim and recent updates to DynDOLOD, seasonal lods can be created to provide matching distant detail for the season you are in. They are, also, very easy to generate and require only or two changes to create.

### xLodGen Seasonal

To have seasonal xLodGen output, tick the seasons checkbox in the bottom left and select which seasons you wish to have terrain lod for. **Note: This will take a lot longer than normal non seasonal generation.**

### DynDOLOD Seasonal

To have seasonal DynDOLOD output, tick the Seasons checkbox, the snow checkbox, and then select the seasons you wish to have DynDOLOD for. **Note: This will take a lot longer than normal non seasonal generation.**

## Grass Cache

**NOTE**: Grass cache **does not function** on builds using a Skyrim.exe **newer than 1.5.97** due to .Net Script framework being incompatible.

Grass Cache is a relatively new technology that allows you to pre-cache grass for all worldspaces in the game. This allows for DynDOLOD to create grass lods to increase the distance which you can see grass and also can give a more stable experience. **Do Note this can hurt your performance if set incorrectly**. 

### Required files
- [.NET Script Framework](https://www.nexusmods.com/skyrimspecialedition/mods/21294) (**ONLY WORKS ON SKYRIM 1.5.97**)
- [No Grass In Objects](https://www.nexusmods.com/skyrimspecialedition/mods/42161) (**ONLY WORKS ON SKYRIM 1.5.97**)  
- [Landscape Fixes for Grass Mods](https://www.nexusmods.com/skyrimspecialedition/mods/9005)
- [Worldspaces with Grass SSEEdit Script](https://www.nexusmods.com/skyrimspecialedition/mods/55152)

For the No Grass in Objects pre-cacher, place the plugin in the `plugins` folder of where your Mod Organizer 2 is installed. Relaunch MO2 and it will appear in the tools area (Shown as a spanner and screwdriver).

### Pre Generation Script & INI file setup
Before running grass cache, I recommend you use this script [here](https://www.nexusmods.com/skyrimspecialedition/mods/55152) to determine which locations to cache grass into. Download that script, save the zip file somewhere safe, and copy the file that ends ".pas" into your xEdit edit scripts folder as shown below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/GrassScriptPlacement.webp)

Open xEdit, allow all your plugins to load, and then apply the script. This process can take a while so grab a coffee. Once completed, a textbox will show on screen with the list of worldspaces to generate grass for. 

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/GrassScriptOutput.webp)

Copy this data and then Go into your `No Grass In Objects` mod, open the INI file, and paste the data in between the "" in the `OnlyPregenerateWorldSpaces =` section. It is **vital** this data is in between the quotes, otherwise it will not be read. You can see an example of how it should look below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/NGIOIni.webp)

Staying in the ini file, change the following lines to read the following:

- `UseGrassCache = True`  
- `OverwriteGrassDistance = 12000`  
- `OverwriteGrassFadeRange = 8000`  
`OnlyLoadFromCache = True`  
- `DynDOLODGrassMode = 1`  

A note on these settings: to improve performance, you can set the `OverWriteGrassDistance` and `OverwriteGrassFadeRange` to be lower. For the former, a setting of 8000 is a bit more than vanilla and may improve your performance. If you just wish to cache the grass but not for DynDOLDOD, change the `DynDOLODGrassMode` back to `=0`. `SuperDenseMode` is another section that you can alter if you wish to tone down the grass amount. I leave this set at `7` as it gives a good balance of performance to visuals; however, setting this to `6` can help improve performance.

### Bounds Data Recalculation

Any grass records that has no object bounds set will not generate anything during grass pre-caching. To ensure that grass has object bounds data, the following should be completed.

Firstly, open xEdit and filter your entire load order for grass records as shown in the picture below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FilterGrassRecs.webp)

Once the filter has finished applying, copy every record that is shown into a new esp flagged esl plugin. Name it something like "Grass Bounds Data" and save it. Your plugin should only contain similar to what is below:

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/GrassRecsPatch.webp)

Close xEdit and then open up the Creation Kit. Load your newly created grass plugin, click on `Grass` in the object window and highlight all the grass, right click and then select `Recalculate Bounds`.

![alt text](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/RecalcBoundsCK.webp)

Save the plugin and then exit the CK. Place the new plugin below all of your grass plugin and ensure it is active.

### Running Grass Cache

Grass cache will take a long time and may take several hours depending on the number of additional worldspaces you have. To increase the speed of the regeneration, there are a few things that you can try.

1. Reduce the resolution of the game so it is just big enough to still se the procress in the console. **Do not use BETHINI Poor of Low presets**, these will cause no grass files to be generated.
2. Deactivate any **non grass** texture replacement mods you have installed.
3. Should you wish to, you can create a new MO2 profile that only contains plugins that alter the worldspace and grass files. This will take a lot of trial and error and time, but could result in an overall quicker generation. Things to look out for in files/plugins would be edits to landscape records and stuff that adds/moves buildings and other objects such as town overhauls.

Once you have done all of the above, click on the spanner and screwdriver icon, and then select `PreCache Grass`. A pop-up will appear confirming that you wish to do this. Click `Yes`. Go grab a coffee and a good book or magazine - this can take a very long time.

Once it is completed, a pop-up will appear saying that grass generation has been completed. **If you do not have a mod set to catch files generated during gameplay, the grass will be in the `overwrite` mod at the bottom of your Mod Oragnizer's left pane (assuming you have the mods sorted by `Priority`).** You should see a folder called `grass` with a load of `.cgid` files inside. Move that folder to the mod called `grass cache` that you created. Press `F5` to refresh MO2 and then activate the mod.

### Grass Lod creation

To create grass lods, you need to have grass billboards which are created by Texgen. Follow the TexGen section but tick the `Grass` checkbox, and set the `Texture min Size` to 32. Allow TexGen to run and then save the output.

For DynDOLOD, follow the settings given however tick the `Grass Lod` checbox and ensure it is set to `Mode 1`. This will take considerably longer to create and requires a large pagefile to complete efficiently.
