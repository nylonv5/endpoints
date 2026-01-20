# Snapchat Endpoint
REPLACE TOKEN WITH YOUR TOKEN

(GetItems From Closet)
```curl
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto closet_v3.proto -d "{}" aws.api.snapchat.com:443 snapchat.bitmoji.fashion.v1.Closet/GetItems
```
(AddItems to your Closet)
```curl
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto closet_v3.proto -d @ < payload_additems.json aws.api.snapchat.com:443 snapchat.bitmoji.fashion.v1.Closet/AddItems
```
(Using payload_additems.json)
```
{
  "field1": {
    "8": {
      "field1": 5001203,
      "field2": 8381440,
      "field3": -7149601,
      "field4": -1226402,
      "field5": -1484032,
      "field6": -1484032,
      "field7": -1484032,
      "field8": -1484032,
      "field9": -1484032
    }
  }
}
```
(Using closet_v3.proto)
```
syntax = "proto3";

package snapchat.bitmoji.fashion.v1;

service Closet {
  rpc GetItems(GetItemsRequest) returns (GetItemsResponse);
  rpc AddItems(AddItemsRequest) returns (AddItemsResponse);
}

message GetItemsRequest {
  repeated sint32 field1 = 1;
}

message GetItemsResponse {
  repeated Category categories = 1;
}

message AddItemsRequest {
  map<int32, ToneEntry> field1 = 1;  
}

message AddItemsResponse {
 
}

message Category {
  repeated Item items = 1;
}

message Item {
  sint64 field1 = 1;
  repeated ToneEntry field2 = 2;
  sint64 field3 = 3;
  sint64 field4 = 4;
  sint64 field5 = 5;
}

message ToneEntry {
  sint64 field1 = 1;
  sint64 field2 = 2;
  sint64 field3 = 3;
  sint64 field4 = 4;
  sint64 field5 = 5;
  sint64 field6 = 6;
  sint64 field7 = 7;
  sint64 field8 = 8;
  sint64 field9 = 9;
}

```

# Create Avatar (PAID)

CreateAvatar endpoint (Must be POSTed when a NEW account is made to own the items BEFORE you create your bitmoji)
```
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto avatar.proto -d @ < payload.json aws.api.snapchat.com:443 snapchat.bitmoji.avatar.v1.Avatar/CreateAvatar
```
(Using payload.json)
```
{
  "data": {
    "gender": -1,
    "style": -3,
    "options": [
      {"key": "jaw", "value": -698},
      {"key": "brow", "value": 784},
      {"key": "eye", "value": -813},
      {"key": "nose", "value": -721},
      {"key": "mouth", "value": -1169},
      {"key": "ear", "value": -714},
      {"key": "skin_tone", "value": -8382029},
      {"key": "pupil_tone", "value": 2988558},
      {"key": "hair", "value": -671},
      {"key": "hair_tone", "value": 2397845},
      {"key": "beard", "value": -833},
      {"key": "beard_tone", "value": -2135827},
      {"key": "glasses", "value": -684},
      {"key": "cheek_details", "value": 826},
      {"key": "face_proportion", "value": 5},
      {"key": "clothing_type", "value": -1},
      {"key": "top", "value": -5001202},
      {"key": "top_tone1", "value": -8158718},
      {"key": "top_tone2", "value": 1250067},
      {"key": "top_tone3", "value": -8158718},
      {"key": "top_tone4", "value": -8158718},
      {"key": "top_tone5", "value": -8158718},
      {"key": "top_tone6", "value": -8158718},
      {"key": "top_tone7", "value": -8158718},
      {"key": "top_tone8", "value": -8158718},
      {"key": "top_tone9", "value": -8158718},
      {"key": "top_tone10", "value": -8158718},
      {"key": "bottom", "value": 5001203},
      {"key": "bottom_tone1", "value": 6932523},
      {"key": "bottom_tone2", "value": 6932523},
      {"key": "bottom_tone3", "value": 6932523},
      {"key": "bottom_tone4", "value": 6932523},
      {"key": "bottom_tone5", "value": 6932523},
      {"key": "bottom_tone6", "value": 6838984},
      {"key": "bottom_tone7", "value": 6932523},
      {"key": "bottom_tone8", "value": 6932523},
      {"key": "bottom_tone9", "value": 6932523},
      {"key": "bottom_tone10", "value": 6932523},
      {"key": "footwear", "value": 95},
      {"key": "footwear_tone1", "value": 8224125},
      {"key": "footwear_tone2", "value": 8224125},
      {"key": "footwear_tone3", "value": 8224125},
      {"key": "footwear_tone4", "value": 8224125},
      {"key": "footwear_tone5", "value": 8224125},
      {"key": "footwear_tone6", "value": -7072748},
      {"key": "footwear_tone7", "value": 8224125},
      {"key": "footwear_tone8", "value": -1249299},
      {"key": "footwear_tone9", "value": -7533299},
      {"key": "footwear_tone10", "value": -5126699},
      {"key": "sock", "value": -148},
      {"key": "sock_tone1", "value": -7993462},
      {"key": "sock_tone2", "value": -1843754},
      {"key": "sock_tone3", "value": -7993462},
      {"key": "sock_tone4", "value": -7993462}
    ]
  }
}
```
(Using avatar.proto)
```
syntax = "proto3";

package snapchat.bitmoji.avatar.v1;

service Avatar {
  rpc CreateAvatar(CreateAvatarRequest) returns (CreateAvatarResponse);
  rpc UpdateAvatar(UpdateAvatarRequest) returns (UpdateAvatarResponse);
  rpc GetAvatar(GetAvatarRequest) returns (GetAvatarResponse);
}

message CreateAvatarRequest {
  AvatarData data = 1;
}

message CreateAvatarResponse {
  ResponseData data = 1;
}

message UpdateAvatarRequest {
  AvatarData data = 1;
}

message AvatarData {
  sint32 gender = 1;
  sint32 style = 2;
  repeated OptionEntry options = 3;
}

message OptionEntry {
  string key = 1;
  sint64 value = 2;
}

message UpdateAvatarResponse {
  ResponseData data = 1;
}

message ResponseData {
  sint64 id = 1;
  sint64 field2 = 2;
  sint64 field3 = 3;
}

message GetAvatarRequest {
}

message GetAvatarResponse {
  AvatarData data = 1;
}
```
Get Avatar
```
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto avatar.proto -d "{}" aws.api.snapchat.com:443 snapchat.bitmoji.avatar.v1.Avatar/GetAvatar
```
Update Avatar (Same as CreateAvatar but sometimes doesn't let save paid items!)
```
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto avatar.proto -d @ < payload.json aws.api.snapchat.com:443 snapchat.bitmoji.avatar.v1.Avatar/UpdateAvatar
```
