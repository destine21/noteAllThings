# Firebase Cloud Messaging

Find the *server_key* with the followings regEx pattern:
```
AIzaSy[0-9A-Za-z_-]{33}
AAAA[a-zA-Z0-9_-]{7}:[a-zA-Z0-9_-]{140}
```

## Check key validity
```sh
api_key=YOUR_SERVER_KEY

curl --header "Authorization: key=$api_key" \
     --header Content-Type:"application/json" \
     https://fcm.googleapis.com/fcm/send \
     -d "{\"registration_ids\":[\"Test\"]}"

```

## Send noti
```
POST /fcm/send HTTP/1.1
Host: fcm.googleapis.com
Authorization: key=AAAAmtutpjA:....
Content-type:application/json
Content-Length: 177

{
  "to": "/topics/news",
  "notification": {
    "title": "Breaking News",
    "body": "New news story available."
  },
  "data": {
    "story_id": "story_12345"
  }
}
```

## Send noti legacy to v1
https://firebase.google.com/docs/cloud-messaging/migrate-v1

## Ref
    https://abss.me/posts/fcm-takeover/
    https://firebase.google.com/docs/cloud-messaging/server