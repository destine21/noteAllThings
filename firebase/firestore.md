## Firebase firestore pentest

The firebase read/write authorization should be checked by guest role and low priv role.

## firebase proxy issue
https://github.com/firebase/firebase-js-sdk/issues/2923#issuecomment-630382211
Use the following setting:
    
    firebase.firestore().settings({ experimentalForceLongPolling: true });

## find firebase configuration
```js
// firebase config
firebase.initializeApp({
  apiKey: '### FIREBASE API KEY ###',
  authDomain: '### FIREBASE AUTH DOMAIN ###',
  projectId: '### CLOUD FIRESTORE PROJECT ID ###'
});
```

## find all firestore collection name
By searching for the following keyword:
    
    db.collection('products')

## firestore rest (https://firebase.google.com/docs/firestore/use-rest-api)
https://firestore.googleapis.com/v1/projects/{projectId}/databases/(default)/documents/{collection}

## firestore js query
db = firebase.firestore()
db.collection('products').get().then(res => {res.docs.forEach(e => console.log(e.data()))})

## firestore hacking guide
https://www.youtube.com/watch?v=b7PUm7LmAOw

## Role base implement
https://firebase.google.com/docs/firestore/solutions/role-based-access