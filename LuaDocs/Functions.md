**←** [Back to main](Main.md)

# Functions
* [Global Functions](#Global-Functions)
* [ENetClient Functions](#ENetClient-Functions) (Bot)
* [World Functions](#World-Functions)
* [NetAvatar Functions](#NetAvatar-Functions) (Player)

## Global Functions
* [Sleep](#Sleep)(int millisecond)
* [GetBots](#GetBots)()
* [GetSelectedBots](#GetSelectedBots)()
* [GetBot](#GetBot)(string name)
* [AddBot](#AddBot)(string name, string password [, string socks5])
* [RemoveBot](#RemoveBot)(string name)
* [RunFile](#RunFile)(string filename)
* [StopFile](#StopFile)(string filename)
* [RunThread](#RunThread)(string thread_name, ENetClient, void* function)
* [GetItemInfo](#GetItemInfo)(int item_id)
* [RTVAR](#RTVAR)(string key)
* [HttpGet](#HttpGet)(string url)
* [RemoveColors](#RemoveColors)(string text)
* [MessageBox](#MessageBox)(string title,[, string content, int type, int dismiss_time])

## Sleep
`Sleep(int millisecond)`

Delay parameter 1 value milliseconds in the current thread. (1000ms = 1s)

Example:
```lua
-- Move the bot to the left twice. but add a 1 second delay in the middle
local bot = GetSelectedBots()[1]
bot:Move(LEFT)
Sleep(1000)
bot:Move(LEFT)
```

## GetBots
`GetBots()`

Of all bots, return the bot's [ENetClient Structs](Structs.md#ENetClient) and [ENetClient Functions](#ENetClient-Functions) as a table.

Example:
```lua
-- Print the count of all bots
local bots = GetBots()
print(#bots)
```

## GetSelectedBots
`GetSelectedBots()`

Returns the [ENetClient Structs](Structs.md#ENetClient) and [ENetClient Functions](#ENetClient-Functions) of the selected bot among all bots.

Example:
```lua
-- Print the number of selected bots
local bots = GetSelectedBots()
print(#bots)
```

## GetBot
`GetBot(string name)`

Returns the bot's [ENetClient Structs](Structs.md#ENetClient) and [ENetClient Functions](#ENetClient-Functions).\
The `name` in parameter 1 is not case sensitive and returns `NULL` if the bot is not found.

Example:
```lua
-- Print "found" if the bot was found or "not found" if not found
local bot = GetBot("seth")
print(bot and "found" or "not found")
```

## AddBot
`AddBot(string name, string password [, string socks5])`

Adds a bot to the list, then returns the bot's [ENetClient Structs](Structs.md#ENetClient) and [ENetClient Functions](#ENetClient-Functions).\
`socks5` in parameter 3 is optional and can be added by typing `IP:PORT:USERNAME:PASSWORD`.

Example:
```lua
-- Add a bot and then disconnect it
local bot = AddBot("username", "password")
bot:Disconnect()
```

## RemoveBot
`RemoveBot(string name)`

Removes a bot with that name from the bot list

## RunFile
`RunFile(string filename)`

Execute a script from file ( async )
```lua
RunFile("stealeromg.lua")
```

## StopFile
`StopFile(string filename)`

Terminate a script from file
```lua
StopFile("stealeromg.lua")
```

## RunThread
`RunThread(string thread_name, ENetClient, void* function)`

Create and run a thread with a name, a bot object and a function
```lua
bot1 = GetBot("INDONESIA") 
RunThread("ga tau", bot1, function(bot) print(bot.name) 
end)
```

## ~~StopThread~~
`StopThread(string thread_name)`

Stopa thread with a name
```lua
StopThread("ga tau")
```

## GetItemInfo
`GetItemInfo(int item_id)`

Return the structure [ItemInfo](Structs.md#ItemInfo) of an item
```lua
print(GetItemInfo(2).name)
```

## HttpGet
`HttpGet(string url)`

Return the string
```lua
print(HttpGet("https://indonesia.com/bali-architecture-landmarks"))
```

## RemoveColors
`RemoveColors(string text)`

Return the string
```lua
for id, player in pairs(bot:GetPlayers()) do
	print(RemoveColors(player.name))
end
```

## MessageBox
`MessageBox(string title,[, string content, int type, int dismiss_time])`

Check [MessageBoxType](Defines.md#MessageBoxType)
```lua
MessageBox("BALI", "Indonesian island with Hindu culture, beaches, temples and volcanoes.", MessageBoxType_Info)
```



## RTVAR
`RTVAR(string key)`

return the [RTVAR Functions](#RTVAR-Functions) as a table.

Example:
```lua
-- Parse String to RTVAR
rtvar = RTVAR([[
name|indragoreng
mstate|2
]])
print(rtvar:GetParam("name"))
```

## RTVAR Functions
* [GetParam](#GetParam)(string key)
* [GetIntParam](#GetIntParam)(string key)
* [GetLongParam](#GetLongParam)(string key)
* [FindKey](#FindKey)(string key)

## ENetClient Functions
* [Connect](#Connect)(bool Connect)
* [Disconnect](#Disconnect)(bool reset)
* [Say](#Say)(string message)
* [Move](#Move)(int direction [, ...])
* [Enter](#Enter "Enter the door at the bot's tile position.")()
* [FindPath](#FindPath)(int tile_x, int tile_y [, int delay])
* [Warp](#Warp)(string world_name [, string door_id])
* [Collect](#Collect)(int radius [, bool force collect])
* [CollectSet](#CollectSet)(bool collect, int radius [, int delay, bool force])
* [Punch](#Punch)(int tile_x, int tile_y [, bool animation])
* [Place](#Place)(int item_id, int tile_x, int tile_y [, bool animation])
* [Wrench](#Wrench)(int tile_x, int tile_y)
* [Use](#Use)()
* [Respawn](#Respawn)()
* [Wear](#Wear)(int item_id)
* [SendPacket](#SendPacket)(int type, string packet)
* [SendPacktRaw](#SendPacktRaw)(GamePacket packet)
* [Drop](#Drop)(int item_id [, amount])
* [Trash](#Trash)(int item_id [, amount])
* [FindItem](#FindItem)(int item_id)
* [AddCallback](#AddCallback)(string callback_name, int callback_type, void* function)
* [RemoveCallback](#RemoveCallback)(string callback_name)
* [RemoveCallbacks](#RemoveCallbacks)()
* [GetWorld](#GetWorld)()
* [GetItems](#GetItems)()
* [GetObjects](#GetObjects)()
* [GetTiles](#GetTiles)()
* [GetTile](#GetTile)(int tile_x, int tile_y)
* [GetPlayers](#GetPlayers)()
* [GetGhost](#GetGhost)()
* [FindPlayer](#FindPlayer)(string name [, bool case_sensitive])
* [IsWearing](#IsWearing)(int item_id)

## Connect
`ENetClient:Connect(bool Connect)`

Connect the bot. (Reconnect if already connected)
Example:
```lua
-- Connect the bot
bot:Connect(true)
```

## Disconnect
`ENetClient:Disconnect(bool reset)`

Disconnect the bot
Example:
```lua
-- Disconnect the bot and reset the information
bot:Disconnect(true)
```

## Say
`ENetClient:Say(string message)`

The bot sends a packet to send a chat.

Example:
```lua
-- Check the bot's gem amount
bot:Say("I have %d gems", bot.gems)
```

## Move
`ENetClient:Move(int direction [, ...])`

Moves the bot.\
For the value of parameters, refer to [Directions](Defines.md#Directions)

Example:
```lua
-- Moves the bot left twice, right once, up once, down once
bot:Move(LEFT, LEFT, RIGHT, UP)
-- Don't make too many moves at once
Sleep(1000)
bot:Move(DOWN)
```

## Enter
`ENetClient:Enter()`

Enter the door at the bot's tile position.
Example:
```lua
-- Enter the door
bot:Enter()
```

## FindPath
`ENetClient:FindPath(int tile_x, int tile_y [, int delay_ms])`

Moves the bot to that tile position regardless of distance.\
Returns true if the move was successful, false if it failed.

Example:
```lua
local success = bot:FindPath(23, 10)
print(success and "success!" or "failed!")
```

## Warp
`ENetClient:Warp(string world_name [, string door_id])`

Make the bot warp to the world.
Example:
```lua
-- Warp without door id
bot:Warp("INDONESIA")
-- Warp with doorid
bot:Warp("INDONESIA", "HARGAMATI")
```

## Collect
`ENetClient:Collect(int radius [, bool force collect])`

Collect items within range.
Example:
```lua
-- Collect without force collect
bot:Collect(3)
-- Collect with force collect
bot:Collect(3, true)
```

## CollectSet
`ENetClient:CollectSet(bool collect, int radius [, int delay, bool force])`

Auto Collect items within range.
Example:
```lua
-- Collect set without delay and force
bot:CollectSet(true, 3)
-- Collect set with force collect and delay
bot:CollectSet(true, 3, 100, true)
```

## Punch
`ENetClient:Punch(int tile_x, int tile_y [, bool animation])`

The bot will hit that tile.
Example:
```lua
bot:Punch(54, 24)
```

## Place
`ENetClient:Place(int tile_x, int tile_y, int item_id [, bool animation])`

The bot will place an item on that tile.
Example:
```lua
bot:Place(54, 24, 2)
```

## Wrench
`ENetClient:Wrench(int tile_x, int tile_y)`

The bot will wrench that tile. You can check the dialog using the [AddCallback](#AddCallback) function.
Example:
```lua
bot:Wrench(54, 24)
```

## Use
`ENetClient:Use()`

Use the block in the bot's current tile.
Example:
```lua
bot:Use()
```

## Wear
`ENetClient:Wear(int item_id)`

The bot will wear the item.
Example:
```lua
bot:Wear(48)
```

## SendPacket
`ENetClient:SendPacket(int type, string packet)`

Sends text packet with selected type to server.
Example:
```lua
bot:SendPacket(3, "action|join_request\nname|INDONESIA\ninvitedWorld|0")
```

## SendPacketRaw
`ENetClient:SendPacketRaw(GamePacket packet)`

Sends GamePacket to server.
Example:
```lua
rawpacket = {}
rawpacket.type = 0
rawpacket.pos_x = 0
rawpacket.pos_y = 0
rawpacket.flags = 34
bot:SendPacketRaw(rawpacket)
```

## Drop
`ENetClient:Drop(int item_id [, amount])`

Make the bot drop an item.
Example:
```lua
bot:Drop(2) -- Drop all item in inventory with specific itemid

bot:Drop(2, 200) -- Drop item with specific amount
```

## Trash
`ENetClient:Trash(int item_id [, amount])`

Make the bot trash the item.
Example:
```lua
bot:Trash(2) -- Drop items without the amount of aliases of all

bot:Drop(2, 200) -- Drop items with the amount
```

## FindItem
`ENetClient:FindItem(int item_id)`

Finds an item in the bot's inventory by ID and returns the [InventoryItem](Structs.md#InventoryItem) struct of that item.
Returns `NULL` if not found

Example:
```lua
local item = bot:FindItem(98)
if item then
   bot:Say("I have %d %s.", item.amount, GetItemInfo(item.id).name)
end
```

## AddCallback
`ENetClient:AddCallback(string callback_name, int callback_type, void* function)`
Example:
```lua
bot:AddCallback("Sebuah kata cinta", 3, function(text)
print(text)
)
```

## RemoveCallback
`ENetClient:RemoveCallback(string callback_name)`
Example:
```lua
bot:RemoveCallback("Sebuah kata cinta")
```


## RemoveCallbacks
`ENetClient:RemoveCallbacks()` # Remove all callbacks ! 


## GetWorld
`ENetClient:GetWorld()`
returns the [World](Structs.md#World) struct of that world.
Example:
```lua
bot:GetWorld().name
```

## GetItems
`ENetClient:GetWorld()`
Return the structure of the [InventoryItem](Structs.md#InventoryItem) table from the Item.
Example:
```lua
for index, item in pairs(bot:GetItems()) do
	print(item.id)
end
```

## GetObjects
`ENetClient:GetObjects()`
Return the structure of the [WorldObject](Structs.md#WorldObject) table from the objects.
Example:
```lua
for index, object in pairs(bot:GetObjects()) do
	print(object.id)
end
```

## GetTiles
`ENetClient:GetTiles()`
Return the structure of the [WorldTile](Structs.md#WorldTile) table from the tiles.
Example:
```lua
for index, tile in pairs(bot:GetTiles()) do
	print(tile.fg)
end
```

## GetTile
`ENetClient:GetTile(int tile_x, int tile_y)`
Return the structure of the [WorldTile](Structs.md#WorldTile) table from the tile.
Example:
```lua
print(bot:GetTile(23,34).fg)
```

## GetPlayers
`ENetClient:GetPlayers()`
Return the structure of the [NetAvatar](Structs.md#NetAvatar) table from the players.
Example:
```lua
for id, player in pairs(bot:GetPlayers()) do
    -- id is netid
	print(player.name) -- u need to remove colors
end
```

## GetGhost
`ENetClient:GetGhost()`
Return the structure of the [WorldGhost](Structs.md#WorldGhost) table from the ghost.
Example:
```lua
for id, ghost in pairs(bot:GetGhost()) do
    -- id is ghostid
	print(ghost.ghostype)
end
```

## FindPlayer
`ENetClient:FindPlayer(string name [, bool case_sensitive])`
Return the structure of the [NetAvatar](Structs.md#NetAvatar) table from the players.
Example:
```lua
print(bot:FindPlayer("INDONESIA", true).name)
```

## IsWearing
`ENetClient:IsWearing(int item_id)`
Return the boolean.
Example:
```lua
if bot:IsWearing(48) then
print("hehe-heha")
end
```


