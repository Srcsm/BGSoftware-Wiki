# Menus
Menus (guis) are used in the plugin in many cases, and they are all fully customizable.<br>
In this documantation, you will understand how to edit them to your own style!<br>
Menus also support placeholders!<br>

### Editing the menu's style
You have the ability to edit the style of the menu, which includes its title, its type and the amount of rows it has.<br>

!> Note: some menus might have additional custom fields that are not addressed in this tutorial.

|        Field Name        |                                          Description                                    | Supported Menus |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `title`                  | Custom title for the menu. Supports color codes, 1.16+ codes and placeholders           | All menus       |
| `type`                   | The type of the menu. A list of inventory types can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/inventory/InventoryType.html).         | All menus       |
| `previous-menu`          | Whether or not the previous menu should be opened when closing this menu.               | All menus       |
| `open-sound`             | A sound that will be played when opening the menu. Should follow the sound format.      | All menus       |
| `back`                   | The back button of the menu. This is required if only-back-button is enabled.           | All menus       |
| `previous-page`          | The previous page button for paged menus.                                               | Paged menus     |
| `current-page`           | The display item of the current page of the menu.                                       | Paged menus     |
| `next-page`              | The next page button for paged menus.                                                   | Paged menus     |
| `slots`                  | The item symbol that will be used for the paged menu contents (warps, members, etc)     | Paged menus     |

Besides all of these fields, there is another field that is really important - `pattern`.<br>
This field determines the pattern of the menu, or in other words - the amount of rows that the menu has and the items in the menu.<br>
This field is a list of strings that represents the rows of the menu. Each string should contain the amount of columns the menu has.<br>
(Regular menu types should have 9 items in a row, hoppers should have 5, etc.)<br>
Each item in the menu is represented by a unique char, and can be set in any slot in the menu. Similar chars will represent the same item.<br>

##### Pattern Examples:

The following menu has 1 row with a similar item that is represented by the char `A`:
```yaml
pattern:
- 'A A A A A A A A A'
```

The following example has 5 rows, with a similar item as a border, and is filled with another item:
```yaml
pattern:
- 'A A A A A A A A A'
- 'A B B B B B B B A'
- 'A B B B B B B B A'
- 'A B B B B B B B A'
- 'A A A A A A A A A'
```

### Editing items in the menu
All the items styling is done under the `items` section in the menu. Under this section, each item should have a section where you can style it to your own liking.<br>
The name of the section is the unique char you chose for your item. For the examples above, the unique chars are `A` and `B`.<br>
Therefore, the `items` section will be like the following:
```yaml
items:
  'A':
    ... # All the item's settings
  'B':
    ... # All the item's settings
```

Each item can be configured as you wish, and can have as many settings as you wish from the list down below.<br>

!> Note: SuperiorSkyblock only supports material names, ids are not supported. You can find material names [here](https://bg-software.com/materials/)

|        Field Name        |                                                               Description                                                               |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| `type`                   | The material type of the item.                                                                                                          |
| `data`                   | The data value of the item. Used in versions 1.12 or below to determine different items.                                                |
| `name`                   | Custom name for the item (supports color codes)                                                                                         |
| `lore`                   | A list of lines for the lore of the item (supports color codes)                                                                         |
| `enchants`               | A section for all enchantments. Each enchantment will have a different sub-section, with the level of the ench as a value.              |
| `glow`                   | Whether or not the item should have enchanted effect without having an enchantment in its lore.                                         |
| `flags`                  | A list of item flags to be applied for the item. Supported in 1.9+, and can be found [here](https://helpch.at/docs/1.12.2/index.html?org/bukkit/inventory/ItemFlag.html).  |
| `skull`                  | Base64 value for the skin of the skull, if this item is a player's head item. This can be obtained [here](https://minecraft-heads.com). |
| `unbreakable`            | Set the spigot's unbreakable flag for the item.                                                                                         |
| `effects`                | A list of potion effects that will be applied for the item. More information about it below.                                            |
| `entity`                 | Set the entity of the item, if it's a spawn egg. Replaces the usage of data values for legacy versions.                                 |
| `customModel`            | Set a custom model data for items. This is used to set custom textures for the items using custom resource packs. Supported in 1.14+    |

##### Effects Section
The effects section is used to add effects for potion items. Each effect will have it's own section, and two custom sub-sections: `duration` and `amplifier`.<br>
Here is an example for a potion item with a speed 2 effect that lasts for 5 minutes:
```yaml
'A':
  type: POTION
  effects:
    # Add speed effect to the potion
    speed:
      # The duration of the effect, in seconds
      duration: 300
      # The amplifier of the effect. Calculated as the desired level - 1.
      amplifier: 1
```

# Giving sounds for items
You can make items to play sounds when clicked. All sounds must follow a specific format, which will be described below.<br>
Similar to the way items are configured, the sounds go under the `sounds` section, and as sub-sections, each char of the item you want to apply a custom sound for.<br>
The sound sections should have the following fields:

|        Field Name        |        Description       |
| ------------------------ | ------------------------ |
| `type`                   | The sound to play.       |
| `volume`                 | The volume of the sound. |
| `pitch`                  | The pitch of the sound.  |

An example for a custom sound for the item `A`:
```yaml
sounds:
  'A':
    type: ENTITY_EXPERIENCE_ORB_PICKUP
    volume: 0.2
    pitch: 0.2
```

# Running custom commands
You can make commands to be executed when clicking items. Similar to the sounds and the items sections, you can use the `commands` section to execute custom commands.
Commands can be executed by the Console, or can be executed by the player that clicks the item. Besides that, you can use `%player%` to get the name of the player that clicked the item.<br>

<b>Execute commands by the player:</b><br>
You can make the player to execute the command instead of the Console by having `[player]` at the start of the command.<br>

<b>Execute island commands:</b><br>
You can execute island commands by setting the subcommand in brackets. `[player] [tp]` will make the player to execute /is tp. For a command with args, simply add the args outside of the brackets.<br>

<b>Execute custom commands:</b><br>
You can execute custom commands by simply writing them without `/` at the start. `bc &cHello!` will execute `/bc &cHello!` by the Console.<br>

<b>Built-in actions:</b><br>
The plugin provides two custom actions that can be executed - close the menu and go back to the previous menu.<br>
Similar to the player action, you can use `[close]` to close the menu, and `[back]` to go to the previous menu.<br>


!> I recommend you to follow the default format of menus when you edit them. This will make your life much more easier when working with menus!

# Custom menus
You can make custom menus that will be opened by custom sub-commands.<br>
The principles of the regular menus are also applied to the custom menus. Simply create a new file under the `custom` folder - each file represents a custom menu.<br>
Besides the regular fields of the other menus, custom menus must have the following fields:

|        Field Name        |                                                     Description                                                     | Required Field |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------- | -------------- |
| `command`                | The sub-command that will be used to open the menu (`/island {your-sub-command}`).                                  | Required       |
| `aliases`                | A list of aliases for the command, splitted by `, `.                                                                | Optional       |
| `permission`             | Custom permission that players need to have in order to execute the command.                                        | Optional       |
| `description`            | A list of descriptions for different languages for the command. The description is displayed in `/is help`.         | Optional       |
| `display-command`        | Whether or not the command should be displayed in `/is help`.                                                       | Optional       |

<b>The descriptions section:</b><br>
The description section should have sub-sections for each language, and the description for that language as a value. For example:

```yaml
description:
  # Custom description for the command for English.
  en-US: 'This is a custom command to open a custom menu'
  # Custom description for the command for France.
  fr-FR: ...
```