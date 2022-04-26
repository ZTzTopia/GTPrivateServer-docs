# GTPrivateServer-docs

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
  - `cbits|` - Client bits. if age under `12` the client bits will add `16`.  `2` is check_no_friend_add, `4` is check_hide_signs, `8` is check_hide_iap, `16` is check_hide_tapjoy, `32` is check_broadcasts, `64` is check_no_guild_add, `128` is check_no_guild_flag, `256` is disable_billboard, `512` is use_store_classic. Saved to `save.dat` as `"Client"`.
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
  - `0` - OnSendToServer
  - `1` - Port of the enet server.
  - `2` - Token. Random number and max by userid?
  - `3` - User. Userid increment from 0.
  - `4` - `IP|doorID|UUIDToken`, the first is the ip of the enet server and the second is the doorID and the third is the UUIDToken. The UUIDToken random algorithm same as RID.
  - `5` - lmode/Login mode.

## OnOverrideGDPRFromServer
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - OnOverrideGDPRFromServer
  - `1` - Player age.
  - `2` - Unknown.
  - `3` - Unknown.

## OnSetRoleSkinsAndTitles
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - OnSetRoleSkinsAndTitles
  - `1` - Role skins.
  - `2` - Titles.

## OnSuperMainStartAcceptLogonHrdxs47254722215a
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - OnSuperMainStartAcceptLogonHrdxs47254722215a
  - `1` - items.dat proton hash.
  - `2` - CDN host.
  - `3` - CDN cache path.
  - `4` - Blocked package name for android?
  - `5` - playertribute.dat proton hash.

## OnConsoleMessage
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - OnConsoleMessage
  - `1` - Message to show on chat box.

## SetHasAccountSecured
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - SetHasAccountSecured
  - `1` - 0 or 1.

## OnTodaysDate
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - OnTodaysDate
  - `1` - Month.
  - `2` - What to say?? like `4 April 2100` means the value is `4`.

## SetShowChatOnlyFromFriends
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

Variant:
  - `0` - SetShowChatOnlyFromFriends
  - `1` - 0 or 1.

## OnSetClothing
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:
  - `Net ID`
  
Variant:
  - `0` - OnSetClothing
  - `1` - Hair, Shirt, Pants. `0, 0, 0`
  - `2` - Feet, Face, Hand. `0, 0, 0`
  - `3` - Back, Mask, Necklace. `0, 0, 0`
  - `4` - Skin color.
  - `5` - Ances, unknown, unknown. `0, 0, 0`

## OnCountryState
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant

GameUpdatePacket:
  - `Net ID`
  
Variant:
  - `0` - OnCountryState
  - `1` - Country. `country_code|extra_flag`

## OnSetPos
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant
  
Variant:
  - `0` - OnSetPos
  - `1` - Pos, `x, y`

## OnSetPos
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant
  
Variant:
  - `0` - OnSetCurrentWeather
  - `1` - Weather id.

## OnSetFreezeState
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant
  
Variant:
  - `0` - OnSetCurrentWeather
  - `1` - 0 or 1.

## OnSetFreezeState
From: ENet server, Message type: 4, Game update packet type: 1, Type: Variant
  
Variant:
  - `0` - OnSetCurrentWeather
  - `1` - 0 or 1.
