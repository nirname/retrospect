# ADB

Download adb from http://adbshell.com/downloads

```bash
http://adbshell.com/upload/adb.zip
```

Extract it, then run:

```bash
adb remount /system -o rw
adb devices
adb pull /system/etc/hosts /home
adb push /home/hosts /system/etc
```