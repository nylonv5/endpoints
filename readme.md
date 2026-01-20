# Snapchat Endpoint
```curl
grpcurl -H "x-snap-access-token: TOKEN" -H "user-agent: Snapchat/13.75.0.47" -import-path . -proto closet_v3.proto -d "{}" aws.api.snapchat.com:443 snapchat.bitmoji.fashion.v1.Closet/GetItems
```
