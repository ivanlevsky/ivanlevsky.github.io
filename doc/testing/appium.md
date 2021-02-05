###INSTALL Andriod SDK
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

#####windows:
add system variables

System Variable | Value
---|---
ANDROID_HOME|Disk:\your-android-sdk-folder\cmdline-tools\latest
ANDROID_SDK_HOME|this will create a folder named ".android" in ANDROID_SDK_HOME folder
Path|%ANDROID_HOME%\bin your-android-sdk-folder\build-tools\27.0.3(aapt) your-android-sdk-folder\platform-tools"(adb)

