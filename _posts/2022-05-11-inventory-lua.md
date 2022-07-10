---
title: INVENTORY 
author: outsider
date: 2022-05-11 00:34:00 +0800
categories: [Documentation Lua, INVENTORY]
tags: [Lua] 
---



#### ***VORP inventory API***

## API

vorp Inventory provide a custom API that allow you to interact with items as wall as creating custom inventories.

### ***Installation***

* inventory export to be used at the top of the `server` side

```lua
-- at the top of server file
local VORPInv = {}

VORPInv = exports.vorp_inventory:vorp_inventoryApi()

```

### ***Item API***
You can use the API to give, delete, register item utility, get quantities and even ask if the player can carry the item.

#### Add Item
```lua
VorpInv.addItem(source, itemName, qty, metadata)
```


| Parameter        | Type   | Description                                         | Required ? |
|------------------|--------|-----------------------------------------------------|------------|
| source           | Number | The player id in game                               | True       |
| itemName         | String | The name of the item to add                         | True       |
| qty              | Number | The quantity of item to add                         | True       |
| metadata         | Table  | An object containing all custom data of item to add | False      |

#### Sub Item
```lua
VorpInv.subItem(source, itemName, qty, metadata)
```

| Parameter        | Type   | Description                                            | Required ? |
|------------------|--------|--------------------------------------------------------|------------|
| source           | Number | The player id in game                                  | True       |
| itemName         | String | The name of the item to remove                         | True       |
| qty              | Number | The quantity of item to remove                         | True       |
| metadata         | Table  | An object containing all custom data of item to remove | False      |

#### Get Item
```lua
local item = VorpInv.getItem(source, itemName, metadata)
```

| Parameter | Type         | Description                                         | Required ? |
|-----------|--------------|-----------------------------------------------------|------------|
| source    | Number       | The player id in game                               | True       |
| itemName  | String       | The name of the item to get                         | True       |
| metadata  | Table        | An object containing all custom data of item to get | False      |

| Return   | Type                | Description                                            |
|----------|---------------------|--------------------------------------------------------|
| Return   | Table (Item) or nil | An object containing all item information              |

#### Get Item Count
```lua
local itemCount = VorpInv.getItemCount(source, itemName, metadata)
```

| Parameter | Type         | Description                                            | Required ? |
|-----------|--------------|--------------------------------------------------------|------------|
| source    | Number       | The player id in game                                  | True       |
| itemName  | String       | The name of the item to count                          | True       |
| metadata  | Table        | An object containing all custom data of item to remove | False      |

| Return   | Type   | Description                                          |
|----------|--------|------------------------------------------------------|
| Return   | Number | The total count of selected item in player inventory |

#### Can Carry Item
```lua
local canCarry = VorpInv.cancarryitem(source, itemName, amount)
```

| Parameter | Type   | Description                                                  | Required ? |
|-----------|--------|--------------------------------------------------------------|------------|
| source    | Number | The player id in game                                        | True       |
| itemName  | String | The name of the item to count                                | True       |
| amount    | Number | The amount of space needed in Item stack for the item to add | True       |

| Return   | Type    | Description                                  |
|----------|---------|----------------------------------------------|
| Return   | Boolean | True if there is enough space, False if not. |

#### Can Carry Items
```lua
local canCarry = VorpInv.CanCarryItems(source, amount)
```

| Parameter | Type   | Description                                                  | Required ? |
|-----------|--------|--------------------------------------------------------------|------------|
| source    | Number | The player id in game                                        | True       |
| amount    | Number | The amount of space needed in Inventory for the items to add | True       |

| Return | Type    | Description                                  |
|--------|---------|----------------------------------------------|
| Return | Boolean | True if there is enough space, False if not. |

#### Register Usable Item
```lua
VorpInv.CanCarryItems(itemName, cb)
```

| Parameter | Type     | Description                                            | Required ? |
|-----------|----------|--------------------------------------------------------|------------|
| itemName  | String   | The name of the item to count                          | True       |
| cb        | Function | The function that will be called with the item is used | True       |

#### Get DB Item
```lua
local item = VorpInv.getDBItem(source, itemName)
```

| Parameter | Type         | Description                 | Required ? |
|-----------|--------------|-----------------------------|------------|
| source    | Number       | The player id in game       | True       |
| itemName  | String       | The name of the item to get | True       |

| Return   | Type                | Description                                          |
|----------|---------------------|------------------------------------------------------|
| Return   | Table (Item) or nil | The total count of selected item in player inventory |


### Weapons API
You can use the API to add, delete and get weapons, ad, remove or get weapon bullets and components and even check if the player can carry the weapons.

#### Add Weapon
```lua
VorpInv.creatWeapon(source, weaponName, ammo, comp)
```

| Parameter  | Type   | Description                    | Required ? |
|------------|--------|--------------------------------|------------|
| source     | Number | The player id in game          | True       |
| weaponName | String | The name of the weapon to add  | True       |
| ammo       | Table  | An array containing start ammo | False      |
| comp       | Table  | An array containing start comp | False      |

#### Sub Weapon
```lua
VorpInv.subWeapon(source, weaponId)
```

| Parameter | Type   | Description                    | Required ? |
|-----------|--------|--------------------------------|------------|
| source    | Number | The player id in game          | True       |
| weaponId  | Number | The id of the weapon to remove | True       |

#### Give Weapon
```lua
VorpInv.giveWeapon(source, weaponId, target)
```

| Parameter | Type   | Description                    | Required ? |
|-----------|--------|--------------------------------|------------|
| source    | Number | The player id in game          | True       |
| weaponId  | Number | The id of the weapon to remove | True       |
| target    | Number | The target player id in game   | True       |

#### Add Bullets
```lua
VorpInv.addBullets(source, weaponId, type, qty)
```

| Parameter | Type   | Description                  | Required ? |
|-----------|--------|------------------------------|------------|
| source    | Number | The player id in game        | True       |
| weaponId  | Number | The id of the weapon         | True       |
| type      | String | The bullet type to add       | True       |
| qty       | Number | The amount of bullets to add | True       |

#### Sub Bullets
```lua
VorpInv.subBullets(source, weaponId, type, qty)
```

| Parameter | Type   | Description                     | Required ? |
|-----------|--------|---------------------------------|------------|
| source    | Number | The player id in game           | True       |
| weaponId  | Number | The id of the weapon            | True       |
| type      | String | The bullet type to remove       | True       |
| qty       | Number | The amount of bullets to remove | True       |

#### Get Weapon Bullets
```lua
local WeaponBullets = VorpInv.getWeaponBullets(source, weaponId)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |
| weaponId  | Number | The id of the weapon  | True       |

| Return | Type         | Description                                              |
|--------|--------------|----------------------------------------------------------|
| Return | Table or nil | An Array containing all the loaded bullets in the weapon |

#### Get Weapon Components
```lua
local weaponComps = VorpInv.getWeaponComponents(source, weaponId)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |
| weaponId  | Number | The id of the weapon  | True       |

| Return | Type         | Description                                                 |
|--------|--------------|-------------------------------------------------------------|
| Return | Table or nil | An Array containing all the loaded components on the weapon |

#### Get Weapons
```lua
local weapons = VorpInv.getUserWeapons(source)
```

| Parameter | Type   | Description                     | Required ? |
|-----------|--------|---------------------------------|------------|
| source    | Number | The player id in game           | True       |

| Return | Type         | Description                                      |
|--------|--------------|--------------------------------------------------|
| Return | Table or nil | An Array containing all the weapon of the player |

#### Get Weapon
```lua
local weapon = VorpInv.getUserWeapon(source, weaponId)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |
| weaponId  | Number | The id of the weapon  | True       |

| Return | Type                  | Description                                 |
|--------|-----------------------|---------------------------------------------|
| Return | Table (Weapon) or nil | An Object containing all weapon information |

#### Can Carry Weapons
```lua
VorpInv.canCarryWeapons(source, amount, cb)
```

| Parameter | Type               | Description                                        | Required ? |
|-----------|--------------------|----------------------------------------------------|------------|
| source    | Number             | The player id in game                              | True       |
| amount    | Number             | The amount of space needed to carry the weapons    | True       |
| cb        | Function(canCarry) | A Callback function containing a Boolean Parameter | True       |


### Inventory API
You can use the API to open or close the player Inventory, and register custom private or shared inventories.

#### Get Inventory
```lua
local inventory = VorpInv.getUserInventory(source)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |

| Return | Type                  | Description                                       |
|--------|-----------------------|---------------------------------------------------|
| Return | Table (Item[]) or nil | An Array containing all items in player Inventory |

#### Open Player Inventory
```lua
VorpInv.OpenInv(source)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |

#### Close Player Inventory
```lua
VorpInv.OpenInv(source)
```

| Parameter | Type   | Description           | Required ? |
|-----------|--------|-----------------------|------------|
| source    | Number | The player id in game | True       |

#### Register Inventory
```lua
VorpInv.registerInventory(id, name, limit, acceptWeapons, shared)
```

| Parameter     | Type    | Description                                             | Required ? |
|---------------|---------|---------------------------------------------------------|------------|
| id            | String  | The id of the custom inventory                          | True       |
| name          | String  | The name of the custom inventory                        | True       |
| limit         | Number  | The item limit of the custom inventory                  | True       |
| acceptWeapons | Boolean | Does inventory accept weapons (Default: True)           | False      |
| shared        | Boolean | Is Inventory shared across all players (Default: False) | False      |


#### Remove Inventory
```lua
VorpInv.removeInventory(id)
```

| Parameter     | Type   | Description                              | Required ? |
|---------------|--------|------------------------------------------|------------|
| id            | String | The id of the custom inventory to remove | True       |

#### Open Custom Inventory
```lua
VorpInv.openInventory(source, id)
```

| Parameter | Type   | Description                            | Required ? |
|-----------|--------|----------------------------------------|------------|
| source    | Number | The player id in game                  | True       |
| id        | String | The id of the custom inventory to open | True       |

#### Close Custom Inventory
```lua
VorpInv.openInventory(source, id)
```

| Parameter | Type   | Description                             | Required ? |
|-----------|--------|-----------------------------------------|------------|
| source    | Number | The player id in game                   | True       |
| id        | String | The id of the custom inventory to close | True       |

#### Set Custom Inventory Item Limit
```lua
VorpInv.setInventoryItemLimit(id, itemName, limit)
```

| Parameter | Type   | Description                                                                                | Required ? |
|-----------|--------|--------------------------------------------------------------------------------------------|------------|
| id        | String | The id of the custom inventory                                                             | True       |
| itemName  | String | The name of the Item                                                                       | True       |
| limit     | Number | The limit for this item in the custom inventory. Set 0 to deny this item in this inventory | True       |

#### Set Custom Inventory Weapon Limit
```lua
VorpInv.setInventoryWeaponLimit(id, weaponName, limit)
```

| Parameter  | Type   | Description                                                                                    | Required ? |
|------------|--------|------------------------------------------------------------------------------------------------|------------|
| id         | String | The id of the custom inventory                                                                 | True       |
| weaponName | String | The name of the Weapon                                                                         | True       |
| limit      | Number | The limit for this weapon in the custom inventory. Set 0 to deny this weapon in this inventory | True       |















