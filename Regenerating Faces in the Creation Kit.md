# Regenerating Faces in the Creation Kit for Skyrim SE/AE - By Althro

## Intro

So you're almost done with your modlist and all that remains is the NPC's. You've tried out many NPC's and got frustrated that none meet your style, or you're getting black faces here there and everywhere. Well, the Creation Kit has a solution for you.

> **NOTE: This is a BRUTEFORCE method of getting every face on every NPC in the game to be correct and rendered. You should ONLY do this once you have FULLY FINALISED your modlist. We are NOT RESPONSIBLE for any errors that occur if you remove the facegen and encounter errors.**

The purpose of regenerating all the faces for NPC's in the game to provide a level of consistency across the entire game and ensure that newly added NPC's conform to your chosen styling. Paired with some nice textures, you can create a unique vanilla friendly look to your NPC's.

## Setting Up

### Required Mods

To effectively generate facegen, you will need the following items:
1. The Creation Kit from Bethesda Net 
2. [Creation Kit Platform Extended for Skyrim](https://www.nexusmods.com/skyrimspecialedition/mods/71371)
4. The main file from [Tweaked Creation Kit Ini](https://www.nexusmods.com/skyrimspecialedition/mods/19817)
5. [Synthesis](https://github.com/Mutagen-Modding/Synthesis/releases)
6. [Cathedral Asset Optimizer](https://www.nexusmods.com/skyrimspecialedition/mods/23316)
7. [My Custom BSA Packer CAO Profile](https://github.com/The-Animonculory/Modding-Resources/blob/main/BSA%20Creation.7z?raw=true) (optional but highly recommended. Extract the folder into `\Cathedral Asset Optimizer\Profiles`)

It is recommended that you have some updated textures for NPC's such as [Tempered Skins](https://www.nexusmods.com/skyrimspecialedition/mods/7902) and [Reverie Skin](https://www.nexusmods.com/skyrimspecialedition/mods/64314) and upscaled/reworked warpaint. 

### CK ini Configuration

It is recommended that you change the `TintMaskResolution` line in the `CreationKitPlatformExtended.ini` to `1024` instead of 512 as that will result in better quality facetints being created. The difference is **very noticable**.

## Regeneration

### Creating the NPC Faces Plugin

To ensure that all the required resources are loaded by the creation kit for facegen, we need to run a Synthesis Patcher called [NPCs Face Data](https://github.com/caiobraz/Synth-NPCs-Face-Data). This patcher will check all of your plugins for NPC's and facedata and add the masters to the plugin along with the NPC's in question.

To run the patcher, firstly load Synthesis and then press the `Git Repository` button to add a new patcher. In the `Repository Path` field, paste in: "https://github.com/caiobraz/Synth-NPCs-Face-Data" (Remove the ""). Make sure the `Project` field is set to `SynthNPCsWithFaces/SynthNPCsWithFaces.csproj`. An example of how it should look is given below.

![Synthesis Patcher](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FaceGen//SynthesisPatcher.webp)

Run the patcher and allow it process. Once it is completed, close Synthesis and activate the new plugin called `NPCsWithFaces`. The plugin may be present in your overwrite folder or in a mod that catches generated files if you have one set up. 

### Loading the CK and the faces

Before opening the creation kit, it is __**Strongly**__ recommended that you create a mod called "CK Output" and set your creation kit to output files there. If you don't, bad things can happen. To do this, complete the following:

1. Right click in MO2, press `Create New Mod` and name it something sensible (for the purposes of this tutorial, we are naming it "CK Output")
2. Activate the mod
3. Go to the right hand drop down menu, press `edit` and select the Creation Kit.
4. Tick the button that says `Create files in mod instead of overwrite`. (example given in the picture below)
5. Press the dropdown menu next to it and select the new mod you just made.
6. Press the `Apply` button and then the `OK` button.

![MO2 Overwrite](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FaceGen/CKOutput.webp)

It's now time to get all the resources loaded into the creation kit. Activate any other loose files that you wish to use in the facegen process and then complete the following.

> *Note: Anything that you activate with an ESP plugin after this point will **NOT** be loaded in the CK. Go back and re-run the Synthesis patcher to add them to the loader.*

1. Select the creation kit as the executable and then press the `Run` button. 
2. Once it has finished loading, press the folder icon.
3. Double click the `NPCsWithFaces.esp` plugin that we just made with Synthesis.
4. Press the `Set as Active File` button.

![CK Set Active File](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FaceGen/CKPluginLoad.webp)

### Regeneration

Once the plugin and all its dependencies have loaded, select the Objects window and click on the `Actors` which is in bold. To make life easier for, click on the header that says `Race` twice to filter by race.

> *Note: This is not essential, but does make the next steps much much easier.*

![CK Actors Filter](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FaceGen/CKObjectActor.webp)

The following steps are extremely important to do in the correct order. **Failure to do so will result in FaceGen that is weird and not working!**

1. Select all of the NPC's from the bottom up until you see RedguardRaceChild. **DO NOT SELECT ANY CHILD RACE**.
2. Press Ctrl+F4 and confirm any dialogue box that comes up.
3. Wait until the process is completed and then confirm any dialogue box that comes up.
4. Select all the NPC's from after RedguardRaceChild until you see NordRaceChild. **DO NOT SELECT ANY CHILD RACE**.
5. Repeat steps 2&3.
6. Select all the NPC's ***AFTER NORDRACEASTRID*** until you see ImperialRaceChild. **DO NOT SELECT ANY CHILD RACE OR ASTRID!!!!! IF YOU SELECT ASTRID YOU WILL BREAK ALL OF THE FACEGEN!!!!!!!!!**
7. Repeat steps 2&3.
8. Select all the NPC's after ImperialRaceChild until you see BretonRaceChildVampire. **DO NOT SELECT ANY CHILD RACE OR CHILDVAMPIRERACE**.
9. Repeat steps 2&3.
10. Select all the NPC's after BretonRaceChild up until the top of the list of NPC's. **DO NOT SELECT ANY CHILD RACE**.
11. Repeat steps 2&3.
12. You can now exit the creation kit.

## Packing the files into a BSA

Depending on how many mods you have, your generated FaceGen can be anything from around 8GB to well over 50GB. Naturally, we want to try and compact that to both save space and also minimize conflicts. Thankfully, when you pack facegen into a BSA, it can reduce the overall size down to a tenth of what it is. To compact into a BSA, complete the following.

1. Create a new mod called `Facegen` and move your regerenated facegen into it.
2. Open Cathedral Asset Optimizer and load the `BSA Packer` profile or a similar one. Check the `Show Advanced Settings` box.
3. **IMPORTANT:** Ensure that the`Maximum Size` is set to `1.96`. **IF THIS IS LARGER THAN THAT VALUE, YOUR BSA'S WILL NOT LOAD.**
4. Press `Open Directory` and navigate to where your Facegen folder is. Select it and press `Select Folder`.
5. Verify that the settings look the same as below (**Note**: Where it says `C:/Games/Tinvaak 1/Mods/Tinvaak Facegen`, make sure it says the folder you just selected.

![CAO Settings for BSA Packing](https://raw.githubusercontent.com/The-Animonculory/Modding-Resources/main/Images/FaceGen/CAOPacking.webp)

6. Click on `Log` to move to the logging tab. You will able to monitor CAO's progress in there.
7. Press `Run` to begin the process. If you recieve a pop-up windows asking if you want to save, press `Yes`. This process can take a long time so grab a good book and a mug of coffee.
8. Once CAO has completed, you can safely close the application.
9. Re-Open/navigate back to MO2 and activate the new plugins you see at the bottom of your load order.
10. Jump for joy as you are now ready to play the game.

## FAQ

**Why do I not generate the faces for the Children?**

Due to the unique TRI structure of the child head, regenerating them results in them looking like shiny potatoes. If you want them to look better, I recommend [Rustic Children](https://www.nexusmods.com/skyrim/mods/63353/) or [Simple Children](https://www.nexusmods.com/skyrimspecialedition/mods/22789).

**What happens if I generate Astrid's face?**

All your NPC's will have burnt faces.

**Do I have to repeat the process every time I add a new mod with NPC's or remove it?**

Technically speaking no, but it is recommended if you want to have consistency.

**What mods do you use for this?**

I have used a wide variety of mods for this. A good mixture is [Reverie](https://www.nexusmods.com/skyrimspecialedition/mods/64314) and [Skysight Skins](https://www.nexusmods.com/skyrimspecialedition/mods/6580). BNP skins are good as well.
