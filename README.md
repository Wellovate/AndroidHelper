# Android Helper

The Android Helper project is designed to make it easy for Untiy developers to invoke native Android interfaces to control devices, modify Settings, and so on. 

This project incorporates all our other repositories into one single package, and categorizes all interfaces into 5 classes:  ``DeviceHelper``, ``StorageHelper``, ``WifiHelper``, ``BlueToothHelper``, ``PowerManagerHelper``.

## Usage

1. Put ``androidhelper_vx.x.x.aar`` into the Unity project's Assets/Plugins/Android directory;

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

### DeviceHelper  
- [getPUIVersion][1]: get PUI version of device.
- [getDeviceType](https://github.com/picoxr/AndroidHelper/wiki): Get type of device.   
- [getSN](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getsn): Get serial number of device.        
- [silentInstall🔴](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-silentinstallstring-apkpath-string-packagename): Install the application without user interaction.   
- [silentUninstall🔴](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-silentuninstallstring-packagename):  Uninstall the application without user interaction.       
- [killApp🔴](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-killappstring-packagename): Kill the application.     
- [launch🔴](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-launchstring-filepath): Call WebVR browser to open the file.       
- [goToApp](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-gotoappstring-packagename): Start an application.       
- [startVRShell](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-startvrshellint-way-string-args): Launch Android 2D application.        
- [getAppsString](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getappsstring): Get a name list of installed applications.         
- [registerHomeReceiver](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-registerhomereceiver): Register the receiver for Home event broadcast.        
- [unregisterHomeReceiver](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-unregisterhomereceiver): Log out the receiver for Home event broadcast.     
- [openRecenterApp](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-openrecenterapp): Adjust startup calibration application.       
- [installApp](https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-openrecenterapp): Install the application.    
### StorageHelper
- [getStorageFreeSize](https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#float-getstoragefreesize): The remaining storage space inside the device.      
- [getStorageTotalSize](https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#float-getstoragetotalsize): Total storage space inside the device.         
- [updateFile](https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#void-updatefilestring-filepath): Update storaged file.   
- [getSDCardPath](https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#string-getsdcardpath): Get SD card path.   
### BlueToothHelper
- [registerBlueToothReceiver](https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#void-registerbluetoothreceiver): Register the receiver for bluetooth status broadcast.       
- [unregisterBlueToothReceiver](https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#void-unregisterbluetoothreceiver): Log out the receiver for bluetooth status broadcast.   
- [getContentDevice](https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#string-getcontentdevice): View the name of connected bluetooth.     
- [getBlueToothMac](https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#string-getbluetoothmac): Get MAC address of connected bluetooth.      
### WifiHelper
- [registerWifiReceiver](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-registerwifireceiver)   
- [unregisterWifiReceiver](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-unregisterwifireceiver)   
- [getConnectedWifiSSID](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getconnectedwifissid)   
- [getWifiMac](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getwifimac)   
- [getWifiIpAddress](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getwifiipaddress)   
- [connectWifi🔴](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-connectwifistring-ssidstring-password)   
- [connectWifiWithStaticIP](https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-connectwifiwithstaticipstring-ssidstring-passwordstring-ipstring-gatewaystring-dns)  
### PowerManagerHelper
- [androidLockScreen](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidlockscreen)   
- [androidUnLockScreen](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidunlockscreen)   
- [acquireWakeLock](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-acquirewakelock)   
- [acquireWakeLock(timeout)](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-acquirewakelocklong-timeout)   
- [releaseWakeLock](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-releasewakelock)   
- [setPropSleep](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-setpropsleepstring-time)   
- [setPropScreenOff](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-setpropscreenoffstring-time)   
- [androidShutDown🔴](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidshutdown)   
- [androidReBoot🔴](https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidreboot)  

[1]: https://github.com/picoxr/AndroidHelper/wiki
