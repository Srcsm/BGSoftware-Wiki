# Spawner Upgrades
Besides the stacking system of spawners, the plugin also has spawners upgrading system which you can use.<br>
Entities that will be spawned by an upgraded spawner will have the same upgrade as well.<br>
This system gives you the ability to set custom spawner settings and custom drops to entities, and in this page we will cover all of that.

#### Spawner Settings
As I mentioned above, you can edit the settings of spawners using this system.<br>
You can edit the settings of spawners for each upgrade, so you can make upgraded spawners faster with less spawning conditions.<br>
Each ladder has a default upgrade, which means that you can edit the spawner settings to spawners without making them upgradable.

All the spawner settings must go under the upgrade you want:
```yaml
spawner-upgrades:
  # Upgrade ladders
  ladders:
    '1':
      default:
        next-upgrade: coal
        required-player-range: 16
      coal:
        required-player-range: 32
```
In this example, I made it so all the spawners must have a player withing 16 blocks from them.<br>
However, the upgraded spawners (coal upgrade) have an expanded radius of 32 blocks instead of 16.<br>
You can play with this however you want, and there are no restrictions to this.

**Available settings:**<br>

|          Setting         |                                 Description                              | Default Value |
| ------------------------ | ------------------------------------------------------------------------ | ------------- |
| `min-spawn-delay`        | The minimum spawn delay that can be set to spawners.                     | `200`         |
| `max-spawn-delay`        | The maximum spawn delay that can be set to spawners.                     | `800`         |
| `spawn-count`            | The maximum amount of entities that can be spawned in one spawn attempt. | `4`           |
| `max-nearby-entities`    | The maximum amount of entities that can be near the spwaner.             | `6`           |
| `required-player-range`  | The radius to look for nearby players                                    | `16`          |
| `spawn-range`            | The spawning radius                                                      | `4`           |

<br>

#### Upgrade Ladders
The upgrades system is based on ladders, and each spawner can be assoicated with one ladder at most.<br>
This means that you can set different upgrade ladders for different spawners.

Let's start with a basic layout for the ladder:
```yaml
spawner-upgrades:
  # Upgrade ladders
  ladders:
    # The name of the ladder, must be unique.
    '1':
      # A list of mobs that will use this ladder. If non specified, all the spawners will use it.
      entities: []
      # Settings related to the default upgrade. This section is required, otherwise the ladder will not be registered.
      default:
        ...
      # Other upgrades of the ladder. These sections are optional, and you can remove them if you don't want spawners to be upgradable. 
      coal:
        ...
      iron:
        ...
      another-upgrade:
        ...
```

The layout of the ladders is pretty simple:<br>
`entities` A list of entities that can use the ladder.<br>
`default` The default upgrade that will be applied to all the spawners of the ladder.<br>
`upgrades..` Other upgrades that can be added.

All the upgrades sections are the same (default and unique ones), and must have the following sections:<br>
`id` A numerical id for the upgrade. This id must unique across all the upgrades in all the ladders. Default upgrades have a default id of 0 and cannot be changed.<br>
`display` The display prefix/suffix for spawners and mobs. This string is attached to names of entities and spawners.<br>
`cost` The required balance to upgrade into this upgrade. Default upgrades don't need a cost section.<br>
`next-upgrade` The name of the next upgrade. This section is optional, and if it doesn't exist, the upgrade will be treated as the last one in the ladder.<br>
`icon` A custom icon that will be displayed inside the upgrades menu. This section is optional, and if it doesn't exist the upgrades will have a default icon.<br>

That's it! Now you can start creating new upgrades for your spawners.

!> You can find a fully and working example in the default config of the plugin.

#### Custom Drops

You can restrict certain loot pairs and loot items to only be dropped if the entities have a specific upgrade.<br>
You can restrict them by adding `upgrade` section to them with the name of the upgrade you want them to have.

For example, if I want zombies to drop x1 coal if they have the coal upgrade, I will add the following pair to their loot table:
```json
{
  "upgrade": "coal",
  "chance": 100,
  "items": [
    {
      "type": "COAL",
      "chance": 100,
      "min": 1,
      "max": 1
    }
  ]
}
```

!> You can find more information about loot tables [here](http://localhost:3000/#/wildstacker/loot-tables/)