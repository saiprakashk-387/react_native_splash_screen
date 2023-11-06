Splashscreen in react-native android.
Follow the given steps
Importent:

your_splash means for image name.
There you will find minmap folders
1.) Initialise a bare react native app (if not already done).

2.) Install react-native-splash-screen and link the library.

npm i react-native-splash-screen
3.) Add your_splash.png to all minmap folders.

Go to android/app/src/main/res
There you will find minmap folders like (mipmap-hdpi, mipmap-mdpi, etc.)
4.) Inside the res directory, create a folder named drawable. Inside that, ceate a file named background_splash.xml

Add the below code to the file

<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
 <item
 android:drawable="@mipmap/your_splash"
 android:gravity="fill" />
</layer-list>
5.) Inside the res directory, create a folder named layout. Inside that, ceate a file named launch_screen.xml

Add the below code to the file

<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:orientation="vertical"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:background="@mipmap/bg_screen"
/>
6.) Go to res/values/styles.xml replace the code

background_splash means for background_splash.xml file.
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <item name="android:windowDisablePreview">true</item>
        <item name="android:windowBackground">@drawable/background_splash</item>
    </style>

</resources>

7.) Go to MainActivity.java

package com.splashexample; // change package name

import com.facebook.react.ReactActivity;
import org.devio.rn.splashscreen.SplashScreen; // add this
import android.os.Bundle; // add this

public class MainActivity extends ReactActivity {

/\*\*

- Returns the name of the main component registered from JavaScript. This is used to schedule
- rendering of the component.
  \*/
  @Override // add this
  protected void onCreate(Bundle savedInstanceState) { // add this
  SplashScreen.show(this); // add this
  super.onCreate(savedInstanceState); // add this
  } // add this
  @Override
  protected String getMainComponentName() {
  return "splashexample";
  }
  }

8.) Go to App.js in the src folder.

at the top import SplashScreen from 'react-native-splash-screen';
inside App function add useEffect (Make sure to import it)
useEffect(() => {
SplashScreen.hide();
}, [])
Best part begins-

Hit the terminal and write react-native run-android
