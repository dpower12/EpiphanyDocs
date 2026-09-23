[True Love](https://tboiepiphany.wiki.gg/wiki/True_Love) is a collectible that adds the chance for any heart pickups spawned to be turned into a heart of the same type that Isaac owns. For the few mods that add custom hearts, True Love needs to know how to identify how many of the heart Isaac has and how to spawn it. This guide covers how to add your modded heart onto True Love and replace other heart pickups.

???- info "Existing mod support"
	Epiphany already supports a large number of mods that add their own beggars. This currently includes:

	- [Fiend Folio](https://steamcommunity.com/sharedfiles/filedetails/?id=3778123093) (Immoral Heart, Morbid Heart)

## AddTrueLoveHeart

Adding your custom heart to True Love can be done through the function `Epiphany.API:AddTrueLoveHeart(identifier: string, heartTable: table)`.

- `identifier`: is a string that uniquely identifies your heart type
- `heartTable`: A table that can contain the following variables:

|Variable Name|Possible Values|Description|
|:--|:--|:--|
|getAmount|function|Passes the player holding True Love. Return how many of the heart the player has, serving as a weight to how likely that heart will be chosen when replacing a heart pickup.|
|subtype|integer|Optional. If your heart to spawn is using `PickupVariant.PICKUP_HEART` (10), then you can simply put its subtype here when the pickup spawns|
|replaceFunction|function|Optional. Passes the heart pickup to be morphed. Overrides the `subtype` variable. Can be used to manually morph the heart pickup into something else, typically if your heart pickup uses a different pickup variant or a different pickup entirely.|

### Example

Below is an example usage of the function, using Epiphany's Blue Broken Hearts:

```Lua
Epiphany.API:AddTrueLoveHeart("BLUE_BROKEN", {
	getAmount = function(player)
		return Epiphany:GetBlueBrokenHearts(player)
	end,
	subType = Epiphany.Pickup.BLUE_BROKEN_HEART.ID
})
```
