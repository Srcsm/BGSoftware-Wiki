# Upgrades
Using upgrades, you can give your players custom perks that are upgradable.<br>
In this documantation, you will understand how to edit them to your own style!<br>

### Creating your first upgrade
Creating a new upgrade is an easy task to do!<br>
Here we will go through all the basic sections, that every upgrade has / can have.<br>
All the upgrades go below the main section: "upgrades", and every upgrade must have a unique name.<br><br>
<u>price</u>: The price to upgrade to the next level.<br>
<u>commands</u>: A list of commands that will be exected when completing the upgrade.<br>
<u>permission</u>: The required permission to upgrade to this upgrade.<br><br>
The following sections are for setting custom multipliers etc for islands.<br>
All islands will be synced with them, and will be updated when these are updated.<br>
<u>crops-growth</u>: The crop growth multiplier for this upgrade.<br>
<u>spawner-rates</u>: The spawner rates multiplier for this upgrade.<br>
<u>mob-drops</u>: The mob drops multiplier for this upgrade.<br>
<u>team-limit</u>: The team limit for this upgrade.<br>
<u>warps-limit</u>: The warps limit for this upgrade.<br>
<u>border-size</u>: The border size for this upgrade.<br>
<u>block-limits</u>: The block limits for this upgrade.<br>
Under this section, all the blocks will be in the following format: "TYPE: LIMIT".<br>
<u>generator-rates</u>: The generator rates for this upgrade.<br>
Under this section, all the rates will be in the following format: "TYPE: LIMIT".<br>

### Custom upgrades
You can create custom upgrades with data from other plugins using the commands section.<br>
<u>Please note</u>: islands will not be synced with that data.<br>

### Disabling upgardes
In order to disable upgrades completely, follow the instructions below:<br>
1. Delete all the upgrades from the upgrades file.<br>
2. Revoke the permission superior.island.upgrade from players (Removing the ability to use /is upgrade).<br>
3. Revoke the permission superior.island.rankup from players (Removing the ability to rankup upgrades).<br>

That's all. You can keep upgrades in the upgrades file for default multipliers and limits for your islands.<br>
Unlike the config options, these multipliers & limits will by synced with islands all the time, so you can<br>
edit them from the upgrades file and they will be updated to all the islands. If you remove the permission to<br>
rankup and use the upgrades menu, the upgrades will not be visible to the normal players.<br>