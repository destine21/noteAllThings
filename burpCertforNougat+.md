Install Burp Cert to Android version 7 or more
===

1. Create pem cert file and rename it to hash by following command
```sh
openssl x509 -inform DER -in cacert.der -out cacert.pem  
openssl x509 -inform PEM -subject_hash_old -in cacert.pem |head -1  //return hash
mv cacert.pem <hash>.0  
```

2. Copy the certificate to the device 
```sh
adb push <cert>.0 /sdcard/ 
adb shell
setenforce 0 
mount -o rw,remount /system

mv /sdcard/<cert>.0 /system/etc/security/cacerts/  
chmod 644 /system/etc/security/cacerts/<cert>.0  
reboot
```


Reference https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/#installburpcaasasystemleveltrustedca