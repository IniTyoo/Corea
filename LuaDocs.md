# Corea Documentation
* [Structs](#structs)
* [Functions](#functions)
* [Hooks](#hooks)

## Structs
* [Vector2](#vector2)
* [NetAvatar](#netavatar)
* [WorldObject](#worldobject)
* [InventoryItem](#inventoryitem)
* [Tile](#tile)
* [GamePacket](#gamepacket)
* [VariantList](#variantlist)
* [ItemInfo](#iteminfo)

## Vector2
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `x` | Position x |
| Number | `y` | Position y |

## Clothes
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `hat` | Player's hat item id |
| Number | `shirt` | Player's shirt item id |
| Number | `pants` | Player's pants item id |
| Number | `feet` | Player's feet item id |
| Number | `face` | Player's face item id |
| Number | `hand` | Player's hand item id |
| Number | `back` | Player's back item id |
| Number | `hair` | Player's hair item id |
| Number | `chest` | Player's chest item id |
| Number | `artifact` | Player's artifact item id |

## NetAvatar
| Type | Name | Description|
|:-----|:----:|:-----------|
| String | `name` | Player's name |
| String | `country` | Player's flag id |
| [Vector2](#vector2) | `pos`  | Player's position |
| [Vector2](#vector2) | `tile` | Player's tile position |
| Number | `netid` | Player's netID |
| Number | `userid` | Player's userID |
| Bool | `facing_left` | Is player facing left |
| [Clothes](#Clothes) | `clothes` | Player's tile position |

## WorldObject
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `id` | Object's item ID |
| Number | `oid` | Object's index |
| [Vector2](#vector2) | `pos` | Object's position |
| Number | `count` | Object's item count |
| Number | `flags` | Object's flags |
 
## InventoryItem
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `id` | Item's ID |
| Number | `count` | Item count |

## Tile
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `fg` | Foreground block's ID |
| Number | `bg` | Background block's ID |
| [Vector2](#vector2) | `pos` |Tile's position |
| Number | `flags` | Tile's flags |

## GamePacket
| Type | Name | Description|
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
| Type | Name | Description|
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
| Type | Name | Description|
|:-----|:----:|:-----------|
| String | `name` | Item name |
| Number | `id` | Item ID |
| Number | `rarity` | Item rarity |
| Number | `growtime` | Item growtime |
| Number | `breakhits` | Item breakhits |

## Functions
* [sendPacket](#sendpacket)
* [sendPacketRaw](#sendpacketraw)
* [sendVarlist](#sendvarlist)
* [log](#log)
* [findPath](#findpath)
* [getLocal](#getlocal)
* [getInventory](#getinventory)
* [getPlayers](#getplayers)
* [getObjects](#getobjects)
* [getTile](#gettile)
* [getTiles](#gettiles)
* [getItemInfo](#getiteminfo)
* [isSolid](#issolid)
* [drawLine](#drawline)
* [drawText](#drawtext)
* [drawRect](#drawrect)
* [worldToScreen](#worldtoscreen)
* [patchBytes](#patchbytes)
