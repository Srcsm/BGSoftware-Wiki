# Missions
Using missions, you can give your players tasks to do on your server.<br>
In this documantation, you will understand how to edit them to your own style!<br>

### How do missions work?
First of all, it's important to understand how missions work.
Missions are instructions that given to external jars (similar to plugins). The jars handle the events and actions that player do,<br>
and by following the instructions that are given to them, they know how to reward the players or islands.<br>
SuperiorSkyblock provides default jars that know how to handle a large range of actions, such as<br>
block breaking, island actions, enchanting, collection of items and crafting of items.<br><br>
There are some sections that can be applied to all the missions:<br>
<u>required-missions</u>: A list of missions that must be completed before completion of the mission.<br>
<u>required-checks</u>: A list of checks which depend on placeholders that needs to be checked before completion of the mission.<br>
<u>only-show-if-required-completed</u>: Whether or not the mission should only be shown in menus when the required missions & checks are completed.<br>
<u>island</u>: Whether or not the mission should be an islands mission (mission that is synced with all island members).<br>
<u>auto-reward</u>: Whether or not the plugin should reward the players without them doing it in the missions menu.<br>
<u>disband-reset</u>: Whether or not the mission should be reset when disbanding the island (used for player-missions).<br>
<u>reset-amount</u>: The amount of times a mission can be completed.<br>
<u>rewards.items</u>: A list of items that will be given to players when they complete the mission.<br>
<u>rewards.commands</u>: A list of commands that will be executed when players complete the mission.<br>
<u>icons.not-completed</u>: The item that will be shown in the menu when the mission is not completed.<br>
<u>icons.can-complete</u>: The item that will be shown in the menu when the mission can be completed.<br>
<u>icons.completed</u>: The item that will be shown in the menu when the mission is completed.<br>

### Default Mission Jars
Here you can find information about every default mission jar.<br><br>
<u>BlocksMissions.jar</u><br>
This jar knows to handle break of blocks by players. You can track break of blocks using this one.<br>
The jar has some custom instructions that can be given to it:<br>
required-blocks: A list of blocks that are needed to be broken.<br>
only-natural-blocks: Whether or not the mission will work only on natural blocks.<br>
blocks-placement: Whether or not the mission should listen to block placements.<br>
blocks-replace: Whether or not the mission should check if the block was placed before.<br><br>
<u>CraftingMissions.jar</u><br>
This jar knows to handle crafting of items. You can track crafting of items using this one.<br>
The jar needs one instruction so it can work:<br>
craftings: A list of items that are needed to be crafted.<br><br>
<u>EnchantingMissions.jar</u><br>
This jar knows to handle enchanting of items. You can track enchanting of items using this one.<br>
The jar needs one instruction so it can work:<br>
required-enchants: A list of enchants that needs to be applied on items.<br><br>
<u>IslandMissions.jar</u><br>
This jar knows to handle actions that are done in islands. You can track them using this one.<br>
The jar has some custom instructions that can be given to it:<br>
events: A list of events that needs to be listened to. You can add the suffix "-target" to tell the plugin to check only when the player is the target of the action.<br>
success-check: A check that will be run on the event. Coding knowledge is required to use this section.<br><br>
<u>ItemsMissions.jar</u><br>
This jar knows to handle collected items by players. You can track collected items using this one.<br>
The jar needs one instruction so it can work:<br>
required-items: A list of items that are needed to be collected.<br><br>
<u>KillsMissions.jar</u><br>
This jar knows to handle killing of entities. You can track killed entities using this one.<br>
The jar has some custom instructions that can be given to it:<br>
required-entities: A list of entities that are needed to be killed.<br>
reset-after-finish: Whether or not the killing counter should get reset after completing the mission.<br>