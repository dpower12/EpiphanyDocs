Remembrance is an item that allows temporary familiars such as Minisaacs, Blue Flies and Spiders, and Dips, to be revived. The familiar dies, is turned into a wisp, and if the wisp is kept alive for enough rooms, it will then spawn two of the familiar the wisp was created from. For mods that add their own temporary familiars, this guide will briefly go over how to setup compatibility with Remembrance so that they can spawn a Remembrance wisp of their own.

## AddRemembranceFamiliar

Adding your familiar as one that can spawn a Remembrance wisp is all done through one function: `Epiphany.API:AddRemembranceFamiliar(identifier: string, remembranceTable: table)`.

- `identifier`: Must be a string unique to the familiar.
- `remembranceTable`: Accepts a table that can contain the following variables:

|Variable Name|Possible Values|Description|
|:--|:--|:--|
|Variant|FamiliarVariant|The variant ID of the familiar to drop a Remembrance wisp on death.|
|Subtype|integer|Optional. The subtype ID of the familiar to drop a Remembrance wisp on death.|
|WispAnm2|string|Optional. The anm2 of the wisp. By default, uses `gfx/003.905.051_crimson_wisp_remembrance.anm2`. If you're customizing the anm2, copy this anm2 and build off of it.|
|WispSpawnChecker|function|Optional. Passes the familiar being killed. Can be used to control whether or not the familiar should drop a wisp. Return `true` if it should, `false/nil` otherwise, where it will continue with its code as normal.|

Below is an example in one of Epiphany's own patches for its Golden Flies/Spiders via Golden Cobweb. WispSpawnChecker is necessary as they're differenciated with custom data, not by variant or subtype, but shouldn't be necessary in most cases if have your own unique familiar variant/subtype:

```Lua
Epiphany.API:AddRemembranceFamiliar("Golden Cobweb Fly", {
	Variant = FamiliarVariant.BLUE_FLY,
	Subtype = 0,
	WispSpawnChecker = function (familiar)
		return familiar:GetData().EP_GoldenCobweb ~= nil
	end,
	AnimationName = "Idle" .. tostring(FamiliarVariant.BLUE_FLY)
})
```

## REMEMBRANCE_WISP_POST_SPAWN_FAMLIIAR

A callback made available through Epiphany is explained in more detail [here](../enums/Epiphany.ExtraCallbacks.md#remembrance_wisp_post_spawn_famliiar), but it essentially runs right after spawning your associated familiar. This is mostly relevant if you intend to do something special for your spawned It passes the familiar that was spawned and, if present, the identifier associated with the familiar. Below is an example of the callback being used once again for Epiphany's Golden Flies/Spiders:

```Lua
--As the familiar spawned would otherwise be a regular blue fly/spider, this is necessary to turn it into its golden variant.
local function goldenCobwebSpawn(_, familiar, customName)
	if customName == "Golden Cobweb Fly" then
		Mod.Item.GOLDEN_COBWEB:ReplaceFly(familiar)
	elseif customName == "Golden Cobweb Spider" then
		Mod.Item.GOLDEN_COBWEB:ReplaceSpider(familiar)
	end
end

Epiphany:AddExtraCallback(Epiphany.ExtraCallbacks.REMEMBRANCE_WISP_POST_SPAWN_FAMLIIAR, goldenCobwebSpawn, FamiliarVariant.BLUE_FLY)
Epiphany:AddExtraCallback(Epiphany.ExtraCallbacks.REMEMBRANCE_WISP_POST_SPAWN_FAMLIIAR, goldenCobwebSpawn, FamiliarVariant.BLUE_SPIDER)
```