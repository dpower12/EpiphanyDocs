Everything for Epiphany is accessed through the `Epiphany` global. From here, it branches off into different tables that contain the rest of the mod, accessed as `Epiphany.VARIABLE_NAME`.

Below are all the main tables Epiphany holds that a modder may need to access, the tables they hold, and the variables that can be consistently found through all of them. Further information on these tables or others not listed here should be found by searching through the game's codebase directly.

## Epiphany.PlayerType

- BETHANY
- BLUEBABY
- CAIN
- EDEN
- ISAAC
- JUDAS
- JUDAS_1
- JUDAS_2
- JUDAS_4
- JUDAS_5
- KEEPER
- LOST
- MAGDALENE
- SAMSON

## Epiphany.Character

???+ info
	Holds all code associated with the character. PlayerTypes should be accessed with `Epiphany.PlayerType`.

- BETHANY
- BLUEBABY
- CAIN
- EDEN
- ISAAC
- JUDAS
- KEEPER
- LOST
- MAGDALENE
- SAMSON

## Epiphany.Item

???+ info "Item structure"
	The following can be accessed through the variables under `Epiphany.Item`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|ID|integer|CollectibleType ID|
	|FAMILIAR|integer|Holds the FamiliarVariant, if a familiar is involved|

- ACTIVE_SACK
- AIR_CONDITIONER
- ANAL_FISSURE
- ANCIENT_ONES_MARK
- ANKLE_WEIGHTS
- BAD_COMPANY
- BLEEDING_HEART
- BLIGHTED_DICE
- BLIGHTED_PHOTO
- BOMB_VOUCHER
- BOTTLED_SPIRITS
- BRAIN_IN_A_JAR
- BROKEN_HALO
- BROKEN_ORB
- BROKEN_PILLAR
- BURNING_PASSION
- CARDBOARD_CUTOUT
- CARDIAC_ARREST
- CHANCE_CUBE
- CLOT_BOMBS
- COIN_CASE
- CORPUS_HERMETICUM
- CORPUS_VOCANDI
- CRIMSON_BANDANA
- D5
- DADS_TOOLBOX
- DARK_ROCK
- DEBUG
- DELILAHS_RAZOR
- DESCENT
- DIMENSIONAL_KEY
- DIVINE_REMNANTS
- DOORKNOB
- EMPTY_DECK
- FERRYMANS_OAR
- FINAL_WISHES
- FIRE_OF_ALEXANDRIA
- FIRST_PAGE
- FLY_TRAP
- GAMBITS_DICE
- GEOCACHE
- GIANT_PUFFBALL
- GLITCHED_PHOTO
- GLITCH_ITEM_0
- GLITCH_ITEM_1
- GLITCH_ITEM_2
- GLITCH_ITEM_3
- GLITCH_ITEM_4
- GOLDEN_COBWEB
- KAEK
- KILLER_INSTINCT
- KINS_CURSE
- LIL_GUPPY
- LINEN_SHROUD
- LIQUID_NITROGEN
- LIVING_BLOOD
- MIMICRY
- MIX
- MOMS_HUG
- MOTHERS_SHADOW
- MYOPIA
- NOTHING
- OLD_KNIFE
- PARTY_POPPER
- PILE_OF_NOTES
- PLASMA_BALL
- PORTABLE_DICE_MACHINE
- PRINTER
- PROMO_TOY
- RELATIVE_ROBBY
- REMEMBRANCE
- RETRIBUTION
- REVOLT
- ROTTEN_CORE
- SAVAGE_CHAINS
- SEGMENTATION_FAULT
- SHADOW_REMNANTS
- SHARP_ROCK
- SHRED
- STOCK_FLUCTUATION
- SURPRISE_BOX
- THE_BOX
- THIRTY_PIECES_OF_SILVER
- THROBBING_CROWN
- THROWING_BAG
- TRUE_LOVE
- TURNOVER
- WARM_COAT
- WEIRD_HEART
- WOODEN_STAKE
- WOOLEN_CAP
- WORK_IN_PROGRESS
- ZIP_BOMBS

## Epiphany.Trinket

???+ info "TrinketType"
	The TrinketType ID is accessed through `Epiphany.Trinket.TRINKET_NAME.ID`.

- BETHS_ORDEAL
- BLACK_KEY
- CEREMONIAL_BOWL
- DADS_WALLET
- ECTOPLASM
- HELLS_EYE
- IED
- LUCKY_CAT
- MOMS_GRIEF
- PAPER_AIRPLANE
- ROPES

## Epiphany.Card

???+ info "Card structure"
	The following can be accessed through the variables under `Epiphany.Card`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|ID|integer|Card ID|
	|SFX|integer|Announcer voiceline when using the card|
	|SFX_ALT|integer|Optional. Alternate announcer voiceline that plays rarely|

- AGAINST_HUMANITY
- DEBIT_CARD
- DRAWN_CARD
- DRAW_ONE
- EXCLAMATION_MARK
- GO_TO_JAIL
- HOUSE_QUEEN_OF_HEARTS
- HOUSE_RULES
- HOUSE_SUICIDE_KING
- HOUSE_TWO_OF_CLUBS
- HOUSE_TWO_OF_DIAMONDS
- HOUSE_TWO_OF_HEARTS
- HOUSE_TWO_OF_SPADES
- INVERSE
- MINUS_ONE
- OFFERING
- PAIN_IN_A_BOX
- REVERSE
- SMALL_RAZOR

## Epiphany.Essence

???+ info "Essence structure"
	The following can be accessed through the variables under `Epiphany.Essence`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|ID|integer|Essence ID|
	|SFX|integer|Announcer voiceline sound ID when using the essence|
	|SFX_ALT|integer|Optional. Alternate announcer voiceline sound ID that plays rarely|
- BAGGED
- BETHANY
- BLUEBABY
- CAIN
- EDEN
- ISAAC
- JUDAS
- KEEPER
- LOST
- MAGDALENE
- SAMSON

## Epiphany.Capsule

???+ info "Capsule structure"
	The following can be accessed through the variables under `Epiphany.Capsule`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|ID|Capsule||
	|SFX|integer|Announcer voiceline sound ID when using the capsule|
	|WEIGHT|float|Alternate announcer voiceline sound ID that plays rarely|
	|MOD|string|Optional. If belonging to another mod, contains the mod's name. By default, `"Epiphany"` and `"Fiend Folio"` are used|
- AZURITE_SPINDOWN
- D1
- D10
- D100
- D12
- D2
- D20
- D3
- D4
- D5
- D6
- D7
- D8
- DUSTY_D10
- ETERNAL_D10
- ETERNAL_D12
- ETERNAL_D6
- GAMBITS_DICE
- LOADED_D6
- SPINDOWN_DICE

## Epiphany.Slot

???+ info "SlotVariant"
	The SlotVariant ID is accessed through `Epiphany.Slot.SLOT_NAME.ID`.

- ALTAR
- CONVERTER_BEGGAR
- DICE_MACHINE
- GLITCH
- GRAFTING_ALTAR
- PAIN_O_MATIC
- PROBOSCIS
- TITHE_BOX
- TURNOVER_RESTOCK

## Epiphany.Pickup

???+ info "PickupVariant"
	The PickupVariant ID is accessed through `Epiphany.Slot.SLOT_NAME.ID`.

- BLUE_BROKEN_HEART
- BOMB_SACK
- BROKEN_HEART
- COLOSTOMY
- DIME_DAMAGE
- DIME_LUCK
- DIME_RANGE
- DIME_SHOTSPEED
- DIME_SPEED
- DIME_TEARS
- DUSTY_CHEST
- GOLDEN_ITEM
- MANTLE_SHARD
- MULTITOOL
- NICKEL_DAMAGE
- NICKEL_LUCK
- NICKEL_RANGE
- NICKEL_SHOTSPEED
- NICKEL_SPEED
- NICKEL_TEARS
- ONE_TIME_USE_ITEM
- PENNY_DAMAGE
- PENNY_LUCK
- PENNY_RANGE
- PENNY_SHOTSPEED
- PENNY_SPEED
- PENNY_TEARS
- SAMPLE_BOMBS
- TASTY_PENNY
- WHEAT

## Epiphany.Grid

- TWISTED_ROCK
	- Has the type `GridEntityType.GRID_ROCK` and variant `TWISTED_ROCK.ID`.
- WISP_HIVE
	- Identified by save data that can be checked with `WISP_HIVE:IsWispHive(fire)`.

## Epiphany.Npc

???+ info "PickupVariant"
	The EntityType ID is accessed through `Epiphany.Npc.NPC_NAME.ID`.

???+ info "Revolt"
	`KNIGHT`, `GRUNT`, `BRUTE`, and `COMMANDER` each contain `ID` and `Variant` for the EntityType and variant.

- ABEL
- EDEN_GLITCH
- REVOLT
	- KNIGHT
	- GRUNT
	- BRUTE
	- COMMANDER
- SHADOW_MIRAGE

## Epiphany.Challenge

???- info "Challenge structure"
	The following can be accessed through the variables under `Epiphany.Challenge`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|Name|Used for DSS achievement viewer.|
	|SortOrder|Used for DSS achievement viewer.|
	|ID|integer|Challenge ID.|
	|Character|string|Name of the character that starts in this challenge in all caps. Used to associate the challenge unlock with a character unlock.|
	|UnlockReq|string|The name of something else to be unlocked to unlock the challenge. Used for the DSS achievement viewer, currently exclusively unlocked with tarnished characters.|
	|Unlock|string|Name of the achievement unlocked by beating the challenge|
	|func|function|Function that passes the player. Called during [MC_PLAYER_INIT_POST_LEVEL_INIT_STATS](https://repentogon.com/enums/ModCallbacks.html#mc_player_init_post_level_init_stats) during the respective challenge.|

- DEALMAKER
- DONDE_ESTA_LA_BIBLIOTECA
- EMPEROR_OF_FLIES
- FIRST_STONE
- HEART_BURN
- KAGEMANE_NO_JUTSU
- NULL_POINTER_EXCEPTION
- ONE_WITH_NOTHING
- OVERWHELMING_ODDS
- POOL
- RETRIBUTION_CHALLENGE

## Epiphany.PickupPrice

- PRICE_HEART_DEBT: PickupPrice,
- PRICE_KEYS: PickupPrice,
- PRICE_TWO_BLUE_BROKEN_HEARTS: PickupPrice,
- PRICE_TWO_BROKEN_HEARTS: PickupPrice,

## Epiphany.Rooms

- ATTIC
- BATHROOM
- BETHANY_ENDING
- CHEST
- REVOLT
- ROOM_MANAGER

## Epiphany.MiscFamiliar

???+ info "MiscFamiliar structure"
	The following can be accessed through the variables under `Epiphany.MiscFamiliar`:

	|Variable Name|Possible values|Description|
	|:--|:--|:--|
	|ID|integer|The variant or subtype of the familiar, depending on the entity.|

- BLOOD_BABY_IRONCLAD
	- Variant: `FamiliarVariant.BLOOD_BABY`, Subtype: Table's `ID`.
- FLY_HOLY
	- Variant: `FamiliarVariant.BLUE_FLY`, Subtype: Table's `ID`.
- FLY_ICY
	- Variant: `FamiliarVariant.BLUE_FLY`, Subtype: Table's `ID`.
- FLY_MAGNETIC
	- Variant: `FamiliarVariant.BLUE_FLY`, Subtype: Table's `ID`.
- FLY_PSYCHIC
	- Variant: `FamiliarVariant.BLUE_FLY`, Subtype: Table's `ID`.
- SOILED_KEEPER
	- Variant: Table's `ID`.
