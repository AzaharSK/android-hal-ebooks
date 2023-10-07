# ADB FASTBOOT commands cheatsheet

## ADB Basics 

```
adb help            			 (List all comands )
```

## Devices 

```
adb usb
adb devices   				( show devices attached )
adb devices -l    			( devices (product/model )
adb connect ip_address_of_device

```


## ADB Shell

```
adb shell  				(starts the backround terminal) 				
exit 					(exits the background terminal) 

adb shell ls (list directory contents)
adb shell ls -s (print size of each file)
adb shell ls -R (list subdirectories recursively)


/data/data/<package>/databases (app databases)
/data/data/<package>/shared_prefs/ (shared preferences)
/data/app (apk installed by user)
/system/app (pre-installed APK files)
/mmt/asec (encrypted apps) (App2SD)
/mmt/emmc (internal SD Card)
/mmt/adcard (external/Internal SD Card)
/mmt/adcard/external_sd (external SD Card)

```


## ADB root 

```
adb root             			(restarts adbd with root permissions)
adb reboot           			(reboots the device)
adb reboot recovery  
adb reboot-bootloader

adb reboot fastboot (reboot device into recovery mode)
fastboot devices	
fastboot oem unlock	 
fastboot oem lock       
fastboot reboot bootloader
fastboot flash boot boot.img
fastboot flash recovery recovery.img
fastboot boot filename.img
fastboot erase

```
## ADB remount 

```
adb root
adb remount

  or

adb root
adb disable-verity
adb reboot
adb root
adb remount

or 

$ adb shell
$ su
# mount -o rw,remount /

```

## Adb Server 

```
adb start-server       			(starts the adb server)
adb kill-server        			(kills the adb server)
```


## ADB multiple devices 

```
adb -s <deviceName> <command> (redirect command to specific device)
adb –d <command> (directs command to only attached USB device)
adb –e <command> (directs command to only attached emulator)
```

## LogCat 

```
adb logcat
adb logcat -c // clear // The parameter -c will clear the current logs on the device.
adb logcat -d > [path_to_file] // Save the logcat output to a file on the local system.
adb bugreport > [path_to_file] // Will dump the whole device information like dumpstate, dumpsys and logcat output.
```
## Get device android version 

```
adb shell getprop ro.build.version.release
```

## Files

```
adb push [source] [destination]    // Copy files from your computer to your phone.
adb pull [device file location] [local file location] // Copy files from your phone to your computer.
```

## Package Installation 

```
adb shell install <apk> (install app)
adb shell install <path> (install app from phone path)
adb shell install -r <path> (install app from phone path)
adb shell uninstall <name> (remove the app)
```

## Package Info 

```
adb shell list packages (list package names)
adb shell list packages -r (list package name + path to apks)
adb shell list packages -3 (list third party package names)
adb shell list packages -s (list only system packages)
adb shell list packages -u (list package names + uninstalled)
adb shell dumpsys package packages (list info on all apps)
adb shell dump <name> (list info on one package)
adb shell path <package> (path to the apk file)
```

## App install  

```
adb -e install path/to/app.apk

-d                        - directs command to the only connected USB device...
-e                        - directs command to the only running emulator...
-s <serial number>        ...
-p <product name or path> ...
The flag you decide to use has to come before the actual adb command:
```

## Uninstalling app from device 

```
adb uninstall com.myAppPackage
adb uninstall <app .apk name>
adb uninstall -k <app .apk name> -> "Uninstall .apk withour deleting data"

adb shell pm uninstall com.example.MyApp
adb shell pm clear [package] // Deletes all data associated with a package.

```



## Configure Settings Commands

```
adb shell dumpsys battery set level <n> (change the level from 0 to 100)
adb shell dumpsys battery set status<n> (change the level to unknown, charging, discharging, not charging or full)
adb shell dumpsys battery reset (reset the battery)
adb shell dumpsys battery set usb <n> (change the status of USB connection. ON or OFF)
adb shell wm size WxH (sets the resolution to WxH)
```

## Phone Info

```
adb get-statе (print device state)
adb get-serialno (get the serial number)
adb shell dumpsys iphonesybinfo (get the IMEI)
adb shell netstat (list TCP connectivity)
adb shell pwd (print current working directory)
adb shell dumpsys battery (battery status)
adb shell pm list features (list phone features)
adb shell service list (list all services)
adb shell dumpsys activity <package>/<activity> (activity info)
adb shell ps (print process status)
adb shell wm size (displays the current screen resolution)
dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp' (print current app's opened activity)
```


## Device Related Commands

```
adb reboot-recovery (reboot device into recovery mode)
adb reboot fastboot (reboot device into recovery mode)
adb shell screencap -p "/path/to/screenshot.png" (capture screenshot)
adb shell screenrecord "/path/to/record.mp4" (record device screen)
adb backup -apk -all -f backup.ab (backup settings and apps)
adb backup -apk -shared -all -f backup.ab (backup settings, apps and shared storage)
adb backup -apk -nosystem -all -f backup.ab (backup only non-system apps)
adb restore backup.ab (restore a previous backup)
adb shell am start|startservice|broadcast <INTENT>[<COMPONENT>]
-a <ACTION> e.g. android.intent.action.VIEW
-c <CATEGORY> e.g. android.intent.category.LAUNCHER (start activity intent)

adb shell am start -a android.intent.action.VIEW -d URL (open URL)
adb shell am start -t image/* -a android.intent.action.VIEW (opens gallery)
```

## Device state onformation

```
adb get-statе (print device state)
adb get-serialno (get the serial number)
adb shell dumpsys iphonesybinfo (get the IMEI)
adb shell netstat (list TCP connectivity)
adb shell pwd (print current working directory)
adb shell dumpsys battery (battery status)
adb shell pm list features (list phone features)
adb shell service list (list all services)
adb shell dumpsys activity <package>/<activity> (activity info)
adb shell ps (print process status)
adb shell wm size (displays the current screen resolution)
dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp' (print current app's opened activity)
```


## Package info

```
adb shell list packages (list package names)
adb shell list packages -r (list package name + path to apks)
adb shell list packages -3 (list third party package names)
adb shell list packages -s (list only system packages)
adb shell list packages -u (list package names + uninstalled)
adb shell dumpsys package packages (list info on all apps)
adb shell dump <name> (list info on one package)
adb shell path <package> (path to the apk file)
```

## Configure Settings Commands
```
adb shell dumpsys battery set level <n> (change the level from 0 to 100)
adb shell dumpsys battery set status<n> (change the level to unknown, charging, discharging, not charging or full)
adb shell dumpsys battery reset (reset the battery)
adb shell dumpsys battery set usb <n> (change the status of USB connection. ON or OFF)
adb shell wm size WxH (sets the resolution to WxH)
```
## Device Related Commands

```
adb reboot-recovery (reboot device into recovery mode)
adb reboot fastboot (reboot device into recovery mode)
adb shell screencap -p "/path/to/screenshot.png" (capture screenshot)
adb shell screenrecord "/path/to/record.mp4" (record device screen)
adb backup -apk -all -f backup.ab (backup settings and apps)
adb backup -apk -shared -all -f backup.ab (backup settings, apps and shared storage)
adb backup -apk -nosystem -all -f backup.ab (backup only non-system apps)
adb restore backup.ab (restore a previous backup)
adb shell am start|startservice|broadcast <INTENT>[<COMPONENT>]
-a <ACTION> e.g. android.intent.action.VIEW
-c <CATEGORY> e.g. android.intent.category.LAUNCHER (start activity intent)

adb shell am start -a android.intent.action.VIEW -d URL (open URL)
adb shell am start -t image/* -a android.intent.action.VIEW (opens gallery)
```

## Logs

```
adb logcat [options] [filter] [filter] (view device log)
adb bugreport (print bug reports)
```

## Other

```
adb backup // Create a full backup of your phone and save to the computer.
adb restore // Restore a backup to your phone.
adb sideload //  Push and flash custom ROMs and zips from your computer.

```
