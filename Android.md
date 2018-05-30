# Android generics

Common operations for Android apps. For Android libraries specific operations, check out [Android-library.md](./Android-library.md)

## Add app permissions
  1. Open `AndroidManifest.xml`
  2. Add the `<uses-permissions>` tag to the **root element** (`<manifest>`) of the XML file.
  
**E.g.:**
```XML
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.domain.package">

    <uses-permission android:name="android.permission.INTERNET" />
    
    <!-- more stuff -->

</manifest>
```
