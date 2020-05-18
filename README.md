# Android Helper

This project incorporates all our other Android repositories into one single package, and categorizes all interfaces into 5 classes:  ``DeviceHelper``, ``StorageHelper``, ``BlueToothHelper``, ``WifiHelper``, ``PowerManagerHelper``.
   
## Usage
1. Clone this repo and make project in Android Studio, or download aar file in [release page](https://github.com/picoxr/AndroidHelper/releases).

2. Put ``AndroidHelper_Vx.x.x.aar`` into your Unity project's Assets/Plugins/Android directory;  

3. Refer to the sample code below to call the interface.

   ```c#
   //Initialize an AndroidJavaObject with the class name of the interface
   AndroidJavaObject  deviceHelper= new AndroidJavaObject("com.picovr.androidhelper.DeviceHelper");
   //Get current activity
   AndroidJavaObject  activityContext = new AndroidJavaClass("com.unity3d.player.UnityPlayer")
   .GetStatic<AndroidJavaObject>("currentActivity");
   //Must call "init" method before call other interface.
   deviceHelper.Call("init", activityContext );
   //Call the interface.
   string puiVersion = deviceHelper.Call<string>("getPUIVersion");
   ```

## Sytem Signature

The interface marked with red dot("🔴") requires the APK has the system signature.

Refer to the following steps:

1. Add sharedUserId in ``AndroidManifest.xml`` in Assets/Plugins/Android

   ```
   android:sharedUserId="android.uid.system"
   ```

2. Refer to [online instruction](http://static.appstore.picovr.com/docs/KioskMode/chapter_three.html) to sign your apk with system signature.


## Interfaces

**Note: The interface marked with "🔴" requires the APK has the system signature**

### DeviceHelper  
- [getPUIVersion][getPUIVersion]: get PUI version of device.
- [getDeviceType][getDeviceType]: Get type of device.   
- [getSN][getSN]: Get serial number of device.        
- [silentInstall🔴][silentInstall]: Install the application without user interaction.   
- [silentUninstall🔴][silentUninstall]:  Uninstall the application without user interaction.       
- [killApp🔴][killApp]: Kill the application.     
- [launch🔴][launch]: Call WebVR browser to open the file.       
- [goToApp][goToApp]: Start an application.       
- [startVRShell][startVRShell]: Launch Android 2D application.        
- [getAppsString][getAppsString]: Get a name list of installed applications.         
- [registerHomeReceiver][registerHomeReceiver]: Register the receiver for Home event broadcast.        
- [unregisterHomeReceiver][unregisterHomeReceiver]: Log out the receiver for Home event broadcast.     
- [openRecenterApp][openRecenterApp]: Adjust startup calibration application.       
- [installApp][installApp]: Install the application.    
### StorageHelper
- [getStorageFreeSize][getStorageFreeSize]: The remaining storage space inside the device.      
- [getStorageTotalSize][getStorageTotalSize]: Total storage space inside the device.         
- [updateFile][updateFile]: Update storaged file.   
- [getSDCardPath][getSDCardPath]: Get SD card path.   
### BlueToothHelper
- [registerBlueToothReceiver][registerBlueToothReceiver]: Register the receiver for bluetooth status broadcast.       
- [unregisterBlueToothReceiver][unregisterBlueToothReceiver]: Log out the receiver for bluetooth status broadcast.   
- [getContentDevice][getContentDevice]: View the name of connected bluetooth.     
- [getBlueToothMac🔴][getBlueToothMac]: Get MAC address of connected bluetooth.      
### WifiHelper
- [registerWifiReceiver][registerWifiReceiver]: Register the receiver for Wi-Fi status broadcast.   
- [unregisterWifiReceiver][unregisterWifiReceiver]:  Log out the receiver for Wi-Fi status broadcast.  
- [getConnectedWifiSSID][getConnectedWifiSSID]: View the name of Wi-Fi connection.      
- [getWifiMac][getWifiMac]: Get MAC address of connected Wi-Fi.   
- [getWifiIpAddress][getWifiIpAddress]: Get Wi-Fi IP address.     
- [connectWifi🔴][connectWifi]: Connect to Wi-Fi.    
- [connectWifiWithStaticIP][connectWifiWithStaticIP]: Set static IP.      
### PowerManagerHelper
- [androidLockScreen][androidLockScreen]: Lock the screen.    
- [androidUnLockScreen][androidUnLockScreen]: Unlock the screen.      
- [acquireWakeLock][acquireWakeLock]: Request a WakeLock.       
- [acquireWakeLock(timeout)][acquireWakeLock(timeout)]: Request a WakeLock, unlock automatically after timeout.          
- [releaseWakeLock][releaseWakeLock]: Deactivate WakeLock.       
- [setPropSleep][setPropSleep]: Sets System Sleep Timeout.           
- [setPropScreenOff][setPropScreenOff]: Sets Screen Off Timeout.      
- [androidShutDown🔴][androidShutDown]: Shutdown the system.      
- [androidReBoot🔴][androidReBoot]: Reboot the system.        

[getPUIVersion]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getpuiversion
[getDeviceType]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getdevicetype
[getSN]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getsn
[silentInstall]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-silentinstallstring-apkpath-string-packagename
[silentUninstall]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-silentuninstallstring-packagename
[killApp]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-killappstring-packagename  
[launch]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-launchstring-filepath  
[goToApp]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-gotoappstring-packagename  
[startVRShell]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-startvrshellint-way-string-args  
[getAppsString]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#string-getappsstring  
[registerHomeReceiver]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-registerhomereceiver   
[unregisterHomeReceiver]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-unregisterhomereceiver  
[openRecenterApp]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-openrecenterapp  
[installApp]: https://github.com/picoxr/AndroidHelper/wiki/DeviceHelper#void-openrecenterapp  
[getStorageFreeSize]: https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#float-getstoragefreesize  
[getStorageTotalSize]: https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#float-getstoragetotalsize  
[updateFile]: https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#void-updatefilestring-filepath    
[getSDCardPath]: https://github.com/picoxr/AndroidHelper/wiki/StorageHelper#string-getsdcardpath  
[registerBlueToothReceiver]: https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#void-registerbluetoothreceiver  
[unregisterBlueToothReceiver]: https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#void-unregisterbluetoothreceiver    
[getContentDevice]: https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#string-getcontentdevice  
[getBlueToothMac]: https://github.com/picoxr/AndroidHelper/wiki/BlueToothHelper#string-getbluetoothmac  
[registerWifiReceiver]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-registerwifireceiver  
[unregisterWifiReceiver]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-unregisterwifireceiver     
[getConnectedWifiSSID]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getconnectedwifissid   
[getWifiMac]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getwifimac   
[getWifiIpAddress]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#string-getwifiipaddress  
[connectWifi]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-connectwifistring-ssidstring-password    
[connectWifiWithStaticIP]: https://github.com/picoxr/AndroidHelper/wiki/WifiHelper#void-connectwifiwithstaticipstring-ssidstring-passwordstring-ipstring-gatewaystring-dns  
[androidLockScreen]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidlockscreen   
[androidUnLockScreen]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidunlockscreen   
[acquireWakeLock]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-acquirewakelock   
[acquireWakeLock(timeout)]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-acquirewakelocklong-timeout   
[releaseWakeLock]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-releasewakelock   
[setPropSleep]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-setpropsleepstring-time   
[setPropScreenOff]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-setpropscreenoffstring-time   
[androidShutDown]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidshutdown   
[androidReBoot]: https://github.com/picoxr/AndroidHelper/wiki/PowerManagerHelper#void-androidreboot  


