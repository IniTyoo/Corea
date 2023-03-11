**←** [Back to main](Main.md)

# Functions
* [Basic Functions](#Basic-Functions)
* [ENetClient Functions (Bot)](#ENetClient-Functions)

## Basic Functions
* [GetBots](#GetBots)
* [GetSelectedBots](#GetSelectedBots)
* [GetBot](#GetBot)

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
The name in parameter 1 is not case sensitive and returns NULL if the bot is not found.

Example:
```lua
-- Print "found" if the bot was found or "not found" if not found
local bot = GetBot("seth")
print(bot and "found" or "not found")
```

## ENetClient Functions
