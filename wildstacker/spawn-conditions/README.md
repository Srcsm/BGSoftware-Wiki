# Spawn Conditions
Spawn Conditions are a way for you to override the vanilla conditions system,
and configure conditions of your own.

To add a mob to override, simple create a list for a mob under the `spawn-conditions` option in the entities section of the config.yml. You can find a list of entities that correspond to the version of your server by [clicking here](https://bg-software.com/entities/).

Examples:
```yaml
# Setting an empty list to a mob will remove all spawn conditions
spawn-conditions:
  COW: []

# This example will remove all other spawn conditions and only have NOT_PEACEFUL as a spawn condition for Zombie.
spawn-conditions:
  ZOMBIE:
  - NOT_PEACEFUL

```

#### Conditions
Find a list of spawn conditions here:

!> Note that not all these conditions exist, depending on your server version. Be sure to check Mob Group!

|         Condition        |                                          Description                                    |      Mob Group     |
| ------------------------ | --------------------------------------------------------------------------------------- | ------------------ |
| `ANIMAL_LIGHT`             | Checks for Light Level above 8                                                          | All Animals        |
| `ANIMAL_LIGHT_AND_COLD`    | Checks for Light Level above 8, but also checks for a Cold Biome                        | Polar Bears        |
| `BELOW_SEA_LEVEL`         | Checks for Below Sea Level                                                              | Dolphins           |
| `DARK_BLOCK_LIGHT`         | Checks for Light Level below 8                                                          | Pillagers          |
| `IN_LAVA_AND_AIR_ABOVE`    | Checks for Lava Block and Air above Spawn Location                                      | Striders           |
| `IN_SEA_SURFACE`           | Checks if the Y-Level is the Sea Surface                                                | Turtles            |
| `IN_SLIME_CHUNK_OR_SWAMP`  | Checks for Slime Chunk or Swamp Biome                                                   | Slimes             |
| `IN_WATER_DEEP`            | Checks if Location is in Deep Water                                                     | All Fish           |
| `MONSTER_LIGHT`            | Checks for Monster Light Restrictions, this has more conditions than `DARK_BLOCK_LIGHT` | All Monsters       |
| `NOT_IN_OCEAN`             | Checks for Biomes that aren't Ocean                                                     | Dolphins           |
| `NOT_IN_OCEAN_DEEP`        | Checks for Y-Level above 45, for not too Deep Oceans                                    | Dolphins           |
| `NOT_ON_NETHER_WART_BLOCK` | Checks for Blocks that are not on a Nether Wart Block                                   | Zombified Piglins  |
| `NOT_PEACEFUL`             | Checks for Difficulty that is not Peaceful                                              | All Monsters       |
| `ON_GRASS`                 | Checks for Grass Block                                                                  | All Animals        |
| `ON_GRASS_OR_SAND_OR_SNOW` | Checks for Grass Block, a Sand or Snow Block                                            | Rabbits            |
| `ON_MYCELIUM`              | Checks for Mycelium Block                                                               | Mooshroom          |
| `ON_NETHER_WART_BLOCK`     | Checks for Nether Wart Block                                                            | Hoglins + Piglins  |
| `ON_SAND`                 | Checks for Sand Block                                                                   | Turtles           |
| `ON_TREE_OR_AIR`          | Checks for a Tree Log block or Air                                                      | Parrots           |
