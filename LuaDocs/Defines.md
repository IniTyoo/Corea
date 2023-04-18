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
|Number|`VARIANTLIST`|0|
|Number|`GAMEMESSAGE`|1|
|Number|`GAMEPACKET`|2|
|Number|`TRACKPACKET`|3|

* [ENetClient:AddCallback](Functions.md#AddCallback)(string callback_name, `int callback_type`, void* function)

## GeigerSignal
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`SIGNAL_NONE`|0|
|Number|`SIGNAL_RED`|1|
|Number|`SIGNAL_YELLOW`|2|
|Number|`SIGNAL_GREEN`|3|
* [ENetClient.World.signal](Structs.md#World)

## MessageBoxType
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`MessageBoxType_None`|0|
|Number|`MessageBoxType_Success`|1|
|Number|`MessageBoxType_Warning`|2|
|Number|`MessageBoxType_Error`|3|
|Number|`MessageBoxType_Info`|4|
* [MessageBox](Functions.md#MessageBox)(string title,[, string content, int type, int dismiss_time])

## ENetPeerState
| Type | Variable | Value |
|:-----|:---------|:-----:|
|Number|`ENET_PEER_STATE_DISCONNECTED`|0|
|Number|`ENET_PEER_STATE_CONNECTING`|1|
|Number|`ENET_PEER_STATE_ACKNOWLEDGING_CONNECT`|2|
|Number|`ENET_PEER_STATE_CONNECTION_PENDING`|3|
|Number|`ENET_PEER_STATE_CONNECTION_SUCCEEDED`|4|
|Number|`ENET_PEER_STATE_CONNECTED`|5|
|Number|`ENET_PEER_STATE_DISCONNECT_LATER`|6|
|Number|`ENET_PEER_STATE_DISCONNECTING`|7|
|Number|`ENET_PEER_STATE_ACKNOWLEDGING_DISCONNECT`|8|
|Number|`ENET_PEER_STATE_ZOMBIE`|9|
* [ENetClient.state](Structs.md#ENetClient)