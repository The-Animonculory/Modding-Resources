## ENB Tips
*Feel free to make suggestions or contribute.*

### Quick Notes
- Keep `CTRL + F` by your side for this guide.
- This guide does not show you how to install ENB.
- This guide does not show you how to create an ENB.
- Not everything here will apply to your ENB, but hey, just trying to help. ;)
- First off, to tweak your ENB settings in-game, the key(s) to open up the UI will vary per ENB. By default, it's `SHIFT + ENTER`. If you've tried several combinations and still haven't opened up the UI, look for your enblocal.ini and edit what it says in KeyEditor. To check values, go here: https://css-tricks.com/snippets/javascript/javascript-keycodes/#aa-tester-tool
<img src="https://imgur.com/eRVASB5.png" width=50%></img>
- Also, please calibrate your monitor. http://www.lagom.nl/lcd-test/
- Lastly, remember to save often, especially when you like the changes you just made. 
  - How to save:

### Tweaks
- When tweaking ENBs, you have your Shaders window, and your Weathers window. 
- Certain settings will be overridden by `IgnoreWeatherSystem` and `IgnoreWeatherSystemInterior`.



#### Why does hair look funny? 
- Try to turn off/tweak `DetailedShadow` and `WETSURFACES`. Look for `ReflectionAmount` in `WETSURFACES`, if you decide not to turn it off.

![image](https://user-images.githubusercontent.com/92814468/167032260-00ce0b1b-ff71-445b-865d-14a4f84bf73e.png)

#### Why are embers so red?
- Tweak `WINDOWLIGHT`.

#### How do I remove the black bars?


#### Why are the corners of my screen dark?
- That's the Vignette setting -- add more info here

#### Why does the water look green?
- Change the brightness in the `WATER` section. Or your water mod.

#### So much water reflection. Doesn't matter what I do.
- There are mods like this, to help: https://www.nexusmods.com/skyrimspecialedition/mods/64736
- Really depends on what mods you have. There are other brightness and reflection fixes. 
- Also tweak the `WATER` section, evidently.

#### When I move from what seems like the same location, the weather suddenly changes.
- You likely have a weather forced by location. To remove this, go into your `enbseries` folder and look for `_locationweather.ini`.
<img src="https://imgur.com/tlCwuGe.png" width=70%></img>
<img src="https://imgur.com/W3yIckx.png" width=70%></img>

#### How can I make the mountains brighter/darker?
<img src="https://imgur.com/x1bbbux.png" width=50%></img>
- Tweak `FogAmountMultiplier` and other relevant values as desired in `ENVIRONMENT`.

#### The sunrays and godrays hurt my eyes!
<img src="https://imgur.com/swGG5do.png" width=70%></img>
- Tweak `PROCEDURALSUN` and play with the `GlowIntensity` values.

#### How do I make the lighting warmer/cooler?

#### The sun is hitting my grass weirdly.

#### How do I get that foggy look?
<img src="https://imgur.com/kBEJUoA.png" width=50%></img>
- Tweak `GAMEVOLUMETRICRAYS` and `VOLUMETRICRAYS`.

#### My candles look like they're vanilla candles. The "twinkle" look is there.
- Edit your `LIGHTSPRITE` settings.

#### Why is there a gigantic glow around candles and things like nirnroots?
- Edit your `LIGHTSPRITE` settings.

#### How do I disable/adjust Depth of Field and Film Grain?
- Uncheck `EnableDepthofField` in `EFFECT`.
#### Which settings are relevant to adjust to help darken/lighten lights?
- Torches, lanterns: Go to `ENVIRONMENT` and tweak `PointLighting` (Intensity, Curve).

#### Shadows look really weird. What gives?
- Do you have [EVLaS](https://www.nexusmods.com/skyrimspecialedition/mods/63725) when your ENB doesn't use it? If it looks off, it's probably incompatible.

#### How can one tweak the brightness?
- So many ways. I personally tweak what's in `ENBEFFECT` and `ENBEFFECTPOSTPASS` first, before anything else. These sections vary so much per ENB, but you have your usual clues, like Brightness, Gamma correction, and you might as well modify Saturation and Contrast if they look incorrect. "Correct" values are typically 1 or 0. Additionally, many ENBs also come with Fake HDR. 
#### How can I improve performance?
- Uncheck `EnableLens`.
- Uncheck `EnableBloom`.
- Uncheck `EnableDepthofField`.
- Uncheck `EnableTessellation` in `WATER`.
- Uncheck `ComplexFireLights` and `ComplexFireLights` OR
  - Uncheck `EnableBigRange` in these two settings.
 
#### Shiny brows? Uhh...
- Grab [this wonderful mod](https://www.nexusmods.com/skyrimspecialedition/mods/66265) by bingus.

#### Why is skin so saturated?
- Tweak `SUBSURFACESCATTERING`. You will see saturation values. 
- You may also want to change the brightness of the skin. Go crazy with the tweaks and see what happens.
- Keep in mind that `SUBSURFACESCATTERING` also affects other things, but mostly skin.

#### Fog coming from windows looks weird.
- First, you might have some sort of mod conflict. If not the case, try tweaking the `PARTICLE` section.

#### Webs look REALLY bright. 
- See if [this](https://www.nexusmods.com/skyrimspecialedition/mods/29872) fixes your issue first.
- Also check if you have the latest [Particle Patch for ENB](https://www.nexusmods.com/skyrimspecialedition/mods/65720).
- You could also tweak the `PARTICLE` section. Specifically `LightingInfluence` and `AmbientInfluence`.

#### Why does hair look weird/yellow/glowy/orange in different angles?
- Disable or tweak `CLOUDSHADOWS`.

#### What's affecting skin + environment glossiness?
- Tweak `WETSURFACES`. 

## ENB Dev Notes
-Spawn as Khajiit to test imagespace.
*Tweak for all times and check various weathers, if desired. Open up the console and coc to these places.*
- `whiterunexterior01`.
- If feeling risqué, `bleakfallsbarrowexterior`, while looking towards Whiterun.
- `markarthsilverbloodinn`.
- `katlasfarmexterior`, check the underwater values also.
