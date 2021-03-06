Full Screen ANE for Adobe AIR
=============================

One of the most common complaints you hear from Adobe AIR developers is that they can't get true full screen on Android devices that have an on-screen navigation bar (the one that contains the back, home and task buttons), with full screen usually meaning that the buttons are simply replaced with a series of grey dots. 

If you're one of those developers, then this AIR Native Extension (ANE) may be the solution you've been looking for. 

This ANE requires Adobe AIR 4+.

How does it work?
-----------------

This ANE enables developers to offer users a true full screen experience in the Adobe AIR apps for Android.

Using Android 4.0+, you can use true full screen in "lean mode", the way you see in apps like YouTube, expanding the app right to the edges of the screen, hiding the status and navigation bars until the user next interacts. This is ideally suited to video or cut-scene content.

In Android 4.4+, however, you can now enter true full screem, fully interactive immersive mode. In this mode, your app will remain in true full screen until you choose otherwise; users can swipe down from the top of the screen to temporarily display the system UI.


Code example
------------

Using the ANE in your app couldn't be easier:


```as3
import com.mesmotronic.ane.AndroidFullScreen;

AndroidFullScreen.isSupported; // Is this ANE supported?
AndroidFullScreen.isImmersiveModeSupported; // Is immersive mode supported?
AndroidFullScreen.hideSystemUI(); // Hide system UI until user interacts
AndroidFullScreen.showSystemUI(); // Show system UI
AndroidFullScreen.showUnderSystemUI(); // Extend your app underneath the system UI (Android 4.4+ only)
AndroidFullScreen.immersiveMode(); // Hide system UI and keep it hidden (Android 4.4+ only)
AndroidFullScreen.immersiveMode(false); // Hide system UI until user swipes from top (Android 4.4+ only)
```

All methods return Boolean values: *true* if the action was successful, *false* if it wasn't (or isn't supported); if you're using the ANE in an app for a platform other than Android, all properties and methods will return false.

Therefore, the simplest way to give users the best possible interactive full screen experience in your app is:

```as3
if (!AndroidFullScreen.immersiveMode())
{
    stage.displayState = StageDisplayState.FULL_SCREEN_INTERACTIVE;
}
```

And a great way to offer the best possible full screen video playback is:

```as3
if (!AndroidFullScreen.hideSystemUI())
{
    stage.displayState = StageDisplayState.FULL_SCREEN_INTERACTIVE;
}
```

Starling
--------

To use this ANE with Starling,  add *Starling.handleLostContext = true;* at the start of your ActionScript code to prevent Stage3D lost context errors breaking your app when switching between the normal app state and true full screen.

License
-------

This project has been released under BSD license; see LICENSE for details.
