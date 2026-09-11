[Golden Items](https://tboiepiphany.wiki.gg/wiki/Golden_Item) are a rare unlockable variant of collectibles in Epiphany, gaining a golden shine. A golden passive item will simply grant two of the item. A golden active item will enact a Car Battery effect where it activates twice, however there are many instances where it is instead given a completely unique effect. This guide covers everything available for interacting with golden items and creating custom golden active item synergies.

???+ info "Designnig golden actives"
	Golden active items should be designed with the same design philosophy as golden trinkets: A marginal upgrade to the item's effects due to its rarity, either by making an existing aspect of the item stronger or adding a new effect in line with how the item works. There's also two specific types of golden active synergies that should be kept in mind:

	1. Most one-time-use active items should be able to be used twice. You can remove the golden status of an active item through `Epiphany:ExaustGoldenItem(itemID, player, slot)` and, as this is your own modded active, can control whether or not its removed.
	2. Specific actives that don't change its effects, but instead reduce its maximum charge. This is done for a few actives that can't work when activated twice and also don't have any good options for a unique effect either, such as Clicker, Gello, and the Pony actives.

## Helper Functions

These functions are all different ways to detect if a golden item is present on a player or pedestal.

### AnyPlayerHasGoldenCollectible () {: aria-label='Functions' }
#### boolean Epiphany.API.AnyPlayerHasGoldenCollectible ([CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html)) {: aria-label='Functions' }

Returns `true` if any player has the provided `CollectibleType` as a golden active item.

___
### CanActivateGoldenEffect () {: aria-label='Functions' }
#### boolean Epiphany.API.CanActivateGoldenEffect ([CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html), [EntityPlayer](https://repentogon.com/EntityPlayer.html), [ActiveSlot](https://wofsauge.github.io/IsaacDocs/rep/enums/ActiveSlot.html) = nil) {: aria-label='Functions' }

Returns `true` if the item usage is valid for activating its golden effect. For use within callbacks related to activations of the item such as [MC_USE_ITEM](https://wofsauge.github.io/IsaacDocs/rep/enums/ModCallbacks.html#mc_use_item), having extra checks for the `nogoldenitem` tag and if it should be activated from Void.

___
### HasGoldenItem () {: aria-label='Functions' }
#### boolean Epiphany.API.HasGoldenItem ([CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html), [EntityPlayer](https://repentogon.com/EntityPlayer.html), [ActiveSlot](https://wofsauge.github.io/IsaacDocs/rep/enums/ActiveSlot.html) = nil) {: aria-label='Functions' }

Returns `true` if the player has the provided `CollectibleType` as a golden active item. Leaving `ActiveSlot` as `nil` will search all active slots on the player.

___
### IsGoldenPedestal () {: aria-label='Functions' }
#### boolean Epiphany.API.IsGoldenPedestal ([EntityPickup](https://repentogon.com/EntityPickup.html)) {: aria-label='Functions' }

Returns `true` if pickup is a pedestal containing a golden item.

___

## Main Functions

These are the functions you should use for changing the default behaviour of golden active items.

### AddGoldenActiveSynergy () {: aria-label='Functions' }
#### void Epiphany.API.AddGoldenActiveSynergy ([CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html), function([EntityPlayer](https://repentogon.com/EntityPlayer.html), [CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html), [RNG](https://wofsauge.github.io/IsaacDocs/rep/RNG.html), [UseFlag](https://wofsauge.github.io/IsaacDocs/rep/enums/UseFlag.html), [ActiveSlot](https://wofsauge.github.io/IsaacDocs/rep/enums/ActiveSlot.html), int varData) SynergyFunc) {: aria-label='Functions' }

Overrides default behaviour of triggering the active item a second time, instead calling the passed function.

???+ note
	Golden active uses are called on [MC_USE_ITEM](https://wofsauge.github.io/IsaacDocs/rep/enums/ModCallbacks.html#mc_use_item) on EARLY priority, meaning it will activate before most modded actives. This is due to the fact that modded actives typically return early on normal priority, preventing future callbacks from running. In most cases, you'll want to pass an empty function into this and use the helper callbacks above directly within your active item's code. This will also disable the default text of "Triggers the item twice!" from the EID entry.

___
### AddSharedGoldenActiveUse () {: aria-label='Functions' }
#### void Epiphany.API.AddSharedGoldenActiveUse ([CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html) ChildItem, [CollectibleType](https://wofsauge.github.io/IsaacDocs/rep/enums/CollectibleType.html) ParentItem) {: aria-label='Functions' }

Treats uses of `ChildItem` on a slot of `-1` as a use of a golden active item if `ParentItem` is a golden active item on the same player. By default, this is used by D Infinity and its uses of other dice items.

___

## Other

A quick list of other things to keep in mind for golden active items:

- Epiphany.Pickup.GOLDEN_ITEM.DisableGoldPedestal can be set to `true` before spawning a pedestal to mark it as not able to spawn as a golden pedestal
- By default, a copy of the default active item sprite is rendered above the regular active item on the HUD. For active items that have multiple sprites via custom rendering or a crop offset, you can use Epiphany.ExtraCallbacks.PRE_GOLDEN_ACTIVE_RENDER to cancel the default rendering and handle the golden rendering yourself.
- The custom tag [nogoldenitem](item_tags.md) can be used in the items.xml file to prevent the item from spawning as a golden item naturally. It can still be forcibly turned into a golden via methods such as Essence of the Keeper, but the tag also stops any additional effects, so it will not activate twice.

## External Item Descriptions

The most important mod compatibility with golden items is describing their effects for the [External Item Descriptions](https://steamcommunity.com/sharedfiles/filedetails/?id=836319872) mod. They should always be additional lines starting with `{{GoldenItem}} {{ColorGold}}"`. As this is a conditional description, you should use add EID's `EID:addDescriptionModifier` and check the provided description object against [IsGoldenPedestal](#isgoldenpedestal) to display your custom golden active text. Keep in mind that Epiphany already handles displaying text by default if the item is a passive item, an item with the `nogoldenitem` tag, or hasn't been added under [AddGoldenActiveSynergy](#addgoldenactivesynergy) to indicate it's simply triggered twice.

More information about generally adding compatibility with EID can be found [here](https://github.com/wofsauge/External-Item-Descriptions/wiki).