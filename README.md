# GTPrivateServer-docs

- [Type definitions](#type-definitions)
- [HTTP](#server_dataphp)
- Message type 2
  - [Login info](#login-info)
- Message type 4
  - Packet type 1
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

## Type definitions

```cpp
enum VariantType : uint8_t {
  UNKNOWN,
  FLOAT,
  STRING,
  VECTOR2,
  VECTOR3,
  UNSIGNED,
  SIGNED = 9
}
```

## server_data.php

From: HTTP server, Type: HTTP

Body:

- `server|` - The enet server ip.
- `port|` - The enet server port.
- `type|` - Unknown.
- `maint|` - Maintenance message.
- `beta_server|` - The beta enet server ip.
- `beta_port|` - The beta enet server port.
- `beta_type|` - Unknown.
- `beta_server2|` - The beta 2 enet server ip.
- `beta_port2|` - The beta 2 enet server port.
- `beta_type2|` - Unknown.
- `type2|` - To use with new packet.
- `meta|` - Metadata to send back to server?
- `RTENDMARKERBS1001` - This is marker for end of data (From ProtonSDK).

## Login info

From: ENet client, Message type: 2, Type: Text

Text:

- `requestedName|` - Guest name.
- `tankIDName|` - GrowID name.
- `tankIDPass|` - GrowID pass.
- `f|` - Swear Filter.
- `protocol|` - Protocol.
- `game_version|` - The game version.
- `fz|` - Game file size.
- `lmode|` - Login mode. 0 login normally, 1 same like mode 0 but without logging on message, 2 login with auto enter to world offers/world, also get from OnSendToServer
- `cbits|` - Client bits. if age under `12` the client bits will add `16`. `2` is check_no_friend_add, `4` is check_hide_signs, `8` is check_hide_iap, `16` is check_hide_tapjoy, `32` is check_broadcasts, `64` is check_no_guild_add, `128` is check_no_guild_flag, `256` is disable_billboard, `512` is use_store_classic. Saved to `save.dat` as `"Client"`.
- `GDPR|` - This after accepted terms, eula, etc and maybe from OnOverrideGDPRServer. `1` if your age over `12`, `2` if the country en_US, en_us, US and USA, `3` if not from en_US, en_us, US and USA.
- `category|` - Unknown.
- `gid|` - Ubisoft account/global id, android only.
- `hash2|` - Mac hash.
- `meta|` - From server_data.php.
- `fhash|` - Hash of all login info without value (e.g. `meta|`) exclude `zf|`, `UUIDToken|`, `tr|`.
- `rid|` - Generate random one time if no `"rid"` in `save.dat`, maybe length from `30-34` and saved to `save.dat` as `"rid"`.
- `platformID|` - The platfrom id, 0 if windows.
- `deviceVersion|` - OS version.
- `country|` - Country.
- `hash|` - Device id hash.
- `mac|` - Mac.
- `user|` - Get from OnSendToServer.
- `token|` - Get from OnSendToServer.
- `UUIDToken|` - Get from OnSendToServer.
- `wk|` - Cryptography info from registry `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography` and `Computer\HKEY_CURRENT_USER\Software\Microsoft\29549`. `NONE0` if not found `Cryptography\MachineGuid`, `NONE1` if not found `29549\*`, `NONE2` if not found ??. Android always return `NONE0`
- `zf|` - Maybe the binary data hash? windows only.
- `aid|` - Advertising id.
- `tr|` - Cant support trees, `0` if detected root apk else `4322` android only.
- `vid|` - Not used.
- `ProductId` - Not used. Note: this without `|`
- `doorID|` - Get from OnSendToServer.

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

- `0` | `STRING` - OnSpawn
- `1` | `STRING` - SpawnData

SpawnData:

- `netID` - The NetID of the user. Used by other game packets.
- `userID` - The account ID of the user. (for example, an ID of 140 means this is the 140th GrowID created)
- `country` - The two letter country code that the player is from. Examples: `us`, `id`, `jp`
- `name` - The name of the user.
- `posXY` - The user position. `x|y`
- `colrect` - The width (20) and height (30) of the bounding box of the player. Used for collision. `0|0|20|30`
- `invis` - The invisibility status of the player. If invisible, doesn't render.
- `mstate` - If the player is a mod, this is bigger than zero. Can see invisible players that don't have an smstate set.
- `smstate` - If the player is a developer, this is bigger than zero. Can see all invisible players' faces.
- `type` - Whether the player is controlled by the peer or not. Leave it out entirely if this is a player that isn't controlled by the user.
