# Island Settings
Every island has settings (flags) that their island owners can modify.<br>
They are used to control different things on the island: fluid flow, lava, spawning and more!<br>

### Built-in settings

**Always Day**<br>
Toggles time to always be day inside the island.<br>
This settings cannot work with other settings that change time.

**Always Middle Day**<br>
Toggles time to always be the middle of the day inside the island.<br>
This settings cannot work with other settings that change time. 

**Always Night**<br>
Toggles time to always be night inside the island.<br>
This settings cannot work with other settings that change time. 

**Always Middle Night**<br>
Toggles time to always be the middle of the night inside the island.<br>
This settings cannot work with other settings that change time. 

**Always Rain**<br>
Toggles weather to always be rainy inside the island.<br>
This settings cannot work with other settings that change weather.

**Always Shiny**<br>
Toggles weather to always be shiny inside the island.<br>
This settings cannot work with other settings that change weather.

**Creeper Explosion**<br>
Toggles creeper explosions harming blocks inside the island.

**Crops Growth**<br>
Toggles growth of crops inside the island.

**Egg Lay**<br>
Toggles chickens laying eggs inside the island.

**Enderman Grief**<br>
Toggles endermans picking up blocks inside the island.

**Fire Spread**<br>
Toggles fire spread to other blocks inside the island.

**Ghast Fireball**<br>
Toggles fireballs harming blocks inside the island.

**Lava Flow**<br>
Toggles lava flowing inside the island.

**Natural Animals Spawn**<br>
Toggles natural spawning of animals inside the island.

**Natural Monster Spawn**<br>
Toggles natural spawning of monsters inside the island.

**PvP**<br>
Toggles pvp between players inside the island.<br>
When enabling the settings, all visitors will be teleported to spawn to prevent traps.

**Spawner Animals Spawn**<br>
Toggles spawner spawning animals inside the island.

**Spawner Monster Spawn**<br>
Toggles spawner spawning monsters inside the island.

**TNT Explosion**<br>
Toggles tnt explosions harming blocks inside the island.

**Tree Growth**<br>
Toggles growth of trees inside the island.

**Water Flow**<br>
Toggles water flowing inside the island.

**Wither Explosion**<br>
Toggles wither explosions harming blocks inside the island.

### Create your own setting
In order to create your own setting, you must have knowledge in Java and the Spigot API.<br>
Alongside of these, you'll also need the SuperiorSkyblock's API, which can be found [here](https://github.com/OmerBenGera/SuperiorSkyblockAPI).<br><br>
Island settings are represented as a class called "IslandFlag", and it's really easy to register custom ones!<br>
In this tutorial, I will make a custom setting for swimming. First, I register the custom setting<br>
by listening to the PluginInitializeEvent, and there I am calling the IslandFlag.register() method.<br>
```java
public final class SwimmingFlag implements Listener {

    private static IslandFlag SWIMMING;

    @EventHandler
    public void onPluginInit(PluginInitializeEvent e){
        IslandFlag.register("SWIMMING");
        SWIMMING = IslandFlag.getByName("SWIMMING");
    }

}
```

!> PluginInitializeEvent is called in the onEnable() method of SuperiorSkyblock. Therefore, you must have your plugin enabling<br>
before SuperiorSkyblock, which can be done by adding "SuperiorSkyblock2" as a depend/softdepend plugin.<br>

After registering the custom flag, we can simply implement the restirction for swimming!<br>
```java
public final class SwimmingFlag implements Listener {

    private static IslandFlag SWIMMING;

    @EventHandler
    public void onPluginInit(PluginInitializeEvent e){
        IslandFlag.register("SWIMMING");
        SWIMMING = IslandFlag.getByName("SWIMMING");
    }
    
    @EventHandler(ignoreCancelled = true)
    public void onPlayerMove(PlayerMoveEvent e){
        // First I check for movement between blocks
        if(e.getFrom().getBlockX() == e.getTo().getBlockX() && e.getFrom().getBlockY() == e.getTo().getBlockY() && 
                e.getFrom().getBlockZ() == e.getTo().getBlockZ())
            return;

        Island island = SuperiorSkyblockAPI.getIslandAt(e.getTo());
        
        // We make sure that swimming is disabled
        if(island == null || island.hasSettingsEnabled(SWIMMING))
            return;

        Block toBlock = e.getTo().getBlock();
        Block belowBlock = toBlock.getRelative(BlockFace.DOWN);
        
        // We check if the target block is water, or the block below it is water.
        if(toBlock.getType() == Material.WATER || (!toBlock.getType().isSolid() && belowBlock.getType() == Material.WATER)){
            e.setCancelled(true);
            e.getPlayer().sendMessage("" + ChatColor.RED + ChatColor.BOLD + "Error | " + ChatColor.GRAY + "This island has swimming disabled.");
        }
        
    }

}
```
That's it! Now players cannot enter water if the setting is disabled.<br>
You can simply add the new setting to the settings menu, and edit it's display icon there, the same as the regular settings.<br>