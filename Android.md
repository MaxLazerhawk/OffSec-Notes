# Android hacking
<details open>
<summary>ADB</summary>

```adb devices``` - Check for devices connected to the host.

```adb shell``` - Enter phone terminal.

```adb shell pm path [package_name]``` - Check path for given app package.

```adb shell find / -name *maps*``` - Find stuff with adb.

```adb shell find / -name 'file.txt' 2>/dev/null``` - Find stuff with adb, ignore permissions denied.

Package names can be viewed via Google Play store. For example: https://play.google.com/store/apps/details?id=com.swapcard.apps.android.blackhat&hl=en_IN

Package name in this case is "com.swapcard.apps.android.backhat"

```adb shell pull /sdcard/Download/[filename]``` - Download files from Android device.

Phonesploit can also be used.

</details>
