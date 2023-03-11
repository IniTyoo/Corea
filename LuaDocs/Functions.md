**←** [Back to main](Main.md)

# Functions
* [Basic Functions](#Basic-Functions)
* [ENetClient Functions](#ENetClient-Functions) (Bot)
* [World Functions](#World-Functions)
* [NetAvatar Functions](#NetAvatar-Functions) (Player)

## Basic Functions
* [Sleep](#Sleep)
* [GetBots](#GetBots)
* [GetSelectedBots](#GetSelectedBots)
* [GetBot](#GetBot)
* [AddBot](#AddBot)
* [RemoveBot](#RemoveBot)
* RunFile
* StopFile
* RunThread
* GetItemInfo
* HttpGet
* RequireFromUrl

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
local bots = GetBots()
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
* [Say](#Say)
* [GetPing](#GetPing)
* [Move](#Move)
* [Enter](#Enter)
* [FindPath](#FindPath)
* [Warp](#Warp)
* [Collect](#Collect)
* [Punch](#Punch)
* [Place](#Place)
* [Wrench](#Wrench)
* [Use](#Use)
* [Wear](#Wear)
* [SendPacket](#SendPacket)
* [SendPacktRaw](#SendPacktRaw)
* [Connect](#Connect)
* [Disconnect](#Disconnect)
* [Drop](#Drop)
* [Trash](#Trash)
* [AddCallback](#AddCallback)
* [RemoveCallback](#RemoveCallback)
* [RemoveCallbacks](#RemoveCallbacks)
* [GetWorld](#GetWorld)
* [GetInventory](#GetInventory)

## Say
`ENetClient:Say(string pattern [, ...])`

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

## Collect
`ENetClient:Collect(int radius)`

## Punch
`ENetClient:Punch(int tile_x, int tile_y [, bool animation])`

## Place
`ENetClient:Place(int tile_x, int tile_y, int item_id [, bool animation])`

## Wrench
`ENetClient:Wrench(int tile_x, int tile_y)`

## Use
`ENetClient:Use()`

## Wear
`ENetClient:Wear(int item_id)`

## SendPacket
`ENetClient:SendPacket(int type, string packet)`

## SendPacketRaw
`ENetClient:SendPacketRaw(table packet)`

## Connect
`ENetClient:Connect()`

## Disconnect
`ENetClient:Disconnect()`

## Drop
`ENetClient:Drop(int item_id [, amount])`

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
