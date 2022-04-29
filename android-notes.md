# PineNote stock Android notes

## Get root

Refer to Dorian's excellent guide: https://github.com/DorianRudolph/pinenotes#android-root

## Adding shortcut of Android `Settings` to default launcher

**Root required**

1. Install Termux from [F-Droid](https://f-droid.org/) or directly from the project's [Github](https://github.com/termux/termux-app/releases).
2. In Termux, install `sqlite3`:
   ```bash
   pkg install sqlite
   ```
3. In Termux or in `adb shell`, run one of the following command:
   (The command is fairly long, it may be better to use `adb shell` and paste the whole command.)

   To add the shortcut as the last shortcut:
   ```bash
   /data/data/com.termux/files/usr/bin/sqlite3 \
     /data/data/com.xrz.ebook.launcher/databases/handwrite_db \
     "INSERT INTO AppList VALUES('com.android.settingsreadApp','com.android.settings','Settings',unixepoch(),'readApp');"
   ```

   To add the shortcut as the first shortcut after the built-in shortcuts:
   ```bash
   /data/data/com.termux/files/usr/bin/sqlite3 \
     /data/data/com.xrz.ebook.launcher/databases/handwrite_db \
     "INSERT INTO AppList VALUES('com.android.settingsreadApp','com.android.settings','Settings',0,'readApp');"
   ```
4. Go back to home by clicking the home icon at the top-left corner of the screen.

   The shortcut is likely still not there yet, as the shortcut list is only refreshed when the device boots and when you make change to the list.
5. To trigger a refresh, click `Add Application`, and pick a random app. The `Settings` shortcut should appear along with the newly added shortcut.
6. Long-press the extra shortcut, and then click `Delete` to remove it.