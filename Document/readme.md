# AdDeals For Unity

this is a AdDeals Unity plugin. is base on [AdDeals](https://www.addealsnetwork.com/) iOS/Android/UWP Native SDK.

Tools Needed:

* Unity 5.5.4.p5 or later
* Vistual Studio 2017 or later
* Xcode 10
* Android Studio 3.2.1

__Note__: if you are use Unity 5.x, please upgrade use Unity 5.x patch version.

## Integrate

* drag `Assets\AdDeals\AdDeals.prefab` to your game scene
* Invoke AdDeals SDK API. take a look at sample code file `Assets\AdDeals\Sample\Test.cs`

```C#
AdDeals.AdDealsWrapper.Init("AppID", "AppSecert");

int adType = 1; // 1:interstitial 2: reward
AdDeals.AdDealsWrapper.ShowPopupAd(adType);
```


### iOS

* support iOS 8+


### Android

* support android sdk 15+

this plugin is not support build APK directly in Unity.

please export Gradle Project, and build&run with Android Studio.

![](./unity_android_export.png)

#### For Unity 5.x

if you use Unity 5.x, please check `YOUR_EXPORTS_PROTECT_ROOT/build.gradle`, make it look like follow:

```gradle
    ...
    android {
        ...
        defaultConfig {
            minSdkVersion 15
            targetSdkVersion 28
            versionCode 1
            versionName '0.1'
            ...
        }
        ...
    }
    ...
```


### Windows UWP

* the plugin is base on [AdDealsUniversalSDKW81](https://www.nuget.org/packages/AdDealsUniversalSDKW81).

* we support Windows UWP with C# Project with .Net ScriptBackend. please make sure your export UWP proejct setting like follow.

    ![Unity UWP project config](./unity_project_config.png)

* enable InternetClient on UWP, you can find it with follow path `PlayerSetting`->`Universal Windows Platform`->`Publishing Setting`->`Capabilities`

    ![Unity UWP capabilities setting](./uwp_capabilities.png)

* UWP application target aginest the lastest UWP SDK must use `Vistual Studio 2017`, so if you use Unity 5.x, please make sure use [Unity patch version](https://unity3d.com/unity/qa/patch-releases).


## API

### Methods

> Init AdDeals
```c#
void AdDeals.AdDealsWrapper.Init(String appID, String appKey);
```

> set privacy policy consent
```c#
void AdDeals.AdDealsWrapper.SetConsent(int consent);
```

> check if ad available

> params uiOrientation is invalid on UWP, send AdDealsWrapper.UIOrientationUnknown
```c#
void AdDeals.AdDealsWrapper.IsAvailable(int adType, int uiOrientation);
```

> cache ad

> params placement is invalid on UWP, send ""

> params uiOrientation is invalid on UWP, send AdDealsWrapper.UIOrientationUnknown

```c#
void AdDeals.AdDealsWrapper.CacheAdByType(int adType, string placement, int uiOrientation);
```

> show ad

> params placement is invalid on UWP, send ""

> params uiOrientation is invalid on UWP, send AdDealsWrapper.UIOrientationUnknown

```c#
void AdDeals.AdDealsWrapper.ShowPopupAd(int adType, string placement, int uiOrientation);
```

### Constants

> UI Orientation
```C#
AdDealsWrapper.UIOrientationUnknown = 0;
AdDealsWrapper.UIOrientationPortrait = 1;
AdDealsWrapper.UIOrientationPortraitUpsideDown = 2;
AdDealsWrapper.UIOrientationLandscapeRight = 3;
AdDealsWrapper.UIOrientationLandscapeLeft = 4;
```

> Ad type
```C#
AdDealsWrapper.AdTypeInterstitial = 1;
AdDealsWrapper.AdTypeRewardVideo = 2;
```


## Versions

* Version 0.0.5

Release Date: 2018.12.11

add WrapperBase class


* Version 0.0.4

Release Date: 2018.12.10

fix xcode project issue on unity 5.5


* Version 0.0.3

Release Date: 2018.12.10

support iOS & Android


* Version 0.0.2

Release Date: 2018.11.30

support Unity 5.5.4+ patch release version


* Version 0.0.1

Release Date: 2018.11.23

first version, support Unity 2017+ with UWP

## Test

Haved Test With Follow Unity Version:

* Unity 2018.2.16f
* Unity 2018.1.0f2
* Unity 2017.1.2f1
* Unity 2017.1.0p5
* Unity 5.5.4p5

## Issues

if you got follow error when import this unitypackage, it's ok, you can ignore it.

![](./unity_addeals_framework_import_error.png)

