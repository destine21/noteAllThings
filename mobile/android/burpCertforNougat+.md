# Install Burp Cert to Android version 7 or more
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
su
setenforce 0 
mount -o rw,remount /system

mv /sdcard/<cert>.0 /system/etc/security/cacerts/  
chmod 644 /system/etc/security/cacerts/<cert>.0  
reboot
```


Reference https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/#installburpcaasasystemleveltrustedca

## Or use Frida script Universal 
https://codeshare.frida.re/@pcipolloni/universal-android-ssl-pinning-bypass-with-frida/


## Fix certificate too long
Using Burp 1.17.15, Chrome 55.0.2883.91, Android 6.0.1 (CyanogenMod 13 on a Nexus 6), I encountered the same issue.  I worked around this problem by generating my own certificate and re-importing. 

***Details***
I used the following commands to generate the PKCS#12 keystore:
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout pk.key -out certificate.crt
openssl pkcs12 -export -out certificate.p12 -inkey pk.key -certfile certificate.crt -in certificate.crt

I also was able to push a converted certificate into my Android cert store /system/etc/security/cacerts/ . To do that, I wrote a script to convert the DER certificate to the Android format on Github.  https://github.com/oemunlock/burp_der_cert_to_android_cert

After importing the certificate in Burp and restarting Burp, I downloaded it to my PC by viewing the Burp Proxy page (localhost:8080) and downloading the cacert.der file. After that, I used the script above and it generates a file that looks like 9a5ba575.0. From there, I ran:

adb root && adb wait-for-device remount && adb wait-for-device push [name of cert] /system/etc/security/cacerts/[name of cert]

Then checked the permissions on the file:  adb shell ls -al -Z /system/etc/security/cacerts/* to make sure everything was okay and rebooted the phone.

