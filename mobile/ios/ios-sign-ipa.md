## iOS sign ipa
- สร้างไฟล์ .mobileprovision (https://github.com/sensepost/objection/wiki/Patching-iOS-Applications)
- ติดตั้ง applesign ($ npm install -g applesign)
- หา Apple Developer identity ที่เป็น 40-digit hex ($ security find-identity -p codesigning -v)
- $ applesign -r -i <developer-identity> -m <.mobileprovision> -c <.ipa>