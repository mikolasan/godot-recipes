---
description: >-
  Based on this tweet
  https://twitter.com/mikolasan/status/1465378386788896778?s=20
---

# Android export

## Settings for Android export

When Android Studio is installed

Android SDK path: **C:\Users\\\<username>\AppData\Local\Android\Sdk**

[`https://github.com/godotengine/godot/blob/96e70ac5f4f477eee3866ea788389a87d0dbd086/platform/android/export/export_plugin.cpp#L1962`](https://github.com/godotengine/godot/blob/96e70ac5f4f477eee3866ea788389a87d0dbd086/platform/android/export/export\_plugin.cpp#L1962)

`adb`: **C:\Users\\\<username>\AppData\Local\Android\Sdk\platform-tools\adb.exe**

`apksigner:` **C:\Users\\\<username>\AppData\Local\Android\Sdk\build-tools\\\<build tools version>\apksigner.bat**

`jarsigner`: **C:\Program Files\AdoptOpenJDK\jdk-11.0.8.10-hotspot\bin\jarsigner.exe** (Install JDK first \[answer]\([https://stackoverflow.com/a/12135749/1104612](https://stackoverflow.com/a/12135749/1104612)))

Debug keystore: **C:\Users\\\<username>\\.android\debug.keystore**

Debug keystore user: androiddebugkey

Debug keystore password: android



## Common errors

### Could not install to device

![](<.gitbook/assets/2021-11-29 23\_59\_58-Godot Engine - Sudoku16x16 - Main.tscn.png>)

Test with adb.&#x20;

```
adb install Sudoku16x16.apk
```
