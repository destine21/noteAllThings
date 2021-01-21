# Bypassing Certificate Pinning on Flutter-based Android app

* Extract libflutter.so from apk
* Use Ghidra to reverse libflutter.so
* Search for text "x509.cc"
* For 64bit search for 390 scalar and select the function that match with range from previous search (x509.cc)
* Copy the function pattern and replace the code below

## Ref
 - https://blog.nviso.eu/2019/08/13/intercepting-traffic-from-android-flutter-applications/
 - https://blog.nviso.eu/2020/05/20/intercepting-flutter-traffic-on-android-x64/

```js
function hook_ssl_verify_result(address)
{
  Interceptor.attach(address, {
    onEnter: function(args) {
      console.log("Disabling SSL validation")
    },
    onLeave: function(retval)
    {
      console.log("Retval: " + retval)
      retval.replace(0x1);
    }
  });
}
function disablePinning()
{
 var m = Process.findModuleByName("libflutter.so"); 
 var pattern = "ff 03 05 d1 fd 7b 0f a9 bc de 05 94 08 0a 80 52 48 00 00 39 16 54 40 f9 76 07 00 b4 c8 02 40 f9 28 07 00 b4 29 20 40 a9 f3 03 02 aa"
 
 var res = Memory.scan(m.base, m.size, pattern, {
  onMatch: function(address, size){
      console.log('[+] ssl_verify_result found at: ' + address.toString());
 
      // Add 0x01 because it's a THUMB function
      // Otherwise, we would get 'Error: unable to intercept function at 0x9906f8ac; please file a bug'
      hook_ssl_verify_result(address.add(0x00));
       
    }, 
  onError: function(reason){
      console.log('[!] There was an error scanning memory');
    },
    onComplete: function()
    {
      console.log("All done")
    }
  });
}
setTimeout(disablePinning, 1000)
```