# Screenshot

[![API](https://img.shields.io/badge/API-16%2B-orange.svg?style=flat)](https://android-arsenal.com/api?level=16)
[![License Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=true)](http://www.apache.org/licenses/LICENSE-2.0)

A new and nice working android library to take screenshots which provides many functions.    
If enabled you will see a screenshot preview like you know it from the official android screenshot option.    
While the screenshot is being taken, you will also hear the shutter click sound for android 4.1+ devices.    

This library uses Android X depencies and is written in Java/Kotlin.


## Usage
Add a dependency to your build.gradle file:
```java
allprojects {
    repositories {
	    ...
	    maven { url 'https://jitpack.io' }
    }
}

dependencies {
    implementation 'com.github.Mika-89:Screenshot:master-SNAPSHOT'
}
```

```java
import com.nmd.screenshot.Screenshot;
```

| Public constructors |
| --- |
| `Screenshot(Context context)` |


## Needed app permissions
```java
android.permission.READ_EXTERNAL_STORAGE;
android.permission.WRITE_EXTERNAL_STORAGE;
```
AndroidMainfest.xml
```java
<manifest xlmns:android...>
  ...
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <application ...
</manifest>
```

Don't forget to set MIN and TARGET SDK values:
```java
<uses-sdk android:minSdkVersion="16" android:targetSdkVersion="xx"/>
```

## Interface

| type | name |
| --- | --- |
| `interface` | OnResultListener<br>*Interface definition for a callback to be invoked when a screenshot was created.* |

Public methods

| type | function |
| --- | --- |
| `abstract void` | result(boolean success, String filePath, Bitmap bitmap)<br>*Called when a screenshot was created.* |

```java
.setCallback(new Screenshot.OnResultListener() {
    @Override
    public void result(boolean success, String filePath, Bitmap bitmap) {
      // your code here.        
    }
});
```

## Public methods

| type | function | description | default value | min api |
| --- | --- | --- | --- | --- |
| `void` | takeScreenshot() | *Take a screenshot of the current visible screen.* | - |  14 |
| `void` | takeScreenshotFromView() | *Take a screenshot of any visible view.* | - |  14 |
| `void` | setFileName(String name) | *The filename for the taken screenshot.* | \"Screenshot.png\" |  14 |
| `string` | getFileName() | *Returns the given screenshot filename.* | - |  14 |
| `void` | showPreview(boolean enabled) | *If enabled you will see a short preview animation after the screenshot is taken.* | true |  14 |
| `boolean` | showPreview() | *Returns true/false if* `ShowPreview(...)` *is enabled/disabled.* | - |  14 |
| `void` | showNotification(boolean enabled) | *If enabled you will see a notification in the statusbar after the screenshot is taken.* | true |  14 |
| `boolean` | showNotification() | *Returns true/false if* `ShowNotification(...)` *is enabled/disabled.* | - |  14 |
| `void` | notificationTitle(String name) | *The title text for the notification.* | \"Screenshot..\" |  14 |
| `string` | notificationTitle() | *Returns the given notification title text.* | - |  14 |
| `void` | notificationShareTitle(String name) | *The share button text for the notification if* `Show Notification(...)` *is enabled.* | "Share" |   16 |
| `string` | notificationShareTitle() | *Returns the given notification share title text.* | - |  16 |
| `void` | notificationBigStyle(boolean enabled) | *If enabled you will see a notification with \"big style\" in the statusbar after the screenshot is taken.* | true |  16 |
| `boolean` | notificationBigStyle() | *Returns true/false if* `NotificationBigStyle(...)` *is enabled/disabled.* | - |  16 |
| `void` | notificationShareButton(boolean enabled) | *If enabled you will see a notification with a share button after the screenshot is taken.* | true |  16 |
| `boolean` | notificationShareButton() | *Returns true/false if* `NotificationShareButton(...)` *is enabled/disabled.* | - |  16 |
| `void` | allowScreenshots(boolean enabled) | *This feature allows users of your app to make or ban screenshots of their app.<br>If disabled and a person tries to make a screenshot, they will receive then a default system message that this is not possible.* | - |  1 |
| `void` | setDimAmount(float amount) | *Set the amount of dim behind the preview window if* `ShowPreview(...)` *is enabled. Use '0.0' for no dim and '1.0' for full dim.* | 0.5f |  14 |
| `float` | getDimAmount() | *Returns the amount from `setDimAmount(...)` .* | - |  14 |
| `boolean` | arePermissionsGranted() | *Returns true if the write and read permission is granted, else false.* | - |  1 |
| `boolean` | isReadPermissionGranted() | *Returns true if the read permission is granted, else false.* | - |  1 |
| `boolean` | isWritePermissionGranted() | *Returns true if the write permission is granted, else false.* | - |  1 |

*You do not need to add SDK version checks by yourself. This does the library for you.*

## Exampe code

```java
package com.YOURNAME.YOURNAME;

import android.app.Activity;
import android.content.Context;
import android.widget.TextView;
import android.graphics.Color;
import com.nmd.screenshot.Screenshot;
...

public class YourClass extends Activity {
  private Context context;
  private TextView txt;
  private Screenshot screenshot;

    public YourClass (...) {
      this.context = getContext();
      initialize();
    }
    
    private void initialize() {
      txt = (TextView)findViewById(R.id.editText);
      screenshot = new Screenshot(this.context);
    }

    public void take() {
      screenshot.notificationTitle("My screenshot title");
      screenshot.setCallback(new Screenshot.OnResultListener() {
        @Override
        public void result(boolean success, String filePath, Bitmap bitmap) {
          txt.setText(filePath);
          txt.setTextColor(success ? Color.GREEN : Color.RED);
          // if success is true then set text color to green, else red
        }
      });
      //After you have done your settings let's take the screenshot
      screenshot.takeScreenshot();
    }
}
```

## Download
[Screenshot.jar](Screenshot.jar)    
[Screenshot.aar](Screenshot.aar)

## Screenshots
![animation](https://github.com/NmdOfficial/Screenshot/blob/master/Images/Animation.gif)

## License
```
Copyright 2020 Author @NMD [Next Mobile Development]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
## Last words
If you like this library feel free to "star" it:<br>
![star](https://github.com/NmdOfficial/Screenshot/blob/master/Images/star.png)

This library has been successfully tested with the latest version of Android Studio (4.0).
