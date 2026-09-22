When [Tarnished Keeper](https://tboiepiphany.wiki.gg/wiki/Tarnished_Keeper) touches a beggar, due to his midas curse, the beggar is instantly turned to gold. This unique interaction comes with mod compatibility, where any other mods with their own beggars can add compatibility with feature to create their own "Midas Cursed", or "Golden" version of their beggar.

???- info "Existing mod support"
	Epiphany already supports a large number of mods that add their own beggars. This currently includes:

	- [Andromeda](https://steamcommunity.com/sharedfiles/filedetails/?id=2722017893) (Wisp Wizard)
	- [Arachna](https://steamcommunity.com/sharedfiles/filedetails/?id=3716302651) (Spider Beggar)
	- [Fiend Folio](https://steamcommunity.com/sharedfiles/filedetails/?id=3778123093) (Evil Beggar, Zodiac Beggar)
	- [Ipecac Community Mod](https://steamcommunity.com/sharedfiles/filedetails/?id=1925867065) (Nerd Beggar)
	- [The Punished](https://steamcommunity.com/sharedfiles/filedetails/?id=2809303353) (Red Beggar)
	- [Repentance Plus](https://steamcommunity.com/sharedfiles/filedetails/?id=2627014611) (Stargazer)
	- [Sheriff](https://steamcommunity.com/sharedfiles/filedetails/?id=3754876229) (Sheriff)
	- [Tainted Treasure Rooms](https://steamcommunity.com/sharedfiles/filedetails/?id=2818356312) (Tainted Beggar)


## Sprites and ANM2

All golden beggars share a similar spritesheet and anm2 file. When creating a version of a golden beggar for your own sprites, you should copy from Epiphany's own files. Simply replace all assets of the beggar with your own beggar, but some may require further customization which you are free to do as such. As long as the anm2 has a non-looping Appear and Idle animation, it can function without issue.

- The anm2 is located in resources/gfx/017.201_beggar.anm2.
- Its spritesheet is located in resources/gfx/misc/, named "gold_beggar.png" and the like.

![Spritesheet of a regular golden beggar at x2 scale](../assets/midas_beggars/gold_beggar.png)
![Appear animation of a golden beggar](../assets/midas_beggars/MidasBeggar.gif)

## entities2.xml

Golden beggars are internally shopkeeper variants. You can copy the entities2.xml entry below and replace the name, anm2, and variant appropriately:

```xml
<entity name="Midas Cursed Beggar"
	id="17" variant="201" friction="1" baseHP="150" boss="0" champion="0" collisionDamage="0" collisionMass="5" collisionRadius="13" numGridCollisionPoints="12" shadowSize="14"
	 anm2path="017.201_beggar.anm2" bestiary="false" bestiaryOverlay="Head" shutdoors="false">
	<gibs amount="5" blood="0" bone="0" eye="0" gut="0" large="0" poop="1" />
</entity>
```

## itempools.xml

When a golden beggar is destroyed, it has a chance to drop an item from its item pool. As of Wave 8, the golden beggars require an actual item pool instead of a simple list of collectibles. If not already, you will need to define your beggar's item drops in a custom made item pool in the itempools.xml file. You can create one just by using a custom name and defining one exactly as you would vanilla item pools.

## Lua code

With the prerequisites met, you can now start adding your beggar to the list of beggars Epiphany recognizes. The function is as follows:

`Epiphany.API:AddMidasCursedBeggar(variant: integer, variantGold: integer, itemPool: ItemPoolType | fun(Epiphany, RNG): CollectibleType, drops: table)`

???+ note "Object groups"
	While you're adding your golden beggar, if not already, define your regular beggar under Epiphany's beggar groups. You can learn more about it [here](object_groups.md).

- `variant`: The entity variant of the regular, non-cursed beggar.
- `variantGold`: The entity variant of the golden beggar.
- `itemPool`: The ID of the item pool that this beggar uses. Fetch custom ones through `Isaac.GetPoolIdByName`. Optionally can also be a function, which will pass the Epiphany global and an [RNG](https://repentogon.com/RNG.html) object. Return a CollectibleType to determine what item should be dropped.
- `drops`: A table of pickups that the golden beggar can spawn if it does not drop a collectible.

### Golden beggar drops

If a golden beggar does not drop its collectible, it may instead drop from a unique pool of pickups. These are not typical beggar drops that they would spawn when destroyed normally, instead uniquely catered to each individual beggar. Inside your `drops` table will be more tables, each table being a different type of pickup that can possibly drop from the beggar. Below is a list of variables that each of these tables must contain:

|Variable Name|Possible Values|Description|
|Amount|integer|The minimum amount of the pickup that can drop.|
|BonusAmount|integer|How many additional instances of the pickup that can drop. Each point into BonusAmount gives a 50% chance to add an additional instance of the pickup to drop.|
|Type|EntityType|Optional. Chance the type of entity that is spawned. Default: `EntityType.ENTITY_PICKUP`|
|Variant|integer|Pickup variant|
|Subtype|integer, function|Pickup subtype. As a function, it passes an [RNG](https://repentogon.com/RNG.html) object. Return what the subtype of the pickup should be.

### Example

Below is a final example of what adding a midas cursed beggar would look like, using the regular beggar and its drops as a base.

```Lua
local GOLDEN_BEGGAR = Isaac.GetEntityVariantByName("Midas Cursed Beggar")

local function getTrinket(rng)

end

Epiphany.API:AddMidasCursedBeggar(SlotVariant.BEGGAR, GOLDEN_BEGGAR, ItemPoolType.POOL_BEGGAR,
{
	{ Amount = 1, BonusAmount = 2, Variant = PickupVariant.PICKUP_TAROTCARD, SubType = 0 },
	{ Amount = 1, BonusAmount = 0, Variant = PickupVariant.PICKUP_TRINKET,   SubType = Epiphany.PickupGetter.GetTrinket }, --An internal function from Epiphany. Returns a random TrinketType.
	{ Amount = 1, BonusAmount = 2, Variant = PickupVariant.PICKUP_KEY,       SubType = 0 },
	{ Amount = 1, BonusAmount = 2, Variant = PickupVariant.PICKUP_BOMB,      SubType = 0 },
	{ Amount = 1, BonusAmount = 4, Variant = PickupVariant.PICKUP_COIN,      SubType = 0 },
	{ Amount = 1, BonusAmount = 2, Variant = PickupVariant.PICKUP_HEART,     SubType = 0 },
})