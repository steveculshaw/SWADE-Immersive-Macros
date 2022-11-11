Below you'll find some descriptions on the macros. Some require other modules to work properly. Some are compatible with other modules though, well they should be compatible with mostly anything really so I won't give a full list. Instead I'll give you a list of modules that *enhance* the functionality of the macro.  
In the very last line all macros tell you their version number. Use it to check whether or not you're using the latest version.  

### Spend Benny
**Requirements:** None.  
**Compatibility:**  
- [Dice So Nice](https://foundryvtt.com/packages/dice-so-nice/) for the Benny throw.

**Immersion setting:** None.  
**Suggested icon:** `systems/swade/assets/benny/benny-chip-front.png`  
**Description:**  
This macro will basically just spend a Benny. It does use the animation from Dice So Nice if it is installed and activated but doesn't require DSN. With SWADE Spices & Flavours you can customise the look of the Benny. This module will automatically find if you're using Spices & Flavours and uses the back image of the Benny if you've set one up.  
The macro will use the Bennies of the selected token (needs a token selected to function). If the user is a GM it will also use the GMs Bennies but will *always* spend token Bennies first and only touches GM Bennies once the token is out of Bennies. It also gives a warning if no more Bennies are left.  
*This macro is the basis for most of the other macros.* Whenever a macro uses a Benny, it will do so using the code from this macro and thus having all its features which I won't detail for other macros.  

### (Un-)Shake
**Requirements:** None.  
**Compatibility:**  
- [Dice So Nice](https://foundryvtt.com/packages/dice-so-nice/) for the Benny throw.

**Immersion setting:** SFX.  
**Suggested icon:** `modules/swim/assets/icons/status_markers/0-Shaken.png`  
**Description:**  
This macro will first check whether or not the selected token (needs a token to be selected) is marked as Shaken (checks for the checkbox on the sheet). If the token is *not* Shaken, it will mark it as Shaken (tick the checkbox). It it is Shaken, then it will prompt a system roll. After rolling it gives a chat message detailing the result. If the result is best it will remove Skaken and that's it. If the roll could've been better it opens a dialogue giving the user the option to spend a Benny to remove Shaken. If accepted a Benny is spent (if there are Bennies left) and removes Shaken. The user can also decline which just closes the dialogue. The dialogue will not appear if there are no more Bennies left (including GM Bennies if the user is a GM). It also tells the user how many Bennies are left in the dialogue.  
Now here is the deal: The macro is aware of any core Edges and Special Abilities that can alter the unshake roll and *automatically* adjusts the roll. You can set up own ones as well by adding them to the `const edgeNames` object (inside the []); put them in '' and only use lower case. The macro requires you to set up Special Abilities like Undead as Edges or Abilities though, so keep that in mind. Also the macro currently does not add a +2 on a reroll if the token has Elan. *Keep in mind that only english Edge names are supported yet.*  
The macro is also aware of Snake Eyes (Critical Failure) and offers no use of a Benny when Snake Eyes occur. It does *not* check for Snake Eyes on Extras though.  
This macro comes in two variants: SWADE and SWD. I like the SWD rules regarding Shaken much better but the choice is yours. Here are the differences:  
**SWD:** To act this turn you need a raise, success removes Shaken but you may only act *next* turn. While Shaken your Pace is halved.  
**SWADE:** To act you'll only need a success.  

### (Un-)Stun
**Requirements:** None.  
**Immersion setting:** SFX.  
**Suggested icon:** `modules/swim/assets/icons/status_markers/2-Stunned.png`  
**Description:**  
This macro is very similar to the (Un-)Shake macro but handles Stunned. If the selected token (needs one selected) is not Stunned, it will be marked as such, including all the effects that come with it. Otherwise it will initiate a roll to unstun and adds/removes conditions according to the result. It is aware of Snake Eyes. It supports SFX on applying Stunned in the same way as (Un-)Shake. **Important:** Set up the path to your prone image to the exact same path as your prone image in the modules setting. This is not necessary if you have imported the CUB Contion Lab file (modules/swim/assets/imports/). If you use the system included status markers the path is: `systems/swade/assets/icons/status/status_prone.svg`.  
The function supports modifiers from Active Effects. To use it create an active effect with the attribute key `SWIM.unStunMod` (case sensitive), the change mode `Add` and a value of your choosing. A bonus must not have a `+` in front of the number, a penalty needs a `-` in front of the number. It only applies as long as the label (name) of the AE is not equal to any recognised Edges or Hindrances (currently only Combat Reflexes).

### Soak Damage / Damage Centre
**Requirements:** None.  
**Immersion setting:** SFX.  
**Suggested icon:** `modules/swim/assets/icons/status_markers/3-Incapacitated.png`  
**Description:**  
One of the most complex macros I ever wrote. It soaks and applies Wounds. It tries to cover everything from SWADE core and guides the user through the process. It is aware of (Un)Holy Warrior and Elan. It follows the core rules and thus is aware of Critical Failures.  
It also supports SFX again. You can configure a path to your desired SFX in the modules configuration.  
You can also use the Gritty Damage setting rule by adding the name of your Injury Table in the modules config. It must be the *exact* name of your Injury Table, best copy and paste it. **Gritty damage is only used for non-GM accounts.** Gritty damage will not be used when you have not set up an ID. So just leave this setting empty if you don't desire to use it.
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Soaking%20Wounds.jpg?raw=true"> </p>  
Since its creation this macro became more and more advanced however. As of today it not just features adding/soaking wounds but also makes Vigor Rolls for you (if you wish) on Incapacitation to avoid Bleeding Out/dying and it also makes Vigor Rolls for you when you already are Bleeding out. It is as a complete *Damage Centre* as it can be and indeed, this is likely how I'll rename it in the future.  

https://user-images.githubusercontent.com/1230041/184658399-b29e4ab1-e100-4d14-afa2-319f12da2db0.mov

(Assets used in the scene are from ForgottenAdventures and not part of SWIM.)  

### Ammo Management  
**Immersion setting:** SFX (optional, user provided).  
**Compatibility:**  
- [Better Rolls 2 (BR2)](https://foundryvtt.com/packages/betterrolls-swade2)  

**Description:**  
A pretty complex macro. The simple one is pretty straight forward and will not be maintained any longer. The Enhanced version has got it's own documentation [here](https://github.com/SalieriC/SWADE-Immersive-Macros/wiki/Ammo-Management). Make sure to read it, it is mandatory to do so, otherwise the macro will not work.  
It comes with optional BR2 integration for the shooting/using ammo part. How the integration works is documented in the above link as well.  
**Wait, where do I get weapon sound effects?**  
I can't include that many sfx right now. It is rather difficult to find good weapon sounds which I am allowed to include and I don't have the funds to buy them for this module. I'm not gonna recommend any particular way on how to get adequate sound effects, figuring that out is on you. Just know that there are many resources you should be able to use out there. As a general lead: Look for PC game modifications which alter the weapon sounds in that specific game. You may not be allowed to use the sfx from the game directly (depends on the game of course), but those from mods are usually not a problem but check that before you do take them. I cannot be held responsible for any breach of contract or copyright you commit it is on you to check whether or not you're allowed to use the sfx you find.  
You may also want to take a look at [SoundFx Library](https://foundryvtt.com/packages/soundfxlibrary) by Cris. It comes with a few bow sounds which may be sufficient for your standard medieval fantasy settings.  

### Fear Table
**Requirements:** None.  
**Immersion setting:** SFX.  
**Suggested icon:** `modules/swim/assets/icons/status_markers/2c-Frightened.png`  
**Description:**  
This does mostly the same as the macro in the core rules module except you can manually set up the name of your Fear table and it has the option to play a sfx on execution.  
This macro basically just opens a dialogue that asks for a fear modifier and then rolls on your Fear table with that modifier. Remember the rules on this: Negative fear modifiers become positive in the table, so do not enter negative numbers unless you know what you're doing.  

### Mark Dead
**Requirements:** None.
**Immersion setting:** SFX.  
**Description:**  
This is a rather simple macro that marks a token as Incapacitated! and is mainly intended for NPC Extras. It requires CUB to toggle the Inc.! status and Health Estimate.  
The macro plays a sound effect on execution and will mark all selected as Inc.! It works both ways though and can uncheck Inc.! if needed.  

### Power Point Management (CURRENTLY NOT WORKING)  
**Incompatibility:**  This macro is *not* compatible with the power point management offered by the SWADE system. Disable it if you want to use this macro.  
**Requirements:**
- [Health Estimate](https://foundryvtt.com/packages/healthEstimate/)

**Immersion setting:** SFX.  
**Description:**  
Oh boy, this one was a pain to create and a great way to learn. It tries to handle all core methods of recharging and spending Power Points and also supports Deadlands The Weird West in the sense of that it offers Whateley Blood. It handles Fatigue and Wounds and only shows the Soul Drain or Whateley Blood stuff if the Edge is found on the character (no language support yet). It will spend as many PP as you set up in the dialogue or recharge as many. It also offerst to recharge 5 by spending a Benny or said Edges.  
SFX works differently here. You need to set up a Playlist called "Magic Effects" and the macro will get all the tracks in it and then plays the selected when PP are spent (not recharged). This offers more flexebility.  
In terms of other SFX: The macro again uses the Incapacitation sfx and the wounded sfx but also a new one played on taking a level of Fatigue.  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Power%20Point%20Management.jpg?raw=true"> </p>  

### Personal Health Centre  
**Requirements:**
- [Health Estimate](https://foundryvtt.com/packages/healthEstimate/)  

**Compatibility:**
- [Sequencer](https://foundryvtt.com/packages/sequencer) (Enabling VFX)

**Immersion setting:** SFX & VFX.  
**Description:**  
This macro is more or less the opposite of the Soak Damage macro. It offers functionality to remove wounds in a generic way (i.e. due to the Healing Skill or Power) and also a way to roll on Natural Healing, interpreting the results, removing wounds, offerring rerolls and is aware of Snake Eyes (adds another Wound or Inc.!). It supports Fast Healer and (on rerolls) Elan as well.  
It also supporst the Regeneration Special/Racial Ability but it must be set up as an Edge or Ability called "Fast Regeneration" or "Slow Regeneration". Then it adjusts the time that needs to be passed until a Natural Healing roll can be made. If your setting calls for longer or shorter periods of time until a Natural Healing roll can be made (Hellfrost comes to mind), then you can set this up in the modules settings.  
It uses the sfx for Wounds, Inc.! and Healing.  
The macro is also capable of removing Fatigue using a given number, which also supports a unique sfx.  
Both, removing Fatigue and Wounds, does support using potions. For this you need to provide the potion names in the relevant game settings. Make sure that you enter the **exact** names (case sensitive) and seperate them by `, ` (comma + empty space). Drinking the potion also has a unique sfx and drinking a potion reduces the quatity by 1. If it was the last potion of this kind, it will be removed from the inventory.  
It is alsocapable of playing visual effects (VFX) if Sequencer is installed and active. I suggest Generic Heal and Cure Wounds for everyone with access to the JB2A patreon module.
Finally it can also be used to heal the target even if you don't have permission to change the target. For this you need to select your token and target another.  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Personal%20Health%20Centre.jpg?raw=true"> </p>  

### Token Vision  
**Requirements:** None.  
**Immersion setting:**  
- Light animation & colour  
- Sound effect  

**Description:**  
This macro was inspired by a macro from [@Sky#9453](https://github.com/Sky-Captain-13/foundry) that supported DnD vision and lighting. I altered it to suit Savage Worlds. For v10 I completely rewrote it and there is almost nothing left from the original. I have to say though, that information on vision and illumination is very lackluster in SWADE with regards to VTT software. It works fine on an actual tabletop but not with dynamic lighting on VTTs. I had to bring some personal taste in but I tried to stay as true to the rules as I could.  
Here are the options explained:  
  
**Light Source:**  
- No Change: Does not change the current settings.
- None: Deactivates all emit light settings from token.
- Candle: 2" radius of bright light.  
- Lamp: 4" radius of bright light.  
- Bullseye: 4" beam of bright light with an angle of 52.5 degree.  
- Torch: 4" radius of bright light.  
- Flashlight: 10" beam of bright light in an angle of 52.2 degrees.  

**Illumination:**  
- No Change: Does not change the current settings.  
- Full Light / Daylight: Sets the tokens vision and detection mode to 1000" (the maximum allowed by Foundry)  
- Dim: Sets the tokens vision and detection mode to 1000" as well because there is no clear distinction.  
- Dark: Sets the tokens vision and detection mode to 10".
- Pitch Dark: Sets the tokens vision to 0" and detection mode to 1".

**Vision Type:**  
- No Change: Does not change the current settings.  
- None: Sets the tokens vision to 0" and detection mode to 1" unless Illumination is better.
- Low Light Vision`*`: Sets the tokens vision and detection mode to 1000" unless Illumination is better.  
- Infravision`*`: Sets the tokens vision to 0" and detection mode to 1000" in the "see heat" mode unless Illumination is better.  
- Darkvision`*`: Sets the tokens vision and detection mode to 10" unless Illumination is better.  
- Night Vision Device: Sets the tokens vision and detection mode to 1000" unless Illumination is better but tints the vision green ("light aplification" mode.  

`*` Only available if the actor has a special ability called like the mode.

Additionally, the user can set up a light colour for the light source and it will be animated with the "torch" animation from core, but rather subtle.  

**The illumination level** can be set to a default by the GM in the scenes lighting section on the left. There is a button that lets you configure the default for players for that scene.

**WARNING:** This macro will **irreversibly overwrite your configured detection modes on the token!** This is because it's really hard to deal with them atm. It will set up "Basic sight" and "See heat" as the others are not that useful for SWADE right now. I will adjust that when this changes.

### Chase Setup  
**Requirements:** Chase layouts/scenes (included in a compendium) and a roll table with card images.  
**Immersion setting:** System card deal sound.  
**Description:**  
This will set your chase scene up with little effort. Accessed easily on the tile controls on any scene (the car icon, added by the system and overwritten by SWIM). It places the cards automatically in the correct position. See the [Chase Scenes documentation](https://github.com/SalieriC/SWADE-Immersive-Macros/wiki/Chase-Scenes) for details.  
*This requires the chase scenes that come in a compendium with this module.* These carry various options, players have in a chase, made with permission from Shane.  
If you don't want to use my chase layouts you can also change the settings either in the dialogue after pressing the button mentioned above or by changing the default values in the SWIM module configurations.  
**Note:** This currently uses a roll table instead of a card deck, thus you'll need a chase card table. One you can import is included in a compendium in SWIM for your convenience.  

### Raise Calculator (Dynamic)  
**Requirements:** None.  
**Immersion setting:** None.  
**Description:**  
A simple raise calculator that can be easily accessed from the controls on the left side of the screen as long as you have a scene. It is the big plus button in the basic (token) controls.  
Changes the amount of Raises dynamically, depending on your input while you type. Whenever you change the result input field the text below is adjusted and will show you the amount of raises. It does not have a button because a button isn't needed. You could keep this one open at all times and change the values whenever you want.  
Below are screenshots from the dynamic version:  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Raise%20Calculator%201.jpg?raw=true"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Raise%20Calculator%202.jpg?raw=true"> </p>   
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Raise%20Calculator%203.jpg?raw=true"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/Raise%20Calculator%204.jpg?raw=true"> </p>   

### Deviation  
**Immersion setting:** None.  
**Description:**  
A utility macro made by [Bruno Calado](https://github.com/brunocalado) that calculates Deviation. Will ultimately become part of the Shooting (enhanced) macro. Image source: [freesvg.org](https://freesvg.org/analogue-clock-vector-graphics).  

### Scale Calculator  
**Immersion setting:** None.  
**Description:**  
A utility macro made by [Bruno Calado](https://github.com/brunocalado) that calculates Scale depending on Size and gives the appropriate malus/bonus. Requires a target to function.  

### Loot-o-Mat  
**Immersion setting:** None.  
**Description:**  
This macro relies on an Additional Stat set up on your actors: "treasure" (type string, no max value). Your bestiary needs this Additional Stat on the actors to function automatically (but there is another way of using it, see below).  
Allowed treasure types are: "Meager", "Worthwhile", "Rich" and "Treasure Trove" which are common loot types i.e. in Hellfrost, 50 Fathoms or the Fantasy  Companion.  
It is also common to these settings to state treasure per x opponents (i.e. "Meager, per 5 Orcs"). In this case set up the Additional Stat like this: "Meager, per x", "Meager per x" or "Meager/x" where x is the amount of enemies as a number *not* a word. These three options are covered by the macro, use no other format!  
   
**How does it work?**
The macro searches all selected and targeted tokens (it won't use duplicates if targeted and selected tokens are the same, don't worry) for the additional stat "treasure" and makes a roll for loot, then it creates a chat message with the random loot amount.  
Alternatively, you can use the macro with no tokens targeted/selected and a dialogue will appear that lets you enter the amount of enemies with their different loot types individually. This dialogue will also open when none of the selected and targeted tokens has the Additional Stat so you can safely use the macro without this.  
If the loot type is set up with an amount of enemies like above (i.e. "Meager, per 5"), the number is used for division and the result is rounded to two decimals.  
In Hellfrost this represents Silver Scields, in Settings which don't use a sub-currency (like 50f), just ignore or round off manually.  

### Shape Changer    
**Immersion setting:** SFX & VFX
**Requirements:**  
- [Warp Gate](https://github.com/trioderegion/warpgate)  

**Compatibility:**
- [Sequencer](https://foundryvtt.com/packages/sequencer) (Enabling VFX)

**Description:**  
The first macro in a lot of things. Writing it was challenging but it seems to work reasonably well. Please report any bugs as usual.  
This macro allows players and GMs alike to shape change their characters into other creatures. It automatically shows those which are available and you can choose whether to change into a new form or back to your regular form. [Warp Gate](https://github.com/trioderegion/warpgate) by honeybadger is required to exchange the token on the canvas, so you can't access it without it. The macro will carry over every values that are required, including wounds, fatigue, conviction, power points, etc. Even on changing back all those values will be updated. The macro should relly take care of everything for you.  
There is some setup to be done however: First head to the compendiums and locate the "SWIM Shape Change Folders" compendium. Open it and import the folder structure into your world. *Do not change the folders names!* Inside the folder structure you'll find sub-folders. You now need to populate these folders with the creatures a chape changer can change into. You don't need to edit any of their settings, the macro will take care of everything. It is recommended that you rename these to avoid confusion with other actors however. I recommend adding a simple "SC: " in front of their names, e.g. "SC: Wolf". Also you might want to delete all the powers the creature might have because as of version 0.13.0, the macro does not delete those (yet). *Make sure to set permission to limited or observer on these actors for all players that are shape shifters!* (Do *not* make the players owner on these, the function will handle that. If all shape shifters have owner permission on the templates, bad things could happen.) And that is everything.  

**How does it work?**
The macro will search this folder structure for your presets and add them to the list of creatures a shape changer can change into. It then will create a duplicate of the selected actor and uses that duplicate for this specific player. It then will change the actor according to the rules. It will change the skills, attributes, token settings, wounds, fatigue, and much more. It even activates conviction if it was currently running on the shape changer.  
*Why not creating the folder structure automatically on first starting the world?* - Shape Change isn't the most common power in my experience, thus I don't want to force it on GMs who have no need for it.  
Here is a short video that showcases the macro (visual effect by JB2A, not included in SWIM):  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/shape_changer_showcase.gif?raw=true"> </p>  
(Assets used in the scene are from ForgottenAdventures and PEG Inc. and not part of SWIM.)  

### Mighty Summoner    
**Immersion setting:** SFX & VFX
**Requirements:**  
- [Warp Gate](https://github.com/trioderegion/warpgate)  

**Compatibility:**
- [Sequencer](https://foundryvtt.com/packages/sequencer) (Enabling VFX)

**Description:**  
The Mighty Summoner allows players to summon creatures to the canvas.  
First you need to import the `[SWIM] Summon Creature` folder structure from the actor compendium. In this folder you now place all the actors your players shall be able to summon. You may sort them to the rank folders but that is not necessary. Important is that they are all in the `Summon Creature Presets` sub-folder of `[SWIM] Summon Creature` or the respective sub-folders of `Summon Creature Presets`.  
Now give the players which are able to summon creatures *at least* limited permission of the creatures. By doing this you can control who is able to summon which creature.  
That's basically everything. It uses the same VFX and SFX as the Shape Changer and Warp Gate handles the placement.  
   
**How does it work?**
The function will search the folder structure for your presets and add them to the list of creatures a summoner can summon. It then will give the player the selected creature attached to the mouse pointer. On click the player places the token on the canvas and give that player permission to control it. It does not create a new actor and thus is only available as a token on the canvas. The sheet can be accessed by double left clicking the token as usual.  
Caster and summoned creature will get an Active Effect. When the effect is removed on either, the summoned creature will be dismissed.
*Why not creating the folder structure automatically on first starting the world?* - Summon powers aren't the most common powers in my experience, especially not on lower ranks, thus I don't want to force it on GMs who have no need for it.  
Here is a short video that showcases the macro (visual effect by JB2A, not included in SWIM):  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/mighty_summoner_showcase.gif?raw=true"> </p> 
(Assets used in the scene are from ForgottenAdventures and PEG Inc. and not part of SWIM.)  

### Common Bond
**Requirements:** None.  
**Compatibility:**  
- [Dice So Nice](https://foundryvtt.com/packages/dice-so-nice/) for the Benny throw.

**Immersion setting:** None.  
**Description:**  
This will give one Benny from a token to another.  
Target the token you want to give the Benny to and select the token from which you want to give the Benny away. The latter needs to have the Common Bond Edge. You need owner permission on the selected token, you don't need owner Permission for the target however.  

### Combat Setup
**Requirements:** None.  
**Immersion setting:** Changing Playlists.  
**Description:**  
This feature is available from a new button (with the fist icon FVTT uses) in the token controls section on the left (only GMs can see it). The button adds all tokens of the current scene to the combat tracker and prompts a dialogue. The user then has the opportunity to group the tokens as needed. A click on the button of the dialogue starts the combat, draws cards for all combatants/groups and sets the turn to the highes initiative.  
Additionally, if configured and activated properly in the settings, the game will pause all current playlists and starts a defined combat playlist. This also works when setting up and starting a combat without the combat setup feature. It is possible to configure a folder with playlists that shall not be stopped (i.e. ambient playlists).  
When stopping (deleting) the combat, the game will automatically stop the combat playlist and resume playing any playlists which were playing before the combat.  

### Power Effect Builder
**Requirements:**  
- [Warp Gate](https://github.com/trioderegion/warpgate)  
- [SUCC](https://github.com/SalieriC/SUCC)  

**Immersion setting:** None atm.  
**Description:**  
An immensely powerful way of setting up Active Effects for the smite, darksight, arcane protection, burrow, damage field, protection, growth/shrink, deflection, sloth/speed, invisibility, confusion, beast friend and boost/lower powers (more to come) on multiple targets. It sets the AE up with the appropriate duration (also respecting the concentration edge if the caster (selected token) has it), end of turn message and so on.  
It makes use of the very powerfull API provided by [Warp Gate](https://github.com/trioderegion/warpgate) and [SUCC](https://github.com/SalieriC/SUCC) to apply the effect even on tokens the user doesn't have permission to edit. Make sure your SUCC and Warp Gate installations are up to date.  
**Please note:** To access some specific Features of the Power Effect Builder you need to make sure that all Powers have their original names at least together with their flavour names (i.e. "Deflecting Moonlight (Deflection)") otherwise the Power Effect Builder has no chance to find the power, which is important to set up maintenance modifiers and duration. **The duration for non-casters is always near infinite!** This is by design so that it only ends on the casters turn. If the power is not found on the caster the effect will get a proper duration however.  
<p align="center"> <img src="https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/power_effect_builder_showcase.gif?raw=true"> </p>  
(Assets used in the scene are from JB2A, ForgottenAdventures, The Elder Scrolls and Adellos and not part of SWIM.)  