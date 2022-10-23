# Acknowledgement  
This macro is actually several scripts with one goal: To completely overhaul the ammo usage of the core system by introducing new features, a way to handle grenades and other consumable weapons, sound effects and more. It even supports ammo for melee weapons.  
Please read this wiki page carefully to get an idea of the features and how they work.  

## Current Features:
- Reduces amount of current `Shots` in the weapon, d'oh!.  
- Does not need to be set up for each weapon, one macro to rule them all.  
- Reloads a weapon at will.  
- - Supports different kinds of ammo (i.e. "Bullets, Large"; "Bullets, Large (AP)"; "Bullets, Large (Hollow Point)" and so on).  
- - Stores information about currently loaded ammo in the weapons SWIM config (see below).  
- - Supports reloading the weapon with another kind of ammo at will (will give back the remaining ammo in the weapon).  
- - Ammo must be set up as a `gear` type item (consumable is not supported atm).
- - Using the last amount of the ammo item will **not** delete the item from the inventory because one might want to swap ammo later.  
- - Offers a way to only load a single bullet instead of the entire weapon (i.e. for revolvers). There is a module setting to make this the default behaviour.  
- Supports weapons that do not require a reload action (i.e. bows).  
- - Such weapons must be marked (system offers this by default).
- - Such weapon *must not* have Shots of anything other than `0`. So put `0` in both Shots fields on the weapon.  
- - Such weapons use the ammo from the inventory instead of the one on the weapon.  
- - The Ammo Management macro will always use the ammo given in the selection of the dialogue.  
- - Since BR2 does not open the dialogue, the BR2 integration *requires* the user to set up the `Loaded Ammo` config (see below). The macro will then always use the ammo which is present in this field. For changing ammo just use the reload option of the Ammo Management macro and it'll set up the chosen ammo in that field without doing anything else.  
- Support for `Charge Packs` (i.e. batteries, gas tanks, ghost rock, magazines etc.):  
- - One `Charge Pack` will reload all current `Shots` in a weapon.  
- - Remaining `Shots` on weapons are lost upon reloading with a `Charge Pack`.  
- - If you change from one `Charge Pack` to another (for changing ammo types), it only refills the old ammo if the current shots are equal to the maximum shots in the weapon, otherwise remaining shots are lost as there is no way to track remaining shots on Charge Packs. This makes it somewhat possible to use Charge Packs as magazines but Players will then always *throw away* magazines which are not full. This is very unlikely to be ever changed as it would conflict with the way Charge Packs were intended (they shall always reload the entire weapon, no matter the max charges of a weapon, so storing remaining charges on Charge Packs is not an option).  
- - `Charge Pack` ammo will always overwrite the single bullet reload (see above) as they are intended to always reload the entire *magazine*.  
- Support for `Consumable Weapons` (i.e. throwing knives, grenades, Spears, etc.).  
- - The Macro will ignore current and maximum `Shots` on `Consumable Weapons` and instead uses their `Quantity` as a measurement of how many are left.  
- - Using the last `Consumable Weapon` will delete the item from the inventory. (Disabled in BR2 integration because that breaks rerolls.)
- - BR2 integration only: Also supports weapons which can be thrown but don't need to. Currently it checks for "Athletics", "Athletics (Throwing)", "Athletics (Explosives)" and  "Throwing" and assumes that consumable weapons always use either. If a consumable weapon does not use any of these skills, the macro stops. If an action is used in BRSW (see below) that initiates a roll with one of these skills, the macro continues as usual.
- Extensive support for Sound Effects (sfx), the following sfx can be configured:  
- - Reload sfx.  
- - Shooting/using sfx.  
- - Autofire sfx.  
- - Silenced shooting sfx.  
- - Silenced autofire sfx.  
- - Empty sfx (when the current `shots` are exactly zero).  
- - For bursts (expended shots less than 5) the macro will play the shooting SFX multiple times.  
- Each sfx can be set up individually for each weapon.  
- Optional integration for [Better Rolls (BRSW)](https://foundryvtt.com/packages/betterrolls-swade2).
- Game setting, allowing GMs to rule that NPCs do not use Ammo items from inventory. NPCs will still use Ammo in the weapon (magazines, clips, etc.) but won't require an item to draw ammo from. Instead they will just reload the weapon to the maximum shots (or by 1 shot if "Single Reload" is checked) without using an item from the inventory. This is especially useful for official modules which do not populate actors with ammunition, making prep for SWIM compatibility a little easier.  

# SWIM Config  
As of SWIM version 1, no more additional stats are needed. Instead SWIM offers a config window accessed by the SWIM button in the header of an item:  
![SWIM Weapon Config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/weapon_config.png?raw=true)

## Weapon Configuration Options  
You have several options here, first some general options:  
![General Weapon Config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/weapon_config_general.png?raw=true)  
These are the general configuration options.  
- **Loaded Ammo** is not needed to be changed unless the players purchase the weapon already loaded. In which case you can enter the correct ammo it comes with here. Otherwise the Ammo Management macro will update this on each reload when the loaded ammo is changed.
- **Suppressed (Silenced)** means that the weapon has a suppressor attached. This can be changed on-the-fly and will affect the used Sound Effect. It currently has no mechanical influence on the game, it's just for immersion.
- **Consumable Weapon** is a setting to mark a weapon as consumable. This means that the weapon doesn't use ammunition but *is* the ammo itself so to speak. This is the correct setting for grenades, molotov cocktails, throwing knives and the like. If checked the weapon will not use any ammo (in fact current and max shots have to be `0`), instead it reduces its quantity.  
Now, you also have several sound effect (SFX) options as well:  
![Wapon SFX Config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/weapon_config_sfx.png?raw=true)  
These sound effects are already explained under "Current Features" above but should also be rather self-explainatory.  
Don't forget to save when you're done!  

## Ammo Configuration Options  
Ammunition has config options as well. These are shown on each item as every item can be used as ammo (except consumables, don't use these as ammo for now). You can access the options in the same way as on weapons:  
![Ammo SWIM Config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/ammo_item.png?raw=true)  
And here are the options available:  
![Ammo config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/ammo_item_config.png?raw=true)  
- **Charge Pack** marks an item as a kind of container for ammo. These might just be a full magazine or a battery or something similar. Charge Packs will always reload a weapon entirely, no matter how many max shots a weapon has.  
- **Set Ammo ActiveEffect** allows you to assign an active effect to a weapon. Due to core limitations, this option is only available for items in the sidebar or inside a compendium. More detailed instructions on how that works and what it does you can find below.  

# Ammunition  
The core system currently supports this stat on a weapon but unfortunately it is not shown until you activate the ammo management of the system. But we want to not use the systems default ammo management. I've created a request to also show it when ammo management is disabled. For now we need a workaround though. Fortunately, there is one:  

## Setting up ammunition  
Each weapon has an ammo field provided by the system (found under the "Properties" tab. In SWADE this can only be populated with a single item name. SWIM changes that. You can still use it as in the system or take it one step further by using pipe (`|`) as separator. This means that you can assign a wide variety of ammunition.  
Let's say your Weapon is supposed to accept the item "Bullets, pistol" as ammo. But there is also "Bullets, pistol (armor piercing)" and "Bullets, pistol (hollow point)". That's easy to achieve in SWIM, just set the ammo on the weapon as this:  
`Bullets, pistol|Bullets, pistol (armor piercing)|Bullets, pistol (hollow point)`  
Make sure that you enter the names of your ammo items exactly as they are, otherwise it won't work.  

## Enabling NPC ammo item usage  
As of version 0.12.0, the macro supports a way to allow NPCs to fully use the ammo management even if they don't have items representing their spare shots, magazines and the like. The NPCs will still use the ammo that is in the weapon but won't require said ammo item anymore. Weapons that don't require a reloading action (i.e. bows) will just fire infinitely, other wepons (i.e. all weapons with a magazine) will fire until their current shots are at 0 and then need to be reloaded using the Ammo Management macro as usual. But their ammo to reload is infinite.   
This is now the default behaviour. To activate the former behaviour (NPCs need ammo items in their inventory), just head to the SWIM module settings and activate it.  

# Better Rolls integration  
If you're using Better Rolls for SWADE (BRSW), there is a way to fully automate the Shooting part of the macro. Each skill roll from the weapon will then execute the macro, play the sfx (if set up) and use the ammo properly. To set this up you need to set it as a "runSkillMacro" [Global Action](https://github.com/javierriveracastro/betteroll-swade/wiki/Global-Actions) in Better Rolls. This is not as difficult as you might think:  
1. Import the macro `SWIM: Ammo usage` from the compendium into your world.  
2. Head over to your module settings and click on "World Global actions" in the BR2 settings.  
3. Click "New action".  
4. Paste the code from [this file](https://raw.githubusercontent.com/SalieriC/SWADE-Immersive-Macros/main/swim/assets/imports/BR2-shooting-integration.json) into the text box.  
5. Save.   

Before using this though, *make sure to disable the ammo management by BR2*.  
That is all there is to it. Now, whenever a *Shooting*, *Athletics* or *Untrained* roll is initiated from a weapon card, the macro will execute and - if it detects circumstances which require it to do its thing - uses the ammo.  

## Disabling the BRSW integrated ammo management button  
This is a bonus for any overachiever out there. This can't be done manually and requires a little bit of coding.  
1. Locate your `betterrolls-swade2` folder in your foundry `data/modules` folder.  
2. Open the `templates` folder and locate the `item_card.html`.  
3. Open it with a decent text editor. Notepad++ works but any IDE (if you have one) works better.  
4. Replace `{{# if ammo }}<div class="brws-attribute-buttons">` with `<!--{{# if ammo }}<div class="brws-attribute-buttons">`.  
6. Replace `</div>{{/if}}` nine lines below with `</div>{{/if}}-->`.  

This will disable the ammo management button from BR2 in the item cards, preventing your players from accidentally using it.   
The macro supports a workaround for ranged weapons used in melee (i.e. a javelin used as a spear) by filtering for the used skill. Not a perfect solution but the best that is possible yet.  

# Active Effects from Ammo  
Okay so you have set your "Bullets, pistol (armor piercing)" set as available ammo on your weapon but it doesn't do anything. SWIM has got you covered. As of SWIM v.1.0.0 you can assign Active Effects to your ammo items. Just open the config of your ammo as shown above. You'll find a config option for Active Effects. This is only available for items in the sidebar or a compendium. Due to core limitations you can't do this for items already on an actors sheet.  
This option will open up an active effect dialogue window you should be familiar with. This can be edited to your liking. Here is an example for armor piercing ammo:  
![Ammo AE Config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/ammo_item_config_effect.png?raw=true)
You can change virtually any setting of a weapon using this. Please note that you **must not use the `@Weapon{WeaponName}[PropertyPath]` notation from the SWADE system here**. Instead you enter a property path directly as if you were editing an actor using an AE. In the above example this is `system.ap` for the armor piercing property of a weapon.*  
Now that this is done (don't forget to save!), you are ready to go. When dropping the ammo on an actor nothing will happen besides the item being added. But once you load this ammo into a weapon, the configured Active Effect is immediately added to the actor and changed to affect the exact weapon it is loaded in:  
![Ammo AE added](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/ammo_mgm_loaded_effect.png?raw=true)  
This is also the reason you must not add the notation to affect items as shown above. The Ammo Management will use the weapons name and set you up.  
When you change the loaded ammo, the AE is immediately removed.  
  
`*` The most frequently used property is likely `system.ap` to change armor penetration of a weapon. To find other paths you can always ask in the Foundry Discord SWADE channel or if you are a dev just use the console to get a weapon item to figure out the property path you need.  