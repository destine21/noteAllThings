## Firebase realtime database pentest
The firebase read/write authorization should be checked by guest role and low priv role.

## find firebase configuration
```js
// firebase config
var firebaseConfig = {
    apiKey: "AIzaSyD5vEO8AcrQj7qxAwNamIK6MGhtzJdClYQ",
    authDomain: "test1-48473.firebaseapp.com",
    databaseURL: "https://test1-48473.firebaseio.com",
    projectId: "test1-48473",
    storageBucket: "test1-48473.appspot.com",
    messagingSenderId: "665110554160",
    appId: "1:665110554160:web:2f049d9868b9de1a1d2ff5"
  };
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
```

## find the document name
By searching for the following keyword:
    
    firebase.database().ref('/users/' + userId)

## realtime database rest (https://firebase.google.com/docs/database/rest/retrieve-data)
Put .json to the end of the database url

    https://test1-48473.firebaseio.com/.json
    https://test1-48473.firebaseio.com/.json?print=pretty //json pretty
    https://test1-48473.firebaseio.com/items/item1.json

    https://docs-examples.firebaseio.com/rest/saving-data/fireblog/users.json
    https://docs-examples.firebaseio.com/rest/saving-data/fireblog/posts.json?print=pretty
