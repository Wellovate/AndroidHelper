# Android Helper

The Android Helper project is designed to make it easy for Untiy developers to invoke native Android interfaces to control devices, modify Settings, and so on. 

This project incorporates all our other repositories into one single package, and categorizes all interfaces into 5 classes:  ``DeviceHelper``, ``StorageHelper``, ``WifiHelper``, ``BlueToothHelper``, ``PowerManagerHelper``

## Usage

1. Put ``androidhelper_vx.x.aar`` into the Unity project's Assets/Plugins/Android directory;

2. Refer to the sample code below to call the interface.

   ```
   //Initialize an AndroidJavaObject with the class name of the interface
   AndroidJavaObject  deviceHelper= new AndroidJavaObject("com.picovr.androidhelper.DeviceHelper");
   //Get current activity
   AndroidJavaObject  activityContext = new AndroidJavaClass("com.picovr.androidhelper.MainActivity")
   .GetStatic<AndroidJavaObject>("currentActivity");
   //Must call "init" method before call other interface.
   deviceHelper.Call("init", activityContext );
   //Call the interface.
   deviceHelper.Call<string>("getPUIVersion");
   ```



## Sytem Signature

The interface marked with red dots requires the APK has the system signature.

Refer to the following two steps:

1. Add sharedUserId in ``AndroidManifest.xml`` in Assets/Plugins/Android

   ```
   android:sharedUserId="android.uid.system"
   ```

2. Refer to [online instruction](http://static.appstore.picovr.com/docs/KioskMode/chapter_three.html) to sign your apk with system signature.



## Interfaces

Click to view interface details.

**Note: The interface marked with red dots requires the system signature**

- **DeviceHelper**

Class name: com.picovr.androidhelper.DeviceHelper

getDeviceType  

getSN

[silentInstall🔴]()

silentUninstall🔴

killApp🔴

launch🔴

goToApp

startVRShell

getAppsString

registerHomeReceiver

unregisterHomeReceiver

openRecenterApp

installApp

- **StorageHelper**

Class name: com.picovr.androidhelper.StorageHelper

getStorageFreeSize

getStorageTotalSize

updateFile

getSDCardPath

- **BlueToothHelper**

Class name: com.picovr.androidhelper.BlueToothHelper

registerBlueToothReceiver

unregisterBlueToothReceiver

getContentDevice

getBlueToothMac

- **WifiHelper**

Class name: com.picovr.androidhelper.WifiHelper

registerWifiReceiver

unregisterWifiReceiver

getConnectedWifiSSID

getWifiMac

getWifiIpAddress

connectWifi🔴

connectWifiWithStaticIP

- **PowerManagerHelper**

Class name: com.picovr.androidhelper.PowerManagerHelper

androidLockScreen

androidUnLockScreen

acquireWakeLock

acquireWakeLock(timeout)

releaseWakeLock

setPropSleep

setPropScreenOff

androidShutDown🔴

androidReBoot🔴
