## Firebase firestore pentest

The firebase read/write authorization should be checked by guest role and low priv role.

## firebase proxy issue
https://github.com/firebase/firebase-js-sdk/issues/2923#issuecomment-630382211
Use the following setting:
    
    firebase.firestore().settings({ experimentalForceLongPolling: true });

## find firebase configuration
For webapp
```js
// firebase config
firebase.initializeApp({
  apiKey: '### FIREBASE API KEY ###',
  authDomain: '### FIREBASE AUTH DOMAIN ###',
  projectId: '### CLOUD FIRESTORE PROJECT ID ###'
});
```

for Android search .firebaseio.com in the sourcecode
<string name="firebase_database_url">https://{projectId}.firebaseio.com</string>

## curl to get firestore token

  curl 'https://identitytoolkit.googleapis.com/v1/accounts:signInWithCustomToken?key=[API_KEY]' -H 'Content-Type: application/json' --data-binary '{"token":"[CUSTOM_TOKEN]","returnSecureToken":true}'

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

## firestore crud
https://medium.com/@aaron_lu1/firebase-cloud-firestore-add-set-update-delete-get-data-6da566513b1b

## secure the rule
- https://firebase.google.com/docs/firestore/security/rules-structure
- https://firebase.google.com/docs/rules/rules-language