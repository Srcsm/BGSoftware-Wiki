### Loot Tables
Loot tables are used to store all the loot data of entities.<br>
They cannot be disabled, and they are used to calculate loot faster.<br>
They can be changed however you want, as long as you follow the formatting rules.<br><br>
Every file is represented as a "loot table". Loot tables contain global settings and pairs.<br>
Pairs contain the items, and can be manipulated differently to get different results.<br>

### Loot Tables
```
{
  # We don't want equipment to be dropped.
  "dropEquipment": false,
  # We want a random exp value between 5 and 8.
  "exp":{
    "min": 5,
    "max": 8,
    # Should exp be dropped no matter how the entity was killed?
    "always-drop": true
  },
  # We want a maximum amount of 2 pairs, but at least 1 pair to be chosen.
  "min": 1,
  "max": 2,
  # All the pairs of items are going here
  "pairs": [
  ...
  ]
}
```

### Loot Pairs
```
{
  # All settings related to the table
  ...
  "pairs": [
    # First Pair
    {
      # This pair should always be chosen (100%)
      "chance": 100,
      # Chance is [base-chance] + ([looting-level] * [looting-chance])
      "lootingChance": 2.5,
      # A required permission for the pair to be chosen.
      "permission": "my.permission",
      # A list of items for this pair
      "items": [
        ...
      ]
    },
    # Second Pair
    {
      # This pair will be chosen only if the entity was killed by a player.
      "killedByPlayer": true,
      # This pair will be chosen only 50% of the times.
      "chance": 50,
      # A required spawn cause for the entity so the pair will be chosen.
      "spawn-cause": "SPAWNER",
      # A list of items for this pair
      "items": [
        ...
      ]
    },
    # Third Pair
    {
      # This pair will be chosen only if the entity was killed by an enderman.
      "killer": [
        "ENDERMAN"
      ],
      # This pair will be chosen only 50% of the times.
      "chance": 50,
      # A list of commands for this pair
      "commands:" [
        ...
      ]
    }
  ]
}
```

### Loot Items
```
{
  # All settings related to the table
  ...
  "pairs": [
    {
      # All settings related to the pair
      ...
      "items": [
        # First item
        {
          # The material type of the item
          "type": "DIAMOND_SWORD",
          # The data value of the item
          "data": 0,
          # A custom name for the item.
          "name": "&6Diamond Sword!!",
          # A custom lore for the item.
          "lore": [
            "&7First line!",
            "&4Second line!"
          ],
          # The chance of this item to be chosen.
          "chance": 50,
          # Minimum amount for the item
          "min": 1,
          # Maximun amount for the item
          "max": 1,
          # A list of enchantments that will be applied to the item.
          "enchants":{
            # First enchantment - Sharpness 5
            "DAMAGE_ALL": 5,
            # Second enchantment - Looting 3
            "LOOT_BONUS_MOBS": 3
          }
        },
        # Second item
        {
          # Values
          ...
          # Should the item amount be increased when using looting?
          # The formula to calculate the item amount is [random number between min and max] + [random number between 0 and the looting level]
          "looting": true,
          # The item will be glowing when dropped (no enchantments will be shown)
          "glow": true,
          # The item that will be dropped if the entity was killed by fire
          "burnable:"{
            "type": "COOKED_BEEF",
            "data": 0
          }
        },
        # Third item
        {
          "type": "PLAYER_HEAD",
          # Values
          ...
          # The texture value of the skull.
          # These values can be taken from many sites, such as https://minecraft-heads.com/.
          # The head below will be shown as an orc head.
          "skull": "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODJkNmI2MjJmMDZkYmQzYjE5YmY3NjUzOGNhNzA0NzMzZWQwYjAyZTQ0MzhjOWQ4OTY4YTA0YmZiYjI4ZWY2MyJ9fX0=",
          # It is possible to add custom nbt tags to your items.
          "nbt-data": {
            "key1": "Value!",
            "key2": 2
          }
        }
      ]
    }
  ]
}
```

### Loot Commands
```
{
  # All settings related to the table
  ...
  "pairs": [
    {
      # All settings related to the pair
      ...
      "commands": [
        # First command
        {
          # The chance of this command to be chosen
          "chance": 50,
          # Minimum amount for the placeholder
          "min": 1,
          # Maximun amount for the placeholder
          "max": 1,
          # A list of commands that will be ran
          "commands":[
            "give {player-name} diamond {number}",
            "give {player-name} dirt {number}"
          ]
        },
        # Second command
        {
          # The chance of this command to be chosen
          "chance": 50,
          # Minimum amount for the placeholder
          "min": 1,
          # Maximun amount for the placeholder
          "max": 64,
          # A list of commands that will be ran
          "commands":[
            "give {player-name} emerald {number}"
          ]
        }
      ]
    }
  ]
}
```