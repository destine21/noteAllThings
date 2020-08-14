# Firestorage pentest


## firebase config

```js
  // Set the configuration for your app
  // TODO: Replace with your app's config object
  var firebaseConfig = {
    apiKey: '<your-api-key>',
    authDomain: '<your-auth-domain>',
    databaseURL: '<your-database-url>',
    storageBucket: '<your-storage-bucket-url>'
  };
  firebase.initializeApp(firebaseConfig);

  // Get a reference to the storage service, which is used to create references in your storage bucket
  var storage = firebase.storage();
```

## list all file
https://firebasestorage.googleapis.com/v0/b/{storageBucket}/o


## file content
https://firebasestorage.googleapis.com/v0/b/{storageBucket}/o/{fileRef}?alt=media

https://firebasestorage.googleapis.com/v0/b/test1-48473.appspot.com/o/images%2fgrey.png?alt=media

## firestrage with js
```js 
    // Create a reference with an initial file path and name
    var storage = firebase.storage();
    var storageRef = storage.ref();
    var pathReference = storage.ref('images/stars.jpg');

    // get url
    pathReference.getDownloadURL().then(res => console.log(res));

    // delete
    pathReference.delete().then(res => console.log(res));
```

## Ref
- https://firebase.google.com/docs/rules/rules-language
- https://firebase.google.com/docs/storage/web/start
- https://firebase.google.com/docs/storage/security
- https://firebase.google.com/docs/storage/security/secure-files#full_example