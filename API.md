As of version 0.15.0 SWIM features an ever expanding API which allows users to make use of some of its functions. Especially worth mentioning being all the (former) macros SWIM had. These are now backed into the module directly and their functions are exposed, meaning you can access them in macros and your own module directly.  
All functions are asynchronous.  

## Helper Functions
Especially useful for macro and module devs may be the following helper functions:

### Get Macro Variables
Macros get a number of variables from FVTT core directly, namely `speaker`, `character`, `actor` and `token`. These are usually not available in other contexts however which is why SWIM offers a simple way to get them:  
`async swim.get_macro_variables()`  
Returns the four variables available in script macros. Best used like this:  
`const { speaker, character, actor, token } = await swim.get_macro_variables()`  

### Critfail Check
Checks if a roll made was a critical failure.  
`async swim.critFail_check(wildcard, roll)`
- `wildcard` {boolean}: Wild Card status of the character that made the roll. If `false` it will make another roll `1d6x` according to the SWADE core rules, if `true` the script will just compare the both dice.  
- `roll` {object}: The roll that was made and needs to be checked for a critfail.  
It returns `true` in case of a critfail or `false` if not.  
**Warning:** Currently doesn't support rolls with multiple trait dice. Feeling advantures? Make a Pull Request to fix it. =)  

### Get Benny Image
Returns the file path of the *back side* of the benny configured in the SWADE core settings.  
`async swim.get_benny_image()`

### Check Bennies
Checks the passed token for available Bennies.  
`async swim.check_bennies(token)`
- `token` {object}: The token you want to check for Bennies.  
Returns `{ tokenBennies, gmBennies, totalBennies }`.  
- `tokenBennies` {number}: The amount of Bennies the *token* has.  
- `gmBennies` {number}: The amount of Bennies the *GM* has, *if* the function is executed from a GMs account.  
- `totalBennies` {number}: The amount of Bennies the *player* has for that specific token (token Bennies + GM Bennies if executed by a GM).
It assumes that non Wild Cards have 0 Bennies and checks for `Luck` and `Great Luck` set up as Edges to apply additional Bennies. You have more Edges/Special Abilities that add Bennies? Create an issue and I'll include them.  

### Spend Benny
Checks for avvailable Bennies first (see above) and spends one if available. If the token has none and the player is a GM, it spends a GM Benny.  
`async swim.spend_benny(token, message)`  
- `token` {object}: The token for which a Benny shall be spent.  
- `message` {boolean}: If `true` a chat message will be created that notifies about the spent Benny.
Note that the game will show the benny flip if DiceSoNice! is active.  

### Is First GM
Checks whether or not the player in question is the first GM that is logged in and returns `true` if that is the case.  
`swim.is_first_gm()`  
This is especially useful for developers who want to relay some code to GMs to execute code that cannot be executed by player accounts (i.e. to alter actors the player does not own). The function effectively prevents execution of the code multiple times if more than one GM is logged in.  

### Wait
Wait a specified amount of *mili*seconds before executing the rest of the script. Especially useful for sound and video effects to not play at the same time. It *needs* to be awaited.  
`async swim.wait(ms)`  
- `ms` {number}: The amount of time to pause script execution in miliseconds.  
This is basically a planned delay in script execution. Use it responsibly, too large numbers can make one think your script is laggy.  

### Get official class
This returns the proper html div tag for the installed an active rules compendium module.  
`async swim.get_official_class()`  
It currently supports the Savage Worlds Pathfinder, Deadlands, Sprawlrunners and SWADE Core modules in this priority order. This means that the divider will be used whichever is first in the aformentioned list if multiple are activated. So if you were to use Deadlands and SWADE Core in your world, the function would return the Deadlands class.  

### Get Actor SFX
Gets and returns all the SFX file paths from an actor. Will return the default ones if the paths are not found or labeled `NULL` (*case sensitive*). (There currently only is a default one for becoming shaken, thus the other will returned as `undefined`.)  
`async swim.get_actor_sfx(actor)`  
- `actor` {object}: The actor on which to search the sfx file paths.  
Returns the four sfx file paths. Best used like this:  
`const { shakenSFX, deathSFX, unshakeSFX, soakSFX } = await swim.get_actor_sfx(actor)`  

### Play SFX
This just plays the sfx with the provided settings for everyone.  
`async swim.play_sfx(sfx, volume, playForAll)`  
- `sfx` {string}: The file path to the audio file.  
- `volume` {number}: The volume level on which to play the audio between 0 and 1. Will use default settings of SWIM if undefined.  
- `playForAll` {boolean}: Determines whether or not the SFX should be played for everyone (true) or just the current user (false). It defaults to true.

### Get Folder Content
This returns all contents of a folder and its sub-folders up to three layers deep, regardless of permission.  
`swim.get_folder_content(folderName)`  
- `folderName` {string}: A unique folder name.  

### Run Migration
This will run the migration of SWIM that changes items and actors to the new setup (converts additional stats to flags).  
`(async) swim.run_migration(actor, item)`  
- `actor` {object}: A swade actor, if you only have a token pass `token.actor`, the migration will then update the tokens actor *and* the actor it originated from as well as all their items. If you don't wish to migrate an actor pass it as a boolean and make it `false`.  
- `item` {object}: A swade item, the migration will then update the item *only* the actor remains unchanged. If you don't wish to migrate an item pass it as a boolean and make it `false`.  

## Feature Functions
The following functions present the core features of SWIM. They are probably less useful for macro and module devs but presented here anyway in case you want to utilise them.  
Note that all of them except the BR2 ones get the macro variables (see above) first, so they really only work on selected token(s). The BR2 ones need the BR2 variables passed to function.  

TBD.  