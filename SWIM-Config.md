As of version 1.0.0, SWIM sports a menu for actors and items made possible by the awesome Loofou who put a lot of his free time and effort into making this dream of mine a reality. (Thank you so much Loofou! <3)  
The menu can be accessed using the SWIM button in the header of each actor and item:  
![swim config button](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/macros/ammo_mgm/ammo_item.png?raw=true)  
The config menu looks different depending on whether it's an actor or item.  

## Actor Config

![actor config](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/img/swim_config/actor_config.png?raw=true)  
Here you will find a lot of configuration options specific to actors.

- **Pronoun:** This is your actors pronoun. More Specifically [https://en.wikipedia.org/wiki/Pronoun#English_pronouns](the third person dependent possessive pronoun). For the most part you will probably want to enter "his" or "her" here. Occasionally you might want that actor to be addressed with another pronoun however and now you can. The default (if nothing is entered) will be "its". Please note that we do not want to ignore the convention of using "their" as a gender-neutral variant by doing this. We instead want to give you more options and this indeed takes more time and effort than usually would by using "their". I just feel it's wrong to address a pesky zombie, skeleton or orc with "their". In the end, this module is about immersion and I feel that using "their" would break my immersion. To make everything simpler and reducing the amount of prep-time I chose "its" instead and allowing to configure this the way you want.
- **Radiation Resistance:** This option is only available if you activate the *irradiated* status effect in the SWIM settings. It is a number that can increase or decrease the resistance of an actor against taking radiation in the Radiation Centre macro. This is likely only interesting for some very niche SaWo settings but *if* you need it, then it is there. (You can even make Hazmat Suits possible by giving them an AE altering `flags.swim.config.radRes`.)
- **SFX Configs**: Here you can set up various sound effects for your actor. These should all be rather self-explanatory. Most are rarely used while others are more frequent. The module will use the defaults from the SWIM Settings if left empty.
