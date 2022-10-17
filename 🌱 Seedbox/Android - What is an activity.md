up::
tags:: #state/seedling #on/android

# What is an Activity?
An *Activity* is the basic building block of an Android app. It can be described as ==a single, focused thing that the user can do==.

In desktop apps, the entry point is always the same: you open the app and you are welcomed by the same initial screen. However, in mobile-apps, the user doesn't always begin in the same place. 

For example, opening the mail app from the home screen may open the inbox with a list of mails. However, opening the app from a photo to send the photo may open with a new email with the photo loaded.

## Parts of an Activity

## Lifecycle of an Activity
The lifecycle of an Activity is controlled by 7 methods of the Activity class. These methods are:
- **onCreate**: called when the activity is first created.
- **onStart**: called when the activity is becoming visible to the user.
- **onResume**: called when the activity will start interacting with the user.
- **onPause**: called when the activity is not in the foreground.
- **onStop**: called when the Activity is no longer visible.
- **onDestroy**: called before the activity is destroyed.

Moreover, there are three key loops within an activity:
- The **entire lifetime** of the activity happens between the first call to **onCreate** until the call to **onDestroy**. An Activity will do all the setup in **onCreate** and release all remaining resources in **onDestroy**.
- The **visible lifetime** of the activity happens between a call to **onStart** until a corresponding call to **onStop**. During this time the user can see the activity on.-screen, though it may not be in the foreground and interacting with the user.
- The **foreground lifetime** of the activity happens between a call to **onResume** until a corresponding call to **onPause**. During this time the activity is visible, active and interacting with the user.

---
Planted: 2022-10-17
Last tended: 2022-10-17