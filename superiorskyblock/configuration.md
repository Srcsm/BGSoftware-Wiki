# Configuration
Here you can find all the information that is needed in order to configurate the plugin.<br><br>


### Spawn Configuration:
In this section, you can configure all the settings related to the spawn location of the plugin.

**location:**<br>
This location will be used to teleport players (for example, after disbanding an island).<br>
Please note: You must have your spawn in a valid world, or the plugin will not function correctly.
 
**protection:**<br>
Add protection to the spawn area. This protection can be bypassed using /is admin bypass.<br>
When the section is disabled, the spawn won't be protected and you should use other plugins to do so.

**settings:**<br>
A list of settings that will be applied to the spawn area.<br>
For a list of settings, please check out the [settings tab](superiorskyblock/island-settings).

**world-border:**<br>
Set whether or not the world-border inside the spawn should be shown.<br><br>


### Roles Configuration:
In this section, you can customize everything related to the island roles.<br>
If you want to read more about island permissions, please check the [permissions tab](superiorskyblock/island-permissions).<br>
Please note: changing role names when data exist can cause many issues.

**guest:**<br>
The guest role is given to players that are not members of the island.<br>
By default, they don't have any permissions in the island.

**coop:**<br>
The coop role is given to players that are not members of the island, but need to have the same permissions as members have.<br>
This can be given to players using /is coop.

**ladder:**<br>
In this section, you configure all the roles that can be given to members, from the default one to the leader role.<br>
The default role has the weight of 0, and the leader role should have the highest weight.<br>
You must give weights in an increasing order, so the plugin will function as it should.<br>
The default example has 4 roles: Member, Moderator, Admin and Leader.<br><br>


### Useful Settings:
**max-island-size:**<br>
Set the max island size of islands. The distance between islands is 3 times this value.<br>
You cannot change that value when having a database, to prevent issues with island calculations.
 
**default-island-size:**<br>
 The default size islands will have. This size is the amount of blocks from the center to the border.

**stacked-blocks:**<br>
This feature brings the ability to stack blocks together in a single block.<br>
The stacked blocks are counted the same towards island top.
 
**island-level-formula:**<br>
This formula is used to convert worth value into levels.<br>
Please note: If a block has a level value, the formula will not be used for that block.

**island-top-order:**<br>
The default sorting algorithm to be used when opening the top islands menu.<br>
Please note: If a block has a level value, the formula will not be used for that block.

**starter-chest:**<br>
Instead of having contents in the schematic, you can set all the chest contents in this section.<br>
Please note: It will only be applied to schematics created using the plugin, and not WorldEdit.<br>
For more about schematics, please check the [schematics tab](superiorskyblock/schematics).<br><br>


There are many more cool features in the config you can check out.<br>
Every section in the config is commented to ensure you get all the information about all the sections.