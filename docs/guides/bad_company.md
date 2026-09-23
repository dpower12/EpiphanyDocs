[Bad Company](https://tboiepiphany.wiki.gg/wiki/Bad_Company) is a collectible that allows Isaac to hire shopkeepers, turning them into unique friendly Greeds or Super Greeds. By default, all shopkeepers (entity type of 17) can be hired and turned into a basic friendly Greed. This guide will briefly cover how to assign a specific Bad Company Greed to your shopkeeper or blacklist your shopkeeper from being hireable.

## AddShopkeeperToBadCompany

Assigning shopkeepers to Bad Company Greeds is done through the function `Epiphany.API:AddShopkeeperToBadCompany(badCompanyGreed: string, ...: integer)`

- `badCompanyGreed`: The string associated with the Bad Company Greed. These are all values available under `Epiphany.Item.BAD_COMPANY.GREEDS`, being:
 - BASE_GREED
 - SUPER_GREED
 - ERROR_GREED
 - GOLD_SUPER_GREED
 - SOILED_GREED
- `...`: An ellipsis (accepts an unlimited amount of arguments) of entity variants of the shopkeepers that can be purchased.

Only the BASE_GREED is a regular Greed, while the rest are Super Greeds, reserved for special types of shopkeepers, but can be used for your own shopkeepers if they're similar enough in nature.

```Lua
Epiphany.API:AddShopkeeperToBadCompany("SOILED_GREED", Epiphany.MiscFamiliar.SOILED_KEEPER.ID)
```

## AddShopkeeperToBadCompanyBlacklist

If you do not wish for your shopkeeper to be hireable, it can be blacklisted with the function `Epihany.API:AddShopkeeperToBadCompanyBlacklist(...: integer)`. It accepts an ellipsis of entity variants, like so:

```Lua
Epiphany.API:AddShopkeeperToBadCompanyBlacklist(Epiphany.MiscFamiliar.SOILED_KEEPER.ID)
```