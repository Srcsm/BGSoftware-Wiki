# API
SuperiorSkyblock provides a powerful API, so you can make your own custom addons to the plugin.<br>
You can find the API [here](https://github.com/OmerBenGera/SuperiorSkyblockAPI).<br>

### Basic usage
All of the API methods can be accessed via the [SuperiorSkyblockAPI](https://github.com/OmerBenGera/SuperiorSkyblockAPI/blob/master/src/main/java/com/bgsoftware/superiorskyblock/api/SuperiorSkyblockAPI.java#L21) class.<br>
The API contains lots of objects that are used as method parameters, and here I'll cover some of them:<br><br>
[SuperiorPlayer](https://github.com/OmerBenGera/SuperiorSkyblockAPI/blob/3cd75af980c19061aa0d6fb1120ea8560c26017a/src/main/java/com/bgsoftware/superiorskyblock/api/wrappers/SuperiorPlayer.java#L20)<br>
This object is used as a warpper to the known player objects of the Bukkit's API. It contains data about the player, states of modes (fly mode etc) and more.<br>
You can retrieve the object using `SuperiorSkyblockAPI.getPlayer(<UUID>)`. <br><br>
[Island](https://github.com/OmerBenGera/SuperiorSkyblockAPI/blob/3cd75af980c19061aa0d6fb1120ea8560c26017a/src/main/java/com/bgsoftware/superiorskyblock/api/island/Island.java#L25)<br>
This object is used to cache data about the islands on your server. Members, banned list, multipliers, upgrades and all of the other data is stored in this object.<br>
You can get the Island of a player by using `SuperiorPlayer#getIsland()`.<br>
If you want to get an Island in a specific location, you can use `SuperiorSkyblockAPI.getGrid().getIslandAt(<Location>)`.<br><br>
[GridManager](https://github.com/OmerBenGera/SuperiorSkyblockAPI/blob/3cd75af980c19061aa0d6fb1120ea8560c26017a/src/main/java/com/bgsoftware/superiorskyblock/api/handlers/GridManager.java#L17)<br>
The grid manager object handles all the islands on your server. If you want to interact with islands, get them from the top list or anything related to that, you should use this object.<br>

!> Do not use methods that the Island object has (for example, the deleteIsland method), as it should only be used by the Island object itself.<br>

### Creating your own command
The API provides a way to register your own commands. This can be done by using the `SuperiorSkyblockAPI.registerCommand(<SuperiorCommand>)` method.<br>
In this tutorial, I will add a new command: /is near. It will return which islands are nearby, and in which direction.<br><br>
First of all, I will create my custom SuperiorCommand class:<br>
```java
public final class NearCommand implements SuperiorCommand {

    @Override
    public List<String> getAliases() {
        // A list of aliases. The first argument will be the label of the subcommand.
        return Arrays.asList("near", "nearby");
    }

    @Override
    public String getPermission() {
        // The required permission for the command. If you don't want a specific permission, use "".
        return "";
    }

    @Override
    public String getUsage(Locale locale) {
        // The usage of the command. Should only include the label & arguments of the command.
        return "near";
    }

    @Override
    public String getDescription(Locale locale) {
        // The description of the command, which will be shown in /is help.
        return "Locate nearby islands.";
    }

    @Override
    public int getMinArgs() {
        // Minimum arguments for the command, including the label.
        return 1;
    }

    @Override
    public int getMaxArgs() {
        // Maximum arguments for the command, including the label.
        return 1;
    }

    @Override
    public boolean canBeExecutedByConsole() {
        // Whether or not the command can be executed from Console.
        return false;
    }

    @Override
    public boolean displayCommand() {
        // Whether or not the command would be displayed in the /is help list.
        return true;
    }

    @Override
    public void execute(SuperiorSkyblock plugin, CommandSender sender, String[] args) {
        // TODO
    }

    @Override
    public List<String> tabComplete(SuperiorSkyblock plugin, CommandSender sender, String[] args) {
        // TODO
        return new ArrayList<>();
    }

}
```
That's it. The only thing that is left is to execute your code under the execute code, and implement the tab-complete.<br>
The `execute()` and `tabComplete()` methods contain 3 parameters:<br>
\- plugin: The instance of the plugin.<br>
\- sender: The command sender.<br>
\- args: The arguments from the sender.<br><br>
After filling my code, the final version of the command is the following:<br>
```java
public final class NearCommand implements SuperiorCommand {
    
    <all the other methods>

    private static final int MAX_ISLAND_SIZE = 200;
    
    @Override
    public void execute(SuperiorSkyblock plugin, CommandSender sender, String[] args) {
        // I know that the sender is a player, as I disabled the console from executing.
        SuperiorPlayer superiorPlayer = SuperiorSkyblockAPI.getPlayer((Player) sender);
        
        Island targetIsland = plugin.getGrid().getIslandAt(superiorPlayer.getLocation());
        
        if(targetIsland == null){
            sender.sendMessage("" + ChatColor.RED + ChatColor.BOLD + "Error | " + ChatColor.GRAY + "You must stand inside an island.");
            return;
        }
        
        StringBuilder message = new StringBuilder();
        int islandsAmount = 0;
        
        for(BlockFace blockFace : BlockFace.values()){
            // I want only to get north, west, east and south - I will just check if their modX is -+1 or their modZ is -+1, but not both.
            int modXAbs = Math.abs(blockFace.getModX()), modZAbs = Math.abs(blockFace.getModZ());
            if((modXAbs == 1 || modZAbs == 1) && modXAbs + modZAbs != 2){
                Location targetIslandLocation = targetIsland.getCenter(World.Environment.NORMAL)
                        .add(MAX_ISLAND_SIZE * 3 * blockFace.getModX(), 0, MAX_ISLAND_SIZE * 3 * blockFace.getModZ());
                if(plugin.getGrid().getIslandAt(targetIslandLocation) != null) {
                    islandsAmount++;
                    message.append(", ").append(blockFace.name());
                }
            }
        }
        
        String directionsMessage = message.length() == 0 ? "" : message.substring(2);
        
        switch (islandsAmount){
            case 0:
                sender.sendMessage("" + ChatColor.YELLOW + ChatColor.BOLD + "Island | " + ChatColor.GRAY + "No islands were found.");
                break;
            case 1:
                sender.sendMessage("" + ChatColor.YELLOW + ChatColor.BOLD + "Island | " + ChatColor.GRAY + "There is one island at " + directionsMessage + ".");
                break;
            default:
                sender.sendMessage("" + ChatColor.YELLOW + ChatColor.BOLD + "Island | " + ChatColor.GRAY + "There are islands at " + directionsMessage + ".");
                break;
        }
    }

    @Override
    public List<String> tabComplete(SuperiorSkyblock plugin, CommandSender sender, String[] args) {
        // I don't want any tab completes for this command.
        return new ArrayList<>();
    }

}
```
The last thing to do is to call `SuperiorSkyblockAPI.registerCommand(<SuperiorCommand>)`, and that's it! You registered your own command!<br>
This command will be supported in all tab completes, /is help and argument restrictions!<br>
You can also register the commands without calling the method above. You can extract the class into an external jar, and put it in the commands folder of SuperiorSkyblock2.<br><br>

### Register your own block-keys
The keys system is used to parse blocks and items into a comparable object, that supports both legacy & non-legacy versions.<br>
By registering custom keys, you can give your custom blocks a custom key, which will separate it from similar blocks.<br>
In this tutorial, I'll make "powerful sponges" to have custom keys.<br><br>
In order to accomplish this, I'll use the `SuperiorSkyblockAPI.getBlockValues().registerKeyParser()` method.<br>
This method takes two parameters:<br>
\- customKeyParser: A CustomKeyParser interface, which we need to create.<br>
\- blockTypes: A list of block types which can be parsed by the parser.<br><br>
First of all, I'll create my CustomKeyParser object. The interface contains two methods that needs to be implemented:<br>
\- getCustomKey(\<Location>): Handles the parsing part.<br>
\- isCustomKey(\<Key>): This method is used in the block counts menu, to parse the custom key into it's block form.<br>
After creating the object and implementing basic parser, the code looks like this:<br>
```java
    private static final Set<Location> powerfulSponges = new HashSet<>();
    private static final Key SPONGE_KEY = Key.of("SPONGE");
    private static final Key POWERFUL_SPONGE_KEY = Key.of("POWERFUL_SPONGE");

    private static final class PowerfulSpongeParser implements CustomKeyParser{

        @Override
        public Key getCustomKey(Location location) {
            /* All of my custom sponges are cached in powerfulSponges.
            I know that the block in that location will always be SPONGE, so I can return the sponge key
            if it's not a custom sponge. If it is, then I return my custom key. */
            return powerfulSponges.contains(location) ? POWERFUL_SPONGE_KEY : SPONGE_KEY;
        }

        @Override
        public boolean isCustomKey(Key key) {
            // If the key is "POWERFUL_SPONGE", then that key was created by this parser.
            return key.equals(POWERFUL_SPONGE_KEY);
        }

    }
```
The only thing left is to register the custom parser, and set the whitelisted block types.<br>
This can be done anytime after SuperiorSkyblock was enabled. I am registering it inside a task of bukkit, so I know it happens on the first tick - after all the plugins were enabled.<br>
The final version is the following:<br>
```java
public final class PowerfulSpongesKey {

    private static final Set<Location> powerfulSponges = new HashSet<>();
    private static final Key SPONGE_KEY = Key.of("SPONGE");
    private static final Key POWERFUL_SPONGE_KEY = Key.of("POWERFUL_SPONGE");
    
    public static void registerKey(JavaPlugin plugin){
        Bukkit.getScheduler().runTask(plugin, () -> {
            SuperiorSkyblockAPI.getBlockValues().registerKeyParser(new PowerfulSpongeParser(), SPONGE_KEY); 
        });
    }

    private static final class PowerfulSpongeParser implements CustomKeyParser{

        @Override
        public Key getCustomKey(Location location) {
            /* All of my custom sponges are cached in powerfulSponges.
            I know that the block in that location will always be SPONGE, so I can return the sponge key
            if it's not a custom sponge. If it is, then I return my custom key. */
            return powerfulSponges.contains(location) ? POWERFUL_SPONGE_KEY : SPONGE_KEY;
        }

        @Override
        public boolean isCustomKey(Key key) {
            // If the key is "POWERFUL_SPONGE", then that key was created by this parser.
            return key.equals(POWERFUL_SPONGE_KEY);
        }

    }

}
```
That's it! Everytime I'll place a powerful sponge, it will be considered as "POWERFUL_SPONGE" instead of a regular sponge.<br>
This is supported in counts menu, values menu, worth file, levels file and everything else!<br>