# Variants

- [OnSendToServer](#onsendtoserver)
- [OnOverrideGDPRFromServer](#onoverridegdprfromserver)
- [OnSetRoleSkinsAndTitles](#onsetroleskinsandtitles)
- [OnSuperMainStartAcceptLogonHrdxs47254722215a](#onsupermainstartacceptlogonhrdxs47254722215a)
- [OnConsoleMessage](#onconsolemessage)
- [SetHasAccountSecured](#sethasaccountsecured)
- [OnTodaysDate](#ontodaysdate)
- [SetShowChatOnlyFromFriends](#setshowchatonlyfromfriends)
- [OnSetClothing](#onsetclothing)
- [OnCountryState](#oncountrystate)
- [OnSetPos](#onsetpos)
- [OnSetCurrentWeather](#onsetcurrentweather)
- [OnSetFreezeState](#onsetfreezestate)
- [OnRemove](#onremove)
- [OnSpawn](#onspawn)
- [OnFlagMay2019](#onflagmay2019)
- [OnDialogRequest](#ondialogrequest)
- [OnNameChanged](#onnamechanged)
- [OnTalkBubble](#ontalkbubble)

## OnSendToServer

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnSendToServer
- `1` | `SIGNED` - Port of the enet server.
- `2` | `SIGNED` - Token. Random number and max by userid?
- `3` | `SIGNED` - User. Userid increment from 0.
- `4` | `STRING` - `IP|doorID|UUIDToken`, the first is the ip of the enet server and the second is the doorID and the third is the UUIDToken. The UUIDToken random algorithm same as RID.
- `5` | `SIGNED` - lmode/Login mode.

## OnOverrideGDPRFromServer

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnOverrideGDPRFromServer
- `1` | `SIGNED` - Player age.
- `2` | `SIGNED` - Unknown.
- `3` | `SIGNED` - Unknown.

## OnSetRoleSkinsAndTitles

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnSetRoleSkinsAndTitles
- `1` | `STRING` - Role skins.
- `2` | `STRING` - Titles.

## OnSuperMainStartAcceptLogonHrdxs47254722215a

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnSuperMainStartAcceptLogonHrdxs47254722215a
- `1` | `UNSIGNED` - items.dat proton hash.
- `2` | `STRING` - CDN host.
- `3` | `STRING` - CDN cache path.
- `4` | `STRING` - Blocked package name for android?
- `5` | `UNSIGNED` - playertribute.dat proton hash.

## OnConsoleMessage

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnConsoleMessage
- `1` | `STRING` - Message to show on chat box.

## SetHasAccountSecured

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - SetHasAccountSecured
- `1` | `UNSIGNED` - 0 or 1.

## OnTodaysDate

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnTodaysDate
- `1` | `SIGNED` - Month.
- `2` | `SIGNED` - Day. `4 April 2100` means the value is `4`.
- `3` | `UNSIGNED` - Unknown, some unix time probably.
- `4` | `UNSIGNED` - Unknown.

## SetShowChatOnlyFromFriends

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - SetShowChatOnlyFromFriends
- `1` | `UNSIGNED` - 0 or 1.

## OnSetClothing

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnSetClothing
- `1` | `VECTOR3` - Hair, Shirt, Pants. `0, 0, 0`
- `2` | `VECTOR3` - Feet, Face, Hand. `0, 0, 0`
- `3` | `VECTOR3` - Back, Mask, Necklace. `0, 0, 0`
- `4` | `UNSIGNED` - Skin color.
- `5` | `VECTOR3` - Ances, unknown, unknown. `0, 0, 0`

## OnCountryState

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnCountryState
- `1` | `STRING` - Country. `country_code|extra_flag`

## OnSetPos

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnSetPos
- `1` | `VECTOR2` - Pos, `x, y`

## OnSetCurrentWeather

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnSetCurrentWeather
- `1` | `SIGNED` - Weather id.

## OnSetFreezeState

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnSetFreezeState
- `1` | `SIGNED` - 0 or 1.

## OnRemove

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnRemove
- `1` | `STRING` - `netID|number`

## OnSpawn

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

- `0` | `STRING` - OnSpawn
- `1` | `STRING` - SpawnData

SpawnData:

- `netID` - The NetID of the user. Used by other game packets.
- `userID` - The account ID of the user. (for example, an ID of 140 means this is the 140th GrowID created)
- `country` - The two letter country code that the player is from. Examples: `us`, `id`, `jp`
- `name` - The name of the user
- `posXY` - The user position. `x|y`
- `colrect` - The width (20) and height (30) of the bounding box of the player. Used for collision. `0|0|20|30`
- `invis` - The invisibility status of the player. If invisible, doesn't render.
- `mstate` - If the player is a mod, this is bigger than zero. Can see invisible players that don't have an smstate set
- `smstate` - If the player is a developer, this is bigger than zero. Can see all invisible players' faces
- `type` - Whether the player is controlled by the peer or not. Leave it out entirely if this is a player that isn't controlled by the user

## OnFlagMay2019

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnFlagMay2019
- `1` | `STRING` - Flags

Flags: [OnFlagMay2019 Flags](#onflagmay2019-flags)

## OnDialogRequest

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnDialogRequest
- `1` | `STRING` - DialogStr

## OnNameChanged

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnNameChanged
- `1` | `STRING` - Name
- `2` | `STRING` - Unknown `||`

## OnTalkBubble

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnTalkBubble
- `1` | `UNSIGNED` - Target NetID
- `2` | `STRING` - Message
- `3` | `UNSIGNED` - Stack text bubble, `0` or `1`

## OnTextOverlay

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:

- `0` | `STRING` - OnTextOverlay
- `1` | `STRING` - Message

## OnPlayPositioned

From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:

- `Net ID`

Variant:

- `0` | `STRING` - OnPlayPositioned
- `1` | `STRING` - Audio file location. `audio/object_spawn.wav`
