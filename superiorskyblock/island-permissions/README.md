# Island Permissions
Permissions that can be assigned to members or roles, that give access to certain things in the island.<br>
You can remove permissions from being given by not having them inside the permissions menu.<br>

### Built-in permissions

**All**<br>
Gives access to all the permissions.<br>
Recommendation: Should only be given to island leaders.<br>

**Animal Breed**<br>
Gives access to breed animals inside the island.

**Animal Damage**<br>
Gives access to damage animals inside the island

**Animal Spawn**<br>
Gives access to spawn animals inside the island

**Ban Member**<br>
Gives access to ban members from the island

**Break**<br>
Gives access to break blocks inside the island

**Build**<br>
Gives access to build inside the island

**Change Name**<br>
Gives access to change the name of the island

**Chest Access**<br>
Gives access to access chests inside the island

**Close Bypass**<br>
Gives bypass to the lock island status

**Close Island**<br>
Gives access to close (lock) the island to the public

**Coop Member**<br>
Gives access to add a player as a coop-member to the island

**Delete Warp**<br>
Gives access to delete island warps

**Demote Members**<br>
Gives access to demote island members

**Deposit Money**<br>
Gives access to deposit money into the island's bank

**Disband Island**<br>
Gives access to disband the island

**Discord Show**<br>
Gives access to see the discord of the island

**Drop Items**<br>
Gives access to drop items inside the island

**Ender Pearl**<br>
Gives access to use ender pearls inside the island

**Expel Bypass**<br>
Gives bypass from being expelled from the island

**Expel Players**<br>
Gives the ability to expel players from the island

**Farm Tramping**<br>
Gives access to destroy farms (jump on them) inside the island

**Fish**<br>
Gives access to fish inside the island

**Fly**<br>
Gives access to fly around the island

**Interact**<br>
Gives access to interact with blocks inside the island.<br>
The interactable blocks are configurable and can be found under the interactables.yml file.

**Invite Member**<br>
Gives access to invite new players into the island

**Item Frame**<br>
Gives access to break and interact with item frames inside the island

**Kick Member**<br>
Gives access to kick members from the island

**Minecart Damage**<br>
Gives access to damage vehicles inside the island

**Minecart Enter**<br>
Gives access to enter vehicles inside the island

**Minecart Open**<br>
Gives access to open vehicles inside the island

**Minecart Place**<br>
Gives access to place vehicles inside the island

**Monster Damage**<br>
Gives access to damage monsters inside the island

**Monster Spawn**<br>
Gives access to spawn monsters inside the island

**Open Island**<br>
Gives access to open (unlock) the island to the public

**Painting**<br>
Gives access to break paintings inside the island

**Paypal Show**<br>
Gives access to see the paypal of the island

**Pickup Drops**<br>
Gives access to pick up drops inside the island

**Promote Members**<br>
Gives access to promote members inside the island

**Rankup**<br>
Gives access to rankup upgrade levels

**Rating Show**<br>
Gives access to see the ratings that were given to the island

**Set Biome**<br>
Gives access to change the biome of the island

**Set Discord**<br>
Gives access to set the discord of the island

**Set Home**<br>
Gives access to set the teleport location of the island

**Set Paypal**<br>
Gives access to set the paypal of the island

**Set Permission**<br>
Gives access to change the permissions of the island

**Set Role**<br>
Gives access to set roles to members of the island

**Set Settings**<br>
Gives access to change the settings of the island

**Set Warp**<br>
Gives access to set new warps inside the island

**Sign Interact**<br>
Gives access to interact with signs inside the island

**Spawner Break**<br>
Gives access to break spawners inside the island

**Uncoop Member**<br>
Gives access to remove members from being coop from the island

**Use**<br>
Gives access to use blocks inside the island

**Withdraw Money**<br>
Gives access to withdraw money from the island's bank

### Create your own permission
In order to create your own permission, you must have knowledge in Java and the Spigot API.<br>
Alongside of these, you'll also need the SuperiorSkyblock's API, which can be found [here](https://github.com/OmerBenGera/SuperiorSkyblockAPI).<br><br>
Island permissions are represented as a class called "IslandPrivilege", and it's really easy to register custom ones!<br>
In this tutorial, I will make a custom permission for breaking beacons inside islands. First, I register the custom permission<br>
by listening to the PluginInitializeEvent, and there I am calling the IslandPrivilege.register() method.<br>
```java
public final class BeaconPlacePermission implements Listener {

    private static IslandPrivilege BEACON_BREAK;

    @EventHandler
    public void onPluginInit(PluginInitializeEvent e){
        IslandPrivilege.register("BEACON_BREAK");
        BEACON_BREAK = IslandPrivilege.getByName("BEACON_BREAK");
    }

}
```
<u>Please note</u>: PluginInitializeEvent is called in the onEnable() method of SuperiorSkyblock. Therefore, you must have your plugin enabling<br>
before SuperiorSkyblock, which can be done by adding "SuperiorSkyblock2" as a depend/softdepend plugin.<br>

After registering the custom permission, we can simply implement the restirction for breaking beacons!<br>
```java
public final class BeaconPlacePermission implements Listener {

    private static IslandPrivilege BEACON_BREAK;

    @EventHandler
    public void onPluginInit(PluginInitializeEvent e){
        IslandPrivilege.register("BEACON_BREAK");
        BEACON_BREAK = IslandPrivilege.getByName("BEACON_BREAK");
    }
    
    @EventHandler
    public void onBlockBreak(BlockBreakEvent e){
        //Checking for beacons only.
        if(e.getBlock().getType() != Material.BEACON)
            return;

        Island island = SuperiorSkyblockAPI.getIslandAt(e.getBlock().getLocation());
        
        // Making sure the block was broken inside an island.
        if(island == null)
            return;
        
        if(!island.hasPermission(e.getPlayer(), BEACON_BREAK)){
            e.setCancelled(true);
            e.getPlayer().sendMessage("" + ChatColor.RED + ChatColor.BOLD + "Error | " + ChatColor.GRAY + "This island is protected.");
        }
    }

}
```
That's it! Now players must have the BEACON_BREAK permission in order to mine beacons.<br>
You can simply add the new permission to the permissions menu, and edit it's display icon there, the same as the regular permissions.<br>