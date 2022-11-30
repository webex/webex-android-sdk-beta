# Android | Mobile SDK - without Calling Feature 
AAR dependency can be downloaded from "Release tags" in right pane OR from [here](https://github.com/webex/webex-android-sdk-beta/releases/tag/calling-features-OFF)
## AAR Details

This documents covers the analysis of Mobile SDK (android) size, after DISABLING the calling features like : Broadworks calling, CUCM calling. A considerable amount of memory gain is there when calling features are disabled. 

Currently disabled calling features includes removal of 
- Broadworks (BWC) Calling 
- Jabber Calling  
-- CUCM calling 
-- Voicemail Service 
-- Office Service 

||**3.7.0-Release** |**Mobile SDK without calling feature** |
| :- | - | - |
|Memory snapshot |<img width="705" alt="Screenshot 2022-11-28 at 8 41 45 PM" src="https://user-images.githubusercontent.com/119413473/204521375-ca9b565c-22c0-4868-b023-306666a9b642.png">|<img width="708" alt="Screenshot 2022-11-28 at 8 36 34 PM" src="https://user-images.githubusercontent.com/119413473/204521557-79f32ebe-c886-40e7-a654-03f517527767.png">
|<p>Size on disk </p><p>(Universal) </p>|**214 MB** |**156 MB** |
|<p>Raw </p><p>Size          </p><p>(Universal) </p>|**212.8 MB** |**155.3 MB** |


|**Detailed AAR comparison** |
| - |
|<img width="1249" alt="Screenshot 2022-11-28 at 4 47 34 PM" src="https://user-images.githubusercontent.com/119413473/204522234-1f6db6dd-98b4-417c-bf6b-529fa81b773e.png">|

## When included in APP(APK details) 

The SDK without any calling feature is tested with a sample application (only meant for core feature like meetings and conversations). We found no impact on core features of Mobile SDK. 
### How to add in APP
1. Put AAR file in libs folder of your Android project
2. Open the project level Gradle file and add the following lines under the repositories tag, which is nested under allprojects.

      ```
      allprojects {
        repositories {
            flatDir { dirs 'aars'} //add this line
        }
      }
      ```
3. Add the following dependency in module level Gradle file and press sync-now
   ```
   implementation files('libs/no-calling-sdk-dev.aar')
   ```
### Memmory analysis for apk
Below details can be used for reference (in the terms of memory), to see the impact of our new Mobile SDK (without calling feature) on APP. 
||**Approx. Sizes (in MB)** |
| :- | - |
|APP bundle size (aab) |<img width="967" alt="Screenshot 2022-11-28 at 8 50 14 PM" src="https://user-images.githubusercontent.com/119413473/204522882-8586a662-b05c-41b6-b768-ad3ee623cbcd.png"><p>**158 MB** </p>|
|Universal apk size |<img width="962" alt="Screenshot 2022-11-28 at 8 52 09 PM" src="https://user-images.githubusercontent.com/119413473/204523253-0feb87f2-cf6d-4491-ab20-a2fa1e06c330.png"><p>**160 MB** </p>|
|arm64 apk size |<img width="965" alt="Screenshot 2022-11-28 at 8 57 01 PM" src="https://user-images.githubusercontent.com/119413473/204523366-d2e8d9e3-24c7-418c-95ad-5fa2b122fd96.png"><p>**43.5 MB** </p>|
|arm64 installation size |<img width="107" alt="image" src="https://user-images.githubusercontent.com/119413473/204523480-e0f179e7-0b52-4e6c-90c8-cea85953f1e1.png"><p>**160 MB** </p>|

