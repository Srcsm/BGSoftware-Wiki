# Upgrades
Using upgrades, you can give your players custom perks that are upgradable.<br>
In this documantation, you will understand how to edit them to your own style!<br>

### Creating your first upgrade
Creating a new upgrade is an easy task to do!<br>
All the upgrades follow the same rules, but in this tutorial we will create a generator upgrade.<br><br>
We will start with the basic layout for the upgrade:<br>
```yaml
upgrades:
  island-generators:        # The name of the upgrade.
    '1':                    # The first level of the upgrade.
      <to-do>
    '2':                    # The second level of the upgrade.
      <to-do>
```
All the upgrades work with the same layout: a global section for the upgrade,<br>
and sub-sections for every level of the upgrade. You can make as many levels as you want!<br><br>
Now, we can start working on our first level. We will give it a price, commands to be executed upon rankup<br>
and a required permission to use the upgrade. In this case, I don't want a permission - so I don't add that section.<br>
```yaml
'1':
  price: 100000.0          # The price to rank up to the second level.
  commands:
    - 'island admin setupgrade %player% island-generators 2'     # We must change the level of the upgrade manually using a command.
    - 'island admin msgall %player% &e&lUpgrade | &7%player% upgraded your generators to level 2!'   # Message that will be sent to the island members.
  permission:  <your-permission>   # You can add it if you want a required permission to rankup.
```
As you might have noticed, I run /is admin setupgrade - this is required so the plugin will actually change the upgrade's level for the island.<br>
Not doing so will make the upgrade to not rankup, as you'll see in the last level.<br><br>
After we set up the basic layout of the level, we want to give it some values. The values will be synced with the island.<br>
You can change crop growth, spawner rates, mob drops, limits, generators and more with the upgrades!<br>
For this tutorial, I will change the generator rates using the "generator-rates" section:<br>
 ```yaml
'1':
  price: 100000.0
  commands:
    - 'island admin setupgrade %player% island-generators 2'
    - 'island admin msgall %player% &e&lUpgrade | &7%player% upgraded your generators to level 2!'
  generator-rates:
    normal:      # The world environment. Can use normal, nether or the_end.
      STONE: 85
      COAL_ORE: 10
      IRON_ORE: 5 
```

That's it! We completed our first level! Because this is the first level of the upgrade, it will be applied to all the islands by default.<br>
It means that all of the islands on my server will have the generator rates that I configured.<br>
Now, I will add more levels by following the same layout:<br>
 ```yaml
upgrades:
  island-generators:
    '1':
      price: 100000.0
      commands:
        - 'island admin setupgrade %player% island-generators 2'
        - 'island admin msgall %player% &e&lUpgrade | &7%player% upgraded your generators to level 2!'
      generator-rates:
        normal:
          STONE: 85
          COAL_ORE: 10
          IRON_ORE: 5 
    '2':
      price: 150000.0
      commands:
        - 'island admin setupgrade %player% island-generators 3'
        - 'island admin msgall %player% &e&lUpgrade | &7%player% upgraded your generators to level 3!'
      generator-rates:
        normal:
          STONE: 70
          COAL_ORE: 15
          IRON_ORE: 10
          DIAMOND_ORE: 5
    '3':
      price: 300000.0
      commands:
        - 'island admin setupgrade %player% island-generators 4'
        - 'island admin msgall %player% &e&lUpgrade | &7%player% upgraded your generators to level 4!'
      generator-rates:
        normal:
          STONE: 50
          COAL_ORE: 25
          IRON_ORE: 15
          DIAMOND_ORE: 10
```
After I configured all of my levels, I must also add the last upgrade - level #4.<br>
Unlike the other upgrades, this upgrade will not have the setupgrade command, but will still have values assigned to it:<br>
```yaml
'4':
  price: 0.0       # I set the price to 0, so my players will always get the warning message.
  commands:
    - 'island admin msg %player% &c&lError | &7You have reached the maximum upgrade for island generators.'
  generator-rates:
    normal:
      EMERALD_ORE: 50
      DIAMOND_ORE: 50
```
Finally, I have a working generator upgrade that will have it's values synced with all the islands.<br>
You can change the values anytime you want, and your islands will be synced automatically with it.<br>
Removing existing levels is not an option - you can just make the upgrade to do nothing, but removing<br>
it completely will cause errors from the plugin.<br>

You can use the following sections to alter island values:<br>
<u>crops-growth</u>: The crop growth multiplier for this upgrade.<br>
<u>spawner-rates</u>: The spawner rates multiplier for this upgrade.<br>
<u>mob-drops</u>: The mob drops multiplier for this upgrade.<br>
<u>team-limit</u>: The team limit for this upgrade.<br>
<u>warps-limit</u>: The warps limit for this upgrade.<br>
<u>coop-limit</u>: The coops limit for this upgrade.<br>
<u>border-size</u>: The border size for this upgrade.<br>
<u>block-limits</u>: The block limits for this upgrade.<br>
&ensp;&ensp;&ensp;&ensp;Under this section, all the blocks will be in the following format: "TYPE: LIMIT".<br>
<u>entity-limits</u>: The entity limits for this upgrade.<br>
&ensp;&ensp;&ensp;&ensp;Under this section, all the entities will be in the following format: "TYPE: LIMIT".<br>
<u>generator-rates</u>: The generator rates for this upgrade.<br>
&ensp;&ensp;&ensp;&ensp;Under this section, all the rates will be in the following format: "TYPE: CHANCE".<br>
<u>island-effects</u>: The island effects for this upgrade.<br>
&ensp;&ensp;&ensp;&ensp;Under this section, all the effects will be in the following format: "EFFECT: LEVEL".<br>

<br>

### Custom Upgrades
You can create custom upgrades with data from other plugins using the commands section.<br>
<u>Please note</u>: islands will not be synced with that data.<br>

<br>

### Disabling Upgardes
In order to disable upgrades completely, follow the instructions below:<br>
1. Delete all the upgrades from the upgrades file.<br>
2. Revoke the permission superior.island.upgrade from players (Removing the ability to use /is upgrade).<br>
3. Revoke the permission superior.island.rankup from players (Removing the ability to rankup upgrades).<br>

That's all. You can keep upgrades in the upgrades file for default multipliers and limits for your islands.<br>
Unlike the config options, these multipliers & limits will by synced with islands all the time, so you can<br>
edit them from the upgrades file and they will be updated to all the islands. If you remove the permission to<br>
rankup and use the upgrades menu, the upgrades will not be visible to the normal players.<br>