### INSTALL Andriod SDK 
***

check if installed successd
```commandline
sdkmanger --version 
```

install android 8 api   
```commandline
sdkmanager platforms
android-27
```


reveal the paths it checks
```commandline
sdkmanager --verbose --list
```

install sdk tools like adb,aapt...  
```commandline
sdkmanager build-tools 
27.0.3
```  

### SET APPIUM ENVIRONMENT
***
##### windows: 
add system variables

System Variable | Value
---|---
ANDROID_HOME|Disk:\your-android-sdk-folder\cmdline-tools\latest
ANDROID_SDK_HOME|this will create a folder named ".android" in ANDROID_SDK_HOME folder
Path|%ANDROID_HOME%\bin;your-android-sdk-folder\build-tools\27.0.3(aapt);your-android-sdk-folder\platform-tools"(adb)


### DEBUG ON ANDROID PHONE  
***
open development mode on phone  
open options  "usb debugging", "install via usb", "usb debugging(security settings)" in system settings  
run `adb devices` command to check phone device id  



### FAQ  
***
Q: "tap by coordinates" ,appium inspector show "coordinates (x,y) out bounds" when tap on screen ?  
A: click "zoom in"  

Q: appium can't connect to phone when not use wifi ?  
A: search "appium" in phone settings "applications",there are three appium apps,make sure they
can use 4g net  

Q: how to find appPackage and appActivity ?  
A: open your app, and run commands:
```shell
adb shell  
dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp'
```   
Q: "dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp" not return message?
A: in phone like realme q2 search "mSurface" param
```shell
adb shell  
dumpsys window windows |grep -E 'mSurface=Surface'
```

Q: appium can't install appium settings app in phone(eg. realme q2)?
A: in develop options-> apps -> "Disable Permission Monitoring"

Q: error when starting sdkmanger.bat in windows10 ?  
A: download the command line tool.zip, unpack it,maken sure the folder structure like this:
```
D:\your-android-sdk-folder
|——————\cmdline-tools
|——————\latest
       |——————\bin
       |——————\lib
       |——————NOTICE.txt
       |——————source.properties
```


Q: how to search installed app's name(app's label) ?  
A: install aapt binary for android and  run commands:
```shell 
# https://android.izzysoft.de/downloads --for android 5.0 before  
# https://github.com/Calsign/APDE/tree/master/APDE/src/main/assets/aapt-binaries --for android 5.0 or after and x86 device
# push aapt binary to phone
adb push aapt-are-pie to /data/local/tmp
adb shell chmod 0755 /data/local/tmp/aapt-arm-pie

# get apkpath
adb shell pm list packages -3 -f
adb shell /data/local/tmp/aapt-arm-pie d badging + apkpath
```   

Q: appium webview chromedriver wrong?  
A: 1.manual select chromedriver:   
   check appium log to find app's webview version, then download the version's chromedriver from `https://chromedriver.chromium.org/downloads`
   then replace the appium desktop's driver from `D:\develop\appium\resources\app\node_modules\appium\node_modules\appium-chromedriver\chromedriver\win\`  
2.auto select chromedriver version:  
see `appium_utils` comment

reference links:  
[useful adb commands](https://gist.github.com/Pulimet/5013acf2cd5b28e55036c82c91bd56d8)  
[appium tutorial doc](https://appium.io/docs/en/about-appium/getting-started/)  
[android sdkmanager offcial site](https://developer.android.com/studio/command-line/sdkmanager)  
