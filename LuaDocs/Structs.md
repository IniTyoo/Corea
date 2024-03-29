**←** [Back to main](Main.md)

# Structs
* [Vector2](#vector2)
* [World](#World)
* [Clothes](#Clothes)
* [ENetClient](#ENetClient) (Bot)
* [NetAvatar](#netavatar) (Player)
* [WorldObject](#worldobject)
* [WorldTile](#WorldTile)
* [WorldGhost](#WorldGhost)
* [InventoryItem](#inventoryitem)
* [Inventory](#inventory)
* [GamePacket](#gamepacket)
* [VariantList](#variantlist)
* [ItemInfo](#iteminfo)

## Vector2
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `x` | Position x |
| Number | `y` | Position y |

## World
| Type | Name | Description |
|:-----|:----:|:-----------|
| String | `name` | World name |
| Number | `width` | World width |
| Number | `height` | World height |
| Number | `signal` | [GeigerSignal](Defines.md#GeigerSignal) |
| Bool | `locked` | Is world locked |
| Bool | `jammed` | Is world jammed |
| Number | `owner` | World owner's userID |
| Table&lt;Number> | `admins` | World admin's userIDs |

| Returns | Function | Description |
|:-----|:----:|:-----------|
| Table<[NetAvatar](#NetAvatar)> | `GetPlayers()` | Get all players |
| Table<[WorldGhost](#WorldGhost)> | `GetGhost()` | Get all ghosts |
| Table<[WorldTile](#WorldTile)> | `GetTiles()` | Get all tiles |
| [WorldTile](#WorldTile) | `GetTile(int tile_x, int tile_y)` | Get tile |
| Table<[WorldObject](#WorldObject)> | `GetObjects()` | Get all floating items (objects) |

## Clothes
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `hat` | Player's hat item ID |
| Number | `shirt` | Player's shirt item ID |
| Number | `pants` | Player's pants item ID |
| Number | `feet` | Player's feet item ID |
| Number | `face` | Player's face item ID |
| Number | `hand` | Player's hand item ID |
| Number | `back` | Player's back item ID |
| Number | `hair` | Player's hair item ID |
| Number | `chest` | Player's chest item ID |
| Number | `artifact` | Player's artifact item ID |

## ENetClient
| Type | Name | Description |
|:-----|:----:|:-----------|
| String | `name` | Bot's name |
| String | `country` | Bot's flag ID |
| String | `world` | Bot's world name |
| [Vector2](#vector2) | `pos`  | Bot's position |
| [Vector2](#vector2) | `tile` | Bot's tile position |
| Number | `netid` | Bot's netID |
| Number | `userid` | Bot's userID |
| Number | `gems` | Bot's gem amount |
| Number | `level` | Bot's level |
| String | `status` | Bot's status |
| Number | `state` | Bot's state ||
| Bool | `captcha` | Bot's captcha state |
| String | `world` | Bot's world name |
| Bool | `facing_left` | Is bot facing left |
| [Clothes](#Clothes) | `clothes` | Bot's clothes |
| [Inventory](#Inventory) | `inventory` | Bot's inventory data |

## NetAvatar
| Type | Name | Description |
|:-----|:----:|:-----------|
| String | `name` | Player's name |
| String | `country` | Player's flag ID |
| [Vector2](#vector2) | `pos`  | Player's position |
| [Vector2](#vector2) | `tile` | Player's tile position |
| Number | `netid` | Player's netID |
| Number | `userid` | Player's userID |
| Bool | `facing_left` | Is player facing left |
| [Clothes](#Clothes) | `clothes` | Player's clothes |
| Bool | `admin` | Is player world admin |
| Bool | `owner` | Is player world owner |

| Returns | Function | Description |
|:-----|:----:|:-----------|
| Null | `Trade()` | Send trade packet |
| Null | `Kick()` | Send kick packet |
| Null | `Pull()` | Send pull packet |
| Null | `Ban()` | Send ban packet |

## WorldObject
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `id` | Object's item ID |
| Number | `oid` | Object's index |
| [Vector2](#vector2) | `pos` | Object's position |
| Number | `amount` | Object's item amount |
| Number | `flags` | Object's flags |

## WorldTile
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `fg` | Foreground block's ID |
| Number | `bg` | Background block's ID |
| [Vector2](#vector2) | `pos` |Tile's position |
| Number | `flags` | Tile's flags |
| Bool | `ready` | Is ready to harvest tree |
| Bool | `solid` | Is can pass the tile |
| Bool | `water` | Is water on the tile |
| Bool | `fire` | Is fire on the tile |

## WorldGhost
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `ghostype` | Ghost type |
| [Vector2](#vector2) | `pos` | Ghost curent position |
| [Vector2](#vector2) | `target` | Ghost target position |
| Number | `velocity` | Ghost velocity |
 
## InventoryItem
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `id` | Item's ID |
| Number | `amount` | Item amount |
| Bool | `wearing` | Is item wearing |
| Bool | `wearable` | Is item can be worn ([ItemInfo](#ItemInfo)) | 

## Inventory
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `size` | Inventory size of slots |
| Number | `space` | Inventory empty slots |
| Number | `use` | Inventory using slots |
| Table<[InventoryItem](#InventoryItem)> | `items` | Inventory items |

## GamePacket
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `type` | Packet type |
| Number | ` objtype` |  |
| Number | `count1 ` |  |
| Number | `count2 ` |  |
| Number | `netid ` | Packet netID |
| Number | `item ` |  |
| Number | `flags ` | Packet flags |
| Number | `float1` |  |
| Number | `int_data` |  |
| Number | `pos_x` |  |
| Number | `pos_y` |  |
| Number | `pos2_x` |  |
| Number | `pos2_y` |  |
| Number | `float2` |  |
| Number | `int_x` |  |
| Number | `int_y` |  |

## VariantList
| Type | Name | Description |
|:-----|:----:|:-----------|
| Number | `netid` | NetID |
| Number | `delay` | Delay |
| String | `[0]` | Variant function name |
| Any | `[1]` | Param 1 |
| Any | `[2]` | Param 2 |
| Any | `[3]` | Param 3 |
| Any | `[4]` | Param 4 |
| Any | `[5]` | Param 5 |

## ItemInfo
※ If the program fails to read items.dat, the functions of the variables associated with this may not work.
| Type | Name | Description |
|:-----|:----:|:-----------|
| String | `name` | Item's name |
| Number | `id` | Item's ID |
| Number | `rarity` | Item's rarity |
| Number | `growTime` | Item's growTime |
| Number | `breakHits` | Item's breakHits |
| Number | `collisionType` | Item's collisionType |
| Number | `clothingType` | Item's clothingType |
| Number | `itemCategory` | Item's itemCategory |
| Number | `itemProps2` | Item's itemProps2 |
