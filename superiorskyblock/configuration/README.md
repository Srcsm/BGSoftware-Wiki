# Configuration
Here you can find all the information that is needed in order to configure the plugin.<br>
You can find all of the default configuration files [here](https://github.com/BG-Software-LLC/SuperiorSkyblock2/tree/master/src/main/resources).<br><br>


### Spawn Configuration:
In this section, you can configure all the settings related to the spawn location of the plugin.

**location:**<br>
This location will be used to teleport players (for example, after disbanding an island).<br>
Please note: You must have your spawn in a valid world, or the plugin will not function correctly.
 
**protection:**<br>
Add protection to the spawn area. This protection can be bypassed using `/is admin bypass`.<br>
When this option is disabled, the spawn won't be protected and you should use other plugins to do so.

**settings:**<br>
A list of settings that will be applied to the spawn area.<br>
For a list of settings, please check out the [settings tab](superiorskyblock/island-settings/).

**permissions:**<br>
A list of permissions that will be applied to the spawn area.<br>
For a list of permissions, please see the [Island Permissions](https://wiki.bg-software.com/#/superiorskyblock/island-permissions/) tab.

**world-border:**<br>
Set whether or not the world-border inside the spawn should be shown.

**size:**<br>
Set the *radius* of the spawn island.<br>
Your spawn size can be larger than your maximum island size, but keep in mind they will not overlap.

**players-damage:**<br>
Use this setting to determine whether or not players will receive damage while in the spawn area.<br><br>


### Roles Configuration:
In this section, you can customize everything related to the island roles.<br>
If you want to read more about island permissions, please check the [permissions tab](superiorskyblock/island-permissions/).<br>
Please note: Changing role names when data player data exists can cause many issues.

**guest:**<br>
The guest role is given to players that are not members of the island.<br>
By default, they don't have any permissions in the island.

**coop:**<br>
The coop role is given to players that are not members of the island, but need to have the same permissions as members have.<br>
This can be given to players using `/is coop`.

**ladder:**<br>
In this section, you configure all the roles that can be given to members, from the default one to the leader role.<br>
The default role has the weight of 0, and the leader role should have the highest weight.<br>
You must give weights in an increasing order, so the plugin will function as it should.<br>
The default example has 4 roles: Member, Moderator, Admin and Leader.<br>
Each role will inherit the permissions of the role weighted lower than it.<br><br>


### Useful Settings:
**max-island-size:**<br>
Set the max island size of islands. The distance between islands is 3 times this value.<br>
You cannot change this value when already having a database, to prevent issues with island calculations.
 
**default-island-size:**<br>
 The default size islands will have. This size is the amount of blocks from the center to the border.

**stacked-blocks:**<br>
This feature brings the ability to stack blocks together into a single block.<br>
The stacked blocks are counted the same towards island top.<br>
You can choose to set limits, disable worlds, whitelist blocks or disable this altogether.
 
**island-level-formula:**<br>
This formula is used to calculate an islands worth into levels.<br>
If you would like to disable this feature and only use levels, set this to '0'.<br>
Please note: If a block has a level value, the formula will not be used for that block.

**island-top-order:**<br>
The default sorting algorithm to be used when opening the top islands menu.

**default-containers:**<br>
Instead of having to place items in a chest for each schematic, you can set default chest contents in this section.<br>
Please note: It will only be applied to schematics created using the plugin, and not WorldEdit.<br>
For more about schematics, please check the [schematics tab](superiorskyblock/schematics).

**default-signs:**<br>
This feature can be used to make a default sign for new islands.<br>
You will need to place a sign, and use the placeholders `{player}  {island}`.

**default-toggled-panel:**<br>
This option allows you to control the behaviour of the `/is panel`.<br>
To have the island panel open with only the `/is` command, set this option to 'true'.

**negative-worth:** + **negative-value:**<br>
Should your island worth/value be allowed to be a negative number?<br>
Set this to false if you don't want to allow negative island worth/value.


There are many more cool features in the config you can check out.<br>
Every section in the config is commented to ensure you get all the information about all the sections.
