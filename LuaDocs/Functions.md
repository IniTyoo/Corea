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
* RunFile(string filename)
* StopFile(string filename)
* RunThread(string thread_name, void* function [, ...])
* GetItemInfo(int item_id)
* HttpGet(string url)
* RequireFromUrl(string url)
* GetTileDistance(int x1, int y1, int x2, int y2)
* string:Split(string delimiter)
* string:RemoveColors()

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

## ENetClient Functions
* [Connect](#Connect)()
* [Disconnect](#Disconnect)()
* [Say](#Say)(string message)
* [GetPing](#GetPing)()
* [Move](#Move)(int direction [, ...])
* [Enter](#Enter)()
* [FindPath](#FindPath)(int tile_x, int tile_y [, int delay])
* [Warp](#Warp)(string world_name [, string door_id])
* [Collect](#Collect)(int radius)
* [Punch](#Punch)(int tile_x, int tile_y [, bool animation])
* [Place](#Place)(int tile_x, int tile_y, int item_id [, bool animation])
* [Wrench](#Wrench)(int tile_x, int tile_y)
* [Use](#Use)()
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
* [GetInventory](#GetInventory)()
* PasswordReply(string password [, int tile_x, int tile_y])
* Respawn()

## Connect
`ENetClient:Connect()`

Connect the bot. (Reconnect if already connected)

## Disconnect
`ENetClient:Disconnect()`

Disconnect the bot

## Say
`ENetClient:Say(string message)`

The bot sends a packet to send a chat.

Example:
```lua
-- Check the bot's gem amount
bot:Say("I have %d gems", bot.gems)
```

## GetPing
`ENetClient:GetPing()`

Returns bot's ping (ms)

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

## Collect
`ENetClient:Collect(int radius [, table whitelist_item_ids])`

Collect items within range.

## Punch
`ENetClient:Punch(int tile_x, int tile_y [, bool animation])`

The bot will hit that tile.

## Place
`ENetClient:Place(int tile_x, int tile_y, int item_id [, bool animation])`

The bot will place an item on that tile.

## Wrench
`ENetClient:Wrench(int tile_x, int tile_y)`

The bot will wrench that tile. You can check the dialog using the [AddCallback](#AddCallback) function.

## Use
`ENetClient:Use()`

Use the block in the bot's current tile.

## Wear
`ENetClient:Wear(int item_id)`

The bot will wear the item.

## SendPacket
`ENetClient:SendPacket(int type, string packet)`

Sends text packet with selected type to server.

## SendPacketRaw
`ENetClient:SendPacketRaw(GamePacket packet)`

Sends GamePacket to server.

## Drop
`ENetClient:Drop(int item_id [, amount])`

Make the bot drop an item.

## Trash
`ENetClient:Trash(int item_id [, amount])`

Make the bot trash the item.

## FindItem
`ENetClient:FindItem(int item_id)`

Finds an item in the bot's inventory by ID and returns the [InventoryItem](Structs.md#InventoryItem) struct of that item.\
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

## RemoveCallback
`ENetClient:RemoveCallback(string callback_name)`

## RemoveCallbacks
`ENetClient:RemoveCallbacks()`

## World Functions
* GetObjects
* GetTiles
* GetTile
* GetPlayers
* GetGhost
* FindPlayer

## NetAvatar Functions
* Kick
* Pull
* Ban
* Trade
* SendMsg
