---
src: /SDK Center/Android.md
---

# Android SDK Setup

This tutorial will walk you through integrating GameSparks with your android project on the Android Builder IDE.the GameSparks Android SDK requires API 8 or greater and the Test Harness requires API 11 or greater for the example test harness project that we supply as a sample.

The source repositories for the android libraries can be found here:

https://bitbucket.org/gamesparks/gamesparks-java-sdk

https://bitbucket.org/gamesparks/gamesparks-android-sdk

To integrate GameSparks into your project:

In your Project's build.gradle add classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.2' and classpath "com.github.dcendents:android-maven-gradle-plugin:1.3" under buildscript dependencies. Add maven {url "http://repo.gamesparks.net/mvn"} under allprojects repositories.Our example looks like this:

```
buildscript {
  repositories {
      jcenter()
  }
  dependencies {
      classpath 'com.android.tools.build:gradle:1.5.0'
      classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.2'
      classpath "com.github.dcendents:android-maven-gradle-plugin:1.3"
  }
}

allprojects {
  repositories {
      jcenter()
      maven {
          url "http://repo.gamesparks.net/mvn"
      }
  }
}
```

In your module's build.gradle under dependencies add 'compile 'com.gamesparks.sdk:gamesparks-android-client-sdk:+''. Our sample looks like:
apply plugin: 'com.android.application'

```
android {
    compileSdkVersion 23
    buildToolsVersion "23.0.2"

    defaultConfig {
        applicationId "com.example.test1"
        minSdkVersion 11
        targetSdkVersion 21
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.txt'
        }
    }
}

dependencies {
    compile 'com.android.support:support-v4:23.1.1'
    compile 'com.android.support:appcompat-v7:23.1.1'
    compile 'com.gamesparks.sdk:gamesparks-android-client-sdk:+'
}
```

Finally, in regards to set up add the following to your AndroidManifest.xml:

If you try to build you application at this point you will receive an error regarding an image clash. In the application block in the manifest add:

 tools:replace="android:icon"
After adding the line, hover your mouse over it and hit Alt+Enter on your keyboard to automatically add the necessary code to make this work.

That will ensure that the API is ready to be used. Now to initialise the GS module and connect our frontend to our backend!

In any of your activity's Java code's OnCreate function place the following:

```
GSAndroidPlatform.initialise(this, "YOUR KEY", "YOUR SECRET", false, true);
```

Now you need an API key and secret, which you given when you create a game on our platform, click here for a quick guide to show you how.

Once that's done, now you need to start the connection. To do that place this code in the activity's

```
@Override
	public void onStart()
	{
		super.onStart();
		GSAndroidPlatform.gs().stop();
		GSAndroidPlatform.gs().start();
	}
```

The reason we stop the module before we start it is to establish a new connection which works to refresh the connection.

After all this is done, you now are ready to use GameSparks API in your project. Details of the API can be found [here](https://api.gamesparks.net/?javasdk#)
