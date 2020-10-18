# Schematics
Schematics are used as a default building of islands (no one wants an empty world to play inside).<br>
There are three different schematics: normal ones, nether ones & end ones.<br>

### Creating your first schematic
Here you can find a tutorial for using the built-in system - which is very fast and done fully async to ensure no lag is occured.<br>
If you prefer to use WorldEdit schematics, please scroll down for the WorldEdit section.

First, toggle the schematic mode using /is admin schematic.<br>
Then, select two blocks using a golden axe, and stand where you want the teleport location to be.<br>
The last thing to do is to run /is admin schematic , which will create the schematic file for you.<br>
This task might be a bit slow, so don't do it while having many players online.<br>

**Creating a sign**:
To create a sign that will appear on the island - you have two options:<br>
1. You can create a sign when you create the schematic
2. You can place a sign on the island when you create a schematic and edit the `default-signs` option in the `config.yml`.

For both, you can use these variables:
* {player} - Island Owner's Name
* {island} - Island Name - If the island name does not exist, then it will default to the Island Owner's Name.

<video src="https://bg-software.com/imgs/schematics-creation.mp4" height="400px" autoplay loop></video>

### WorldEdit Schematics
WorldEdit schematics are supported, but you must have FastAsyncWorldEdit installed.<br>
Support for regular WorldEdit won't be added, as FAWE is the same but better in performance.<br>

### Adding your own schematics
In order to add schematics, you first need to move the schematic files into the schematics folder,<br>
that is located under the main plugin's folder. Make sure you use WorldEdit schematics or built-in schematics.

After doing so, allocate the island-creation menu file (can be found inside the menus folder), and open it.<br>
Add a new item to the items section, and add to it the following sections:<br>
<u>schematic</u>: '' - the name of the schematic file (without file extension)<br>
<u>required-permission</u>: '' - the permission that is required to use the schematic. By default it's ''.<br>
<u>biome</u>: '' - The biome that will be set for the island.<br>
<u>bonus-worth</u>: - The bonus that the island will get of worth once created.<br>
Can be negative to get the island start with a default worth of 0.<br>
<u>bonus-level</u>: - The bonus that the island will get of level once created.<br>
Can be negative to get the island start with a default level of 0.<br>
<u>offset</u>: - When enabled, created islands will have a worth & level values of 0.<br>
This function checks for the default worth of the island, and applies a negative worth bonus.<br>
<u>access</u>: - The item that will be displayed when having access to the schematic.<br>
<u>no-access</u>: - The item that will be displayed when not having access to the schematic.<br>
