# Firebase Cloud Messaging

Find the *server_key* with the followings regEx pattern:
```
AIzaSy[0-9A-Za-z_-]{33}
AAAA[a-zA-Z0-9_-]{7}:[a-zA-Z0-9_-]{140}
```

Send notification with curl
```sh
api_key=YOUR_SERVER_KEY

curl --header "Authorization: key=$api_key" \
     --header Content-Type:"application/json" \
     https://fcm.googleapis.com/fcm/send \
     -d "{\"registration_ids\":[\"Test\"]}"

```

## Ref
    https://abss.me/posts/fcm-takeover/