**←** [Back to main](Main.md)

# Defines
* [Directions](#Directions)
* [CallbackTypes](#CallbackTypes)
* [GeigerSignal](#GeigerSignal)

## Directions
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`UP`|0|
|Number|`DOWN`|1|
|Number|`LEFT`|2|
|Number|`RIGHT`|3|

* [ENetClient:Move](Functions.md#Move)(`int direction [, ...]`)

## CallbackTypes
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`VARIANTLIST`||
|Number|`GAMEMESSAGE`||
|Number|`GAMEPACKET`||
|Number|`TRACKPACKET`||

* [ENetClient:AddCallback](Functions.md#AddCallback)(string callback_name, `int callback_type`, void* function)

## GeigerSignal
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`SIGNAL_NONE`|0|
|Number|`SIGNAL_RED`|1|
|Number|`SIGNAL_YELLOW`|2|
|Number|`SIGNAL_GREEN`|3|
