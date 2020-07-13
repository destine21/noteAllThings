# adb
---

Start a remote shell in the target emulator/device instance:

    adb shell
    adb shell -d <deviceId> // if multiple devices

Get a list of connected devices:

    adb devices

Check whether the adb server process is running and start it:

    adb start-server

Terminate the adb server process:

    adb kill-server

Push an Android application to an emulator/device:

    adb install path/to/file.apk

Copy a file/directory from the target device:

    adb pull path/to/device_file_or_directory path/to/local_destination_directory

Copy a file/directory to the target device:

    adb push path/to/local_file_or_directory path/to/device_destination_directory


adb over network

    adb connect 192.168.1.36:5555
    adb disconnect