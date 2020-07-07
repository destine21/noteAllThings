# Get ipa from iOS

## frida-ios-dump (https://github.com/AloneMonkey/frida-ios-dump)
Pull a decrypted IPA from a jailbroken device

1. Install frida on device
2. sudo pip install -r requirements.txt --upgrade
3. Run usbmuxd/iproxy SSH forwarding over USB (Default 2222 -> 22). e.g. iproxy 2222 22
4. Run ./dump.py Display name or Bundle identifier


## Kungfu Extract IPA from iPhone (encrypted ipa)
On iPhone:
$ cd /var/containers/Bundle/Application/
$ ls * | grep -i "<keyword_of_appname>"
-------------------
Example output:
9FDC2EB8-B08E-440A-93F4-958F8CB2C2A5:
BundleMetadata.plist
SCB-FastEasy.app/
-------------------
$ mkdir Payload
$ cp -r SCB-FastEasy.app/ Payload/
$ zip -r /var/root/IPA/SCB_UAT_25022020.ipa Payload/

On Mac:
$ scp -P <port> root@<ip>:/var/root/IPA/SCB_UAT_25022020.ipa .
