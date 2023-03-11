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
* GetPing
* Move
* Enter
* FindPath
* Warp
* Collect
* Punch
* Place
* Wrench
* Use
* Wear
* SendPacket
* SendPacktRaw
* Connect
* Disconnect
* Drop
* Trash
* AddCallback
* RemoveCallback
* RemoveCallbacks
* GetWorld
* GetInventory
* Collect

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
`ENetClient:Move(int direction)`

Move the bot.\
For the value of parameter 1, refer to [Directions](Defines.md#Directions)

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
