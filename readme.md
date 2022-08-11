# NFC HCE NDEF Reader

This app reads an NDEF message from an emulated NFC class 4 type tag.

For sending the emulated tag you need a second application: NfcHceNdefSender.

The tag is accessible with the IsoDep protocol so it needs a fixed application id (AID) - 
this is set in the "onTagDiscovered" method of MainActivity.java file with the value 
"F0394148148100".

The value need to be the same on sender AND reader side to get a connection - change these values 
on your own risk :-)

This app is based on the work of Justin Ribeiro who provided the basics for the MyApduService part,   
here is the original source: https://github.com/justinribeiro/android-hostcardemulation-sample

Both apps (sender and reader) were tested on real Samsung devices with Android 9 and 12.

AndroidManifest.xml
```plaintext
    <uses-permission android:name="android.permission.NFC" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    ...
    <queries>
        <intent>
            <action android:name="android.intent.action.SENDTO" />
            <data android:scheme="*" />
        </intent>
    </queries>
``
