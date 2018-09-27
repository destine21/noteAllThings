Frida
===

### List running processes of USB device
        frida-ps -U

### Spawn app & Loadscript
        frida -U -l script.js -f com.android.chrome --no-pause

### Remote spawn app & Loadscript
Run frida server with

        ./frida-server -l 0.0.0.0

frida command:

        frida -H 192.168.1.xx -l script.js -f com.android.chrome --no-pause

### Fix 
run this before frida-server

        setenforce 0

### Example frida script
---
script.js
```js
setImmediate(function() {
    Java.perform(function () {
    // Function to hook is defined here
    var MainActivity = Java.use('com.example.seccon2015.rock_paper_scissors.MainActivity');

    // Whenever button is clicked
    MainActivity.onClick.implementation = function (v) {
        // Show a message to know that the function got called
        send('onClick');

        // Call the original onClick handler
        this.onClick(v);

        // Set our values after running the original onClick handler
        this.m.value = 0;
        this.n.value = 1;
        this.cnt.value = 999;

        // Log to the console that it's done, and we should have the flag!
        console.log('Done:' + JSON.stringify(this.cnt));
    };
});
});
```