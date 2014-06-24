Getting Started with Processing + Android
=========================================

**This Tutorial is about getting started with Android Mode for Processing on a Mac.**  
Feel free to fork and add instructions for Linux + Windows.

## Install Processing

You need to Install **Processing 2.0.3** (Revision 0217) which you can download [here](https://code.google.com/p/processing/downloads/detail?name=processing-2.0.3-macosx.zip).  
For a complete list of old Processing Versions see [the old Processing repo](https://code.google.com/p/processing/downloads/list).

At the time of writing newer versions of Processing do not work with Android-Mode because they come with their own Java Runtime Engine included and some of the Android build-scripts still seem to reference the system Java...

### How to keep several versions of Processing

To keep several versions of Processing side-by-side, you can create a sub-folder in your Applications folder, i.e. `/Applications/processing/`
You can then extract different versions of Processing there, and rename them accordingly:

* `Processing-1.5.1.app`
* `Processing-2.0.3.app`
* `Processing-2.2.1.app`


## Installing the SDK

If all you ever want is to create quick and dirty prototypes, you may never need to work with and actual IDE. In this case all you need are the Android [SDK tools](https://developer.android.com/sdk/index.html).
For OSX the file can be found [here](http://dl.google.com/android/android-sdk_r22.6.2-macosx.zip)

## Installing an IDE

If things don't work as expected, or if you are planning to do more advanced stuff, you might want to install an Integrated Developer Environment (IDE).

### ADT Bundle (Eclipse)###

This is a version of eclipse that comes pre-packaged with all the plugins and tools you need to get started with Android development. Learn more about it [here](https://developer.android.com/sdk/installing/bundle.html).

### Eclipse + ADT Plugin ###

If you already have Eclipse installed, you can:

* Download the [SDK tools](https://developer.android.com/sdk/index.html)
* Add the  [ADT Plugin](https://developer.android.com/sdk/installing/installing-adt.html) to Eclipse

### Android Studio (IntelliJ) ###

The main development environment for Android used to be Eclipse, but Google is currently switching to IntelliJ. You can download the early access preview [here](https://developer.android.com/sdk/installing/studio.html).

## Edit your .profile

Once you have extracted the `SDK tools` make sure you can access them on the command line by adding the following two lines to your `.profile`.

	export ANDROID_HOME=$HOME/Developer/Android/android-sdk
	export PATH=$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH

## Tools

The two most important tools are the **package manager** and the **device manager**.


### Package Manager ###

Use the Package Manager to install SDKs for Android development.  
You can start it on the command line like this:
	
	android
	
* Install all the latest packages from the tools section
* For Processing you need Android 2.3.3 (API 10) packages


### Connecting Phyiscal Devices ###

If you connect a physical device to your computer via USB, make sure you to enable USB debugging, in the developer options of your device.
If your Phone has Android 4.2 or newer, read [this article](http://www.androidcentral.com/how-enable-developer-settings-android-42) on how to unlock them.

### Virtual Device Manager ###

Android Virtual Devices (AVD), are phones + tablets that are emulated on your computer. You can start the AVD manager like this:

	android avm

Processing should automatically create a virtual device for you, but in case it doesn't you can create one using the Device Manager, or via the commandline:

	android create avd -n Processing-0217 -t android-10 -c 64M -s WVGA800 --abi armeabi

For more info see [this thread](http://forum.processing.org/two/discussion/3093/emulator-in-android-mode-does-not-work/p1).


### Speeding up the Emulator ###

This step is optional.  
Only do this If you feel the virtual device needs too long to boot.

* Open the android package manager and install the Intel86 Emulator Accelerator (HAXM) from the Extras section
* Inside your android sdk directory you should find the installer: `extras/intel/Hardware_Accelerated_Execution_Manager/IntelHAXM_1.0.8.dmg`  

See [this page](https://software.intel.com/android/articles/speeding-up-the-android-emulator-on-intel-architecture) for more info.
  
Now you can use the android device manager to change the CPU from `ARM` to `x86`.  
You may also do so using the command line:

  	android create avd -n Processing-0217 -t android-10 -c 64M -s WVGA800 --abi x86 --force

In addition you can activate one of the following options when creating/editing a virtual device:

* Use Host GPU for faster graphics + smoother interaction
* Save and load snapshots of the machine state (Hibernate)


### The Android Debug Bridge ###

In order to run sketches on a device, Processing must be able to communicate with it.  
This is done using the `Android Debug Bridge`.

You can see which devices are available for communication by typing:

	adb devices

This should show both physical and virtual devices connected to your computer.


## Android-Mode 

### Installing ###

Now that we have understood the basics, let's install Android-Mode in Processing.

* Click on the little Box saying `Java` in the top right of your Processing-Window.
* Click `Add Mode` to open the Mode Manager
* Install `Android Mode`

### Running ###

* `Sketch > Run on Device` or `[⌘ R]` to run the sketch on a device connected via USB.
* `Sketch > Run in Emulator` or `[SHIFT ⌘ R]` to run the sketch on a virtual device.

## Links ##

* [Android-Mode](http://wiki.processing.org/w/Android) in the Processing Wiki.














