# Android libraries
### Export a library in AAR format
reference: https://developer.android.com/studio/projects/android-library

Publish an Android AAR from a library, with all classes and resource files of the library itself:

        gradle assemble OR assembleRelease OR assembleDebug
        
In order to use the package:
1. Open an Android Studio project
2. Right-click on the project view > New... > New Module...
3. Choose "Import AAR/JAR"

***NOTE:*** **You need to get the dependencies for the library by yourself, since they are NOT included in the AAR file**

***********************************

### Deploy with Jitpack
reference: https://jitpack.io/docs/ANDROID/#publish-an-android-library

**Better solution: automatically download dependencies for your library** - you only need to write a line in build.gradle to get everything you need and start using the library.

Publish your code on Github / BitBucket / GitLab (jitpack is free for public repos). You will need to add some code to the gradle files in your project:

Your library's name: `mylib`
* edit `/build.gradle`:
```Gradle
buildscript { 
  dependencies {
        // other dependencies . . .
    classpath 'com.github.dcendents:android-maven-gradle-plugin:2.0'
  }
}
```
* edit `mylib/build.gradle`:
  * add `apply plugin: 'com.github.dcendents.android-maven'` on top
  * if your code is on GitHub, set `group='com.github.YourUsername'`
  * for BitBucket: `org.bitbucket.YourUsername`
  * for GitLab: `com.gitlab.YourUsername`

then push changes and test the build as explained in the [Troubleshooting](https://jitpack.io/docs/BUILDING/#troubleshooting) section of the Docs
(for short: visit https://jitpack.io/com/github/User/Repo/Tag/build.log)

When the tests pass, you may want to add a **tag** (or a GitHub *Release*) on the working commit, e.g. `1.0` . In order to use the library, just include it in your **Gradle dependencies**, like in the following example:
```Gradle
implementation "com.github.YourUsername:mylib:1.0"
```
(be sure to switch to the right domain if your repo is on BitBucket/GitLab)
