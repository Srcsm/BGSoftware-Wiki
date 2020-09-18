# Menus
Menus (guis) are used in the plugin in many cases, and they are all fully customizable.<br>
In this documantation, you will understand how to edit them to your own style!<br>
Menus also support placeholders!<br>

### Editing your first menu
<div style="margin-top: -10px;">All the menus follow the same concept, but some of them have some changes.<br>
Here we will go through all the basic sections, that every menu has / can have.<br><br>
<u>title</u>: The title of the menu.<br>
<u>type</u>: The type of the menu. Can be HOPPER or CHEST.<br>
<u>pattern</u>: The pattern of the menu. This section is basically the layout of the menu.<br>
Every line represents a line in the menu, and every char represents an item (besides spaces).<br>
<u>items</u>: A section that contains all the chars from the pattern. Every char should have a child-section under this section,<br>
with the item that you want to have in the place where the char is. If the char doesn't have a child-section, the slot will be empty.<br>
<u>sounds</u>: A section that holds all sounds for all the chars. This section is not required and can be deleted if wanted.<br>
Every char you want to play sounds, needs to be under this section, and must follow the sounds format (type section (String), volume section (Double) and pitch section (Double)).<br>
<u>commands</u>: A section that holds all the commands for all the chars. This section is not required and can be deleted if wanted.<br>
Every char you want to run commands, needs to be under this section, and be a list of commands (without slash).<br>
If you want the command to be executed by the player, add "PLAYER:" at the start of the line.

An example can be seen here:
![Menu Example](https://bg-software.com/imgs/menu-example2.png)<br></div>

### Items Section
<div style="margin-top: -10px;">This section holds all the items. Every item should follow the following format:<br>
<u>type</u>: The material type of the item. Required for every item.<br>
<u>data</u>: The data value of the item. Only used in legacy versions.<br>
<u>name</u>: A custom name for your item. Supports color codes.<br>
<u>lore</u>: A list of lines that will be used as the item's lore. Supports color codes.<br>
<u>enchants</u>: A section that holds all enchants. Keys are enchantment names, and their values are the enchantment levels.<br>
<u>glow</u>: A boolean to set a glowing enchantment to the item (no enchantment name in the lore).<br>
<u>flags</u>: A list of item flags that will be added to the item.<br>
<u>skull</u>: A texture value to give to the item if it's a skull.<br>
<u>unbreakable</u>: Should the item have spigot's unbreakable tag?<br>
<u>effects</u>: A section that holds all potion effects. Keys are effect names, and their values are sections with the following keys:<br>
&ensp;&ensp;&ensp;&ensp;<u>duration</u>: The duration of the potion effect.<br>
&ensp;&ensp;&ensp;&ensp;<u>amplifier</u>: The level of the potion effect.<br></div>

### Sounds Section
<div style="margin-top: -10px;">This section holds all the sounds. Every sound should follow the following format:<br>
<u>type</u>: The bukkit-sound type. Required for every sound.<br>
<u>volume</u>: The volume of the sound. Required for every sound.<br>
<u>pitch</u>: The pitch of the sound. Required for every sound.<br></div>

### Commands Section
<div style="margin-top: -10px;">This section holds all the commands. Every command should be a list of strings.<br>
Every line represents a command, and must not contain the slash at the start.<br>
If you want the player to execute the command (and not console), add "PLAYER:" at the start of the line.<br></div>

### Permissions Section
<div style="margin-top: -10px;">This section holds all the permissions for items. Every permission should follow the following format:<br>
<u>permissions.&#60;ch>.permission</u>: The required permission for the player.<br>
<u>permissions.&#60;ch>.no-access-sound</u>: The sound that will be played when the player permission doesn't have the permission to use the item.<br>
&ensp;&ensp;&ensp;&ensp;The sound section should follow the sounds format.

### Common Sections
<div style="margin-top: -10px;">Here's a list of common sections that many menus can have.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br>
<u>back</u>: Set the char of the back button. Unlike previous page, this will open the menu before this one.<br></div>

### Biomes Menu
<div style="margin-top: -10px;"><u>items</u>: Besides the regular items, you can add items that will be represented as biome buttons.<br>
These items have some additional sections:<br>
<u>biome</u>: '' - The biome that is assigned to the button.<br>
<u>access</u>: - The item that will be displayed if there's access to the biome. Should follow the items format.<br>
<u>no-access</u>: - The item that will be displayed if there's no access to the biome. Should follow the items format.<br>
<u>sounds</u>: Sounds of the biome button should follow the following format:<br>
&ensp;&ensp;&ensp;&ensp;<u>access</u>: - The sound that will be played if there's access to the biome. Should follow the sounds format.<br>
&ensp;&ensp;&ensp;&ensp;<u>no-access</u>: - The sound that will be played if there's no access to the biome. Should follow the sounds format.<br></div>

### Border Color Menu
<div style="margin-top: -10px;"><u>green-color</u>: Set the char of the green-color button.<br>
<u>red-color</u>: Set the char of the red-color button.<br>
<u>blue-color</u>: Set the char of the blue-color button.<br></div>

### Confirm Disband Menu
<div style="margin-top: -10px;"><u>confirm</u>: Set the char of the confirm button.<br>
<u>cancel</u>: Set the char of the cancel button.<br></div>

### Control Panel Menu
<div style="margin-top: -10px;"><u>members</u>: Set the char of the members button.<br>
<u>settings</u>: Set the char of the settings button.<br>
<u>visitors</u>: Set the char of the visitors button.<br></div>

### Global Warps Menu
<div style="margin-top: -10px;"><u>warps</u>: Set the char of the warp buttons.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br>
<u>visitor-warps</u>: A boolean to replace warps with visitor locations. Only islands that have their visitor location set, will be shown.<br></div>

### Island Creation Menu
<div style="margin-top: -10px;"><u>items</u>: Besides the regular items, you can add items that will be represented as schematic buttons.<br>
These items have some additional sections:<br>
<u>schematic</u>: '' - The schematic that will be placed when a new island is created.<br>
<u>required-permission</u>: '' - The required permission for using the schematic.<br>
<u>biome</u>: '' - The biome that will be set to the new island.<br>
<u>access</u>: - The item that will be displayed if there's access to use the schematic. Should follow the items format.<br>
<u>no-access</u>: - The item that will be displayed if there's no access to use the schematic. Should follow the items format.<br></div>

### Island Missions Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the mission buttons.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br>
<u>sounds</u>: Sounds of mission items should be in the following format:<br>
&ensp;&ensp;&ensp;&ensp;<u>completed</u>: - The sound that will be played when the mission was already completed.<br>
&ensp;&ensp;&ensp;&ensp;<u>not-completed</u>: - The sound that will be played when the mission cannot be completed.<br>
&ensp;&ensp;&ensp;&ensp;<u>can-complete</u>: - The sound that will be played when the mission can be completed.<br></div>

### Island Rate Menu
<div style="margin-top: -10px;"><u>zero-stars</u>: Set the char of the zero stars button.<br>
<u>one-star</u>: Set the char of the one star button.<br>
<u>two-stars</u>: Set the char of the two stars button.<br>
<u>three-stars</u>: Set the char of the three stars button.<br>
<u>four-stars</u>: Set the char of the four stars button.<br>
<u>five-stars</u>: Set the char of the five stars button.<br></div>

### Island Ratings Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the rating items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br></div>

### Member Manage Menu
<div style="margin-top: -10px;"><u>roles</u>: Set the char of the roles button.<br>
<u>ban</u>: Set the char of the ban button.<br>
<u>kick</u>: Set the char of the kick button.<br></div>

### Member Role Menu
<div style="margin-top: -10px;"><u>items</u>: Besides the regular items, you can add items that will be represented as role buttons.<br>
You must give them the role key, which holds the name of the role as a value.<br></div>

### Members Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the member items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br></div>

### Missions Menu
<div style="margin-top: -10px;"><u>player-missions</u>: Set the char of the player-missions button.<br>
<u>island-missions</u>: Set the char of the island-missions button.<br></div>

### Permissions Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the permission items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br><br>
This menu has a section called "permissions". This section holds all the permissions that will be displayed in the menu.<br>
If a permissions is not in the menu, it won't be able to be changed by players.<br>
Every section should follow the following format:<br>
<u>permission-enabled</u>: - The item that will be displayed when the permission is enabled for the player.<br>
<u>permission-disabled</u>: - The item that will be displayed when the permission is disabled for the player.<br>
<u>role-permission</u>: - The item that will be displayed when opening the menu for a role.<br>
<u>has-access.sound</u>: - The sound that will be played if there's access to change the permission.<br>
<u>no-access.sound</u>: - The sound that will be played if there's no access to change the permission.<br></div>

### Player Language Menu
<div style="margin-top: -10px;"><u>items</u>: Besides the regular items, you can add items that will be represented as language buttons.<br>
You must give them the language key, which holds the language formatted name as a value.<br></div>

### Player Missions Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the mission buttons.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br>
<u>sounds</u>: Sounds of mission items should be in the following format:<br>
&ensp;&ensp;&ensp;&ensp;<u>completed</u>: - The sound that will be played when the mission was already completed.<br>
&ensp;&ensp;&ensp;&ensp;<u>not-completed</u>: - The sound that will be played when the mission cannot be completed.<br>
&ensp;&ensp;&ensp;&ensp;<u>can-complete</u>: - The sound that will be played when the mission can be completed.<br></div>

### Settings Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the settings items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br><br>
This menu has a section called "settings". This section holds all the settings that will be displayed in the menu.<br>
If a settings item is not in the menu, it won't be able to be changed by players.<br>
Every section should follow the following format:<br>
<u>settings-enabled</u>: - The item that will be displayed when the settings is enabled for the island.<br>
<u>settings-disabled</u>: - The item that will be displayed when the settings is disabled for the island.<br>
<u>sound</u>: - The sound that will be played when clicking the item.<br></div>

### Top Islands Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the island items.<br>
<u>worth-sort</u>: Set the char of the worth-sort button.<br>
<u>level-sort</u>: Set the char of the level-sort button.<br>
<u>rating-sort</u>: Set the char of the rating-sort button.<br>
<u>players-sort</u>: Set the char of the players-sort button.<br>
<u>player-island</u>: Set the char of the player-island item.<br>
<u>sort-glow-when-selected</u>: A boolean to set sorting buttons glowing when selecting them.<br><br>
The formatting of the island item is different, and is the following:<br>
<u>island</u>: - The item that will be displayed if an island exists for the place.<br>
<u>no-island</u>: - The item that will be displayed if an island doesn't exist for the place.<br></div>

### Unique Visitors Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the visitor items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br></div>

### Upgrades Menu
<div style="margin-top: -10px;">This menu has a section called "upgrades". This section holds all the upgrade items.<br>
The child-section name is the name of the upgrade. Every section should be in the following format:<br>
<u>item</u>: - The char of that upgrade.<br>
<u>'<#>'</u>: - The item of the upgrade level <#>.<br>
<u>'<#>'.has-next-level</u>: - The item that will be displayed if the player can level-up the upgrade.<br>
<u>'<#>'.no-next-level</u>: - The item that will be displayed if the player cannot level-up the upgrade.<br>
<u>'<#>'.has-next-level.sound</u>: - The sound that will be played if the player can level-up the upgrade.<br>
<u>'<#>'.no-next-level.sound</u>: - The sound that will be played if the player cannot level-up the upgrade.<br></div>

### Values Menu
<div style="margin-top: -10px;">Items that represent value items, should have the block section, that has the type that it counts as a value.<br></div>

### Visitors Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the visitor items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br></div>

### Warps Menu
<div style="margin-top: -10px;"><u>slots</u>: Set the char of the warp items.<br>
<u>previous-page</u>: Set the char of the previous-page button.<br>
<u>current-page</u>: Set the char of the current-page button.<br>
<u>next-page</u>: Set the char of the next-page button.<br></div>