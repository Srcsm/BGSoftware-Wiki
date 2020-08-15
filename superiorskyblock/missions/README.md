# Missions
Using missions, you can give your players tasks to do on your server.<br>
In this documantation, you will understand how to edit them to your own style!<br>

### How do missions work?
First of all, it's important to understand how missions work.
Missions are instructions that given to external jars (similar to plugins). The jars handle the events and actions that player do,<br>
and by following the instructions that are given to them, they know how to reward the players or islands.<br>
SuperiorSkyblock provides default jars that know how to handle a large range of actions, such as<br>
block breaking, island actions, enchanting, collection of items and crafting of items.<br><br>

### Default mission jars
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

### Customize your first mission
Here you'll understand how to customize your own mission.<br>
All the missions have the follow the same concept, but in this tutorial I chose to customize my own lumberjack mission!<br><br>
I first start with setting basic information (name & mission type):<br>
```yaml
lumberjack:
  mission-file: BlocksMissions    # I am using the BlocksMissions jar as it knows how to handle block breaking.
```
After that, I start giving it some more advanced settings. I want my players to only gain progress from natural blocks spawning,<br>
I want the mission to be reset upon disbanding of an island, and I want them to be able to use the mission if they are above island level of 250.<br>
```yaml
lumberjack:
  mission-file: BlocksMissions

  only-natural-blocks: true             # Make sure only natural blocks are counted.
  disband-reset: true                   # Resetting the mission upon island disband.
  required-checks:                      # Handles custom checks, such as minimum level requirement.
    - '%superior_island_level% > 250'
```
Now, I will configure three important things:<br>
1. The blocks that will be tracked (I am using 1.16 blocks).
2. Rewards for the mission
3. The icon of the mission that will be displayed in /is missions.
```yaml
lumberjack:
  mission-file: BlocksMissions

  only-natural-blocks: true
  disband-reset: true
  required-checks:
    - '%superior_island_level% > 250'
  
  # The blocks that will be tracked.
  required-blocks:
    # A section of blocks. All the blocks in a section will be counted together.
    '1':
      # All the blocks of this section.
      types:
        - 'OAK_LOG'
        - 'SPRUCE_LOG'
        - 'BIRCH_LOG'
        - 'JUNGLE_LOG'
        - 'ACACIA_LOG'
        - 'DARK_OAK_LOG'
      # The total amount of all the blocks of the section (5 stacks).
      amount: 320
  
  # The rewards of the mission.
  rewards:
    items:
      '1':                  # Random section name, doesn't really matter.
        type: OAK_SAPLING   # The item's type
        amount: 16          # The item's amount.
    commands:               # Commands that will be executed upon completion.
      - 'is admin msg %player% &e&lMission | &7Successfully finished the mission Lumberjack!'
  
  # Settings related to the icon in the missions menu.
  icons:
    # The icon that will be displayed when the player cannot complete the mission for any reason.
    not-completed:
      type: PAPER
      name: '&aLumberjack'
      lore:
        - '&7Cut 320 logs.'
        - ''
        - '&6Required Materials:'
        - '&8 - &7x320 Logs'
        - ''
        - '&6Rewards:'
        - '&8 - &7x16 Oak Saplings'
        - ''
        - '&6Cut Logs: &7{1}/320'
        - '&6Progress: &7{0}%'
        - '&c&l ✘ &7Not Completed'
    # The icon that will be displayed when the player can complete the mission.
    can-complete:
      type: PAPER
      name: '&aLumberjack'
      lore:
        - '&7Cut 320 logs.'
        - ''
        - '&6Required Materials:'
        - '&8 - &7x320 Logs'
        - ''
        - '&6Rewards:'
        - '&8 - &7x16 Oak Saplings'
        - ''
        - '&6Cut Logs: &7320/320'
        - '&6Progress: &7100%'
        - '&a&l ✔ &7Click to redeem your reward.'
      enchants:
        DURABILITY: 1
      flags:
        - HIDE_ENCHANTS
    # The icon that will be displayed when the player has already completed the mission.
    completed:
      type: MAP
      name: '&aLumberjack'
      lore:
        - '&7Cut 320 logs.'
        - ''
        - '&6Cut Logs: &7320/320'
        - '&6Progress: &7100%'
        - '&a&l ✔ &7Already Claimed.'
```
As you might have noticed, I used some built-in placeholders, such as {0} and {1}.<br>
<u>{0}</u> - Used as a percentage placeholder.<br>
<u>{1}</u> - Used as a placeholder for the amount of tracked blocks.<br>
<u>{value_\<block>}</u> - Used as a placeholder for the amount of a specific tracked block.<br>
<u>{percentage_\<block>}</u> - Used as a percentage placeholder for a specific block.<br><br>
That's it! The mission is now setup and ready to be used.<br>
There are more settings that can be applied to all the missions:<br>
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

### Create your own mission jar
In order to create your own missions jar, you must have knowledge in Java and the Spigot API.<br>
Mission jars are part of the SuperiorSkyblock's API, which can be found [here](https://github.com/OmerBenGera/SuperiorSkyblockAPI).<br><br>
In this tutorial, I will make a chat-mission that counts the amount of times a player has written "Hello".<br>
First, I create a ChatMission object that extends the Mission object, and override all the methods.<br>
```js
public final class ChatMission extends Mission<Object> {

    @Override
    public void load(JavaPlugin plugin, ConfigurationSection section) throws MissionLoadException {

    }

    @Override
    public double getProgress(SuperiorPlayer superiorPlayer) {
        return 0;
    }

    @Override
    public void onComplete(SuperiorPlayer superiorPlayer) {

    }

    @Override
    public void onCompleteFail(SuperiorPlayer superiorPlayer) {

    }

}
```
As you can see, the Mission object needs an argument. This argument will be our data.<br>
The Mission object has a built-in system to organize all the data for us.<br>
In this tutorial, I can just use the Integer class. In more complicated missions, you might want to use your own custom object.<br>
```js
public final class ChatMission extends Mission<Integer> {
    
    ...

}
```
Now, we need to start implementing the default methods.<br>
<u>load()</u> - That's your "constructor" of the mission. It has two parameters: the plugin's instance, and the configurationsection of the mission.<br>
If something was not done correctly, and you want to cancel the loading of the mission - throw MissionLoadException with your error as a message.<br>
<u>getProgress()</u> - Calculates the progress of the player. Must return a number between 0 and 1.<br>
<u>onComplete()</u> - A callback method that will be ran when a player completes a mission.<br>
<u>onCompleteFail()</u> - A callback method that will be ran when a player fails to complete a mission.<br>

```js
public final class ChatMission extends Mission<Integer> {

    private int AMOUNT_OF_TIMES = 0;
    private String CHAT_MESSAGE = "";

    @Override
    public void load(JavaPlugin plugin, ConfigurationSection section) throws MissionLoadException {
        if(!section.contains("times"))
            throw new MissionLoadException("Mission ChatMission must contain the \"times\" section!");

        if(!section.contains("message"))
            throw new MissionLoadException("Mission ChatMission must contain the \"message\" section!");

        AMOUNT_OF_TIMES = section.getInt("times");
        
        if(AMOUNT_OF_TIMES <= 0)
            throw new MissionLoadException("times must be a positive value.");
        
        CHAT_MESSAGE = section.getString("message").toLowerCase();
    }

    @Override
    public double getProgress(SuperiorPlayer superiorPlayer) {
        Integer count = get(superiorPlayer);
        return count == null ? 0D : (double) count / AMOUNT_OF_TIMES;
    }

    @Override
    public void onComplete(SuperiorPlayer superiorPlayer) {
        // There's nothing special to do here, so I will just clear data from the user.
        clearData(superiorPlayer);
    }

    @Override
    public void onCompleteFail(SuperiorPlayer superiorPlayer) {
        // Empty
    }

}
```

At this point, you can start listening to your events and alter the data when necessary.<br>
There's only one important thing to do, and it's to call the rewardMission() method.<br>
Furthermore, it's important to implement the saveProgress() and loadProgress() methods, so data will be saved on restarts.<br><br>
The final product after adding a listener & registering it:<br>
```js
public final class ChatMission extends Mission<Integer> implements Listener {

    private int AMOUNT_OF_TIMES = 0;
    private String CHAT_MESSAGE = "";

    @Override
    public void load(JavaPlugin plugin, ConfigurationSection section) throws MissionLoadException {
        if(!section.contains("times"))
            throw new MissionLoadException("Mission ChatMission must contain the \"times\" section!");

        if(!section.contains("message"))
            throw new MissionLoadException("Mission ChatMission must contain the \"message\" section!");

        AMOUNT_OF_TIMES = section.getInt("times");

        if(AMOUNT_OF_TIMES <= 0)
            throw new MissionLoadException("times must be a positive value.");

        CHAT_MESSAGE = section.getString("message").toLowerCase();

        Bukkit.getPluginManager().registerEvents(this, plugin);
    }

    @Override
    public double getProgress(SuperiorPlayer superiorPlayer) {
        Integer count = get(superiorPlayer);
        return count == null ? 0D : (double) count / AMOUNT_OF_TIMES;
    }

    @Override
    public void onComplete(SuperiorPlayer superiorPlayer) {
        // There's nothing special to do here, so I will just clear data from the user.
        clearData(superiorPlayer);
    }

    @Override
    public void onCompleteFail(SuperiorPlayer superiorPlayer) {
        // Empty
    }

    @EventHandler(priority = EventPriority.MONITOR, ignoreCancelled = true)
    public void onPlayerChat(AsyncPlayerChatEvent e){
        SuperiorPlayer superiorPlayer = SuperiorSkyblockAPI.getPlayer(e.getPlayer());;

        // Checking if the tracked message is in the player's message.
        if(!e.getMessage().toLowerCase().contains(CHAT_MESSAGE))
            return;

        // Making sure that the player can actually complete the mission, so we don't track data for no reason.
        if(!SuperiorSkyblockAPI.getMissions().canCompleteNoProgress(superiorPlayer, this))
            return;

        // Increasing the counter by 1.
        Integer currentCount = get(superiorPlayer);
        insertData(superiorPlayer, currentCount == null ? 1 : currentCount + 1);

        /* Calling the reward method with the following paramters:
            mission - this instance.
            superiorPlayer - our player.
            boolean - should the plugin check for auto reward or not.
         */
        SuperiorSkyblockAPI.getMissiosns().rewardMission(this, superiorPlayer, true);
    }

}
```

More complicated missions will require more data to be tracked and more listeners.<br>
Moreoever, I didn't implement the saveProgress() and loadProgress(), and didn't implement other useful methods that you might want to use.<br>
I recommend going through the Mission object before creating your own jar and see all the things it provides.<br>
If you want to see how the default mission jars are implemented, check out their [github repository](https://github.com/OmerBenGera/SuperiorSkyblock2-Missions/)! 