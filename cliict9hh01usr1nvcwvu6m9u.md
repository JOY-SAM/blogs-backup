---
title: "M1 JDK issue in Building Expo project"
seoTitle: "M1 JDK issue in Building Expo project"
datePublished: Mon Jun 05 2023 04:30:39 GMT+0000 (Coordinated Universal Time)
cuid: cliict9hh01usr1nvcwvu6m9u
slug: mac-m1-npx-expo-run-android-device-throws-errors
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685911277156/ebfad5a8-0efe-4a8c-b509-d5c1f7739818.jpeg
tags: react-native, gradle, android, expo, jdk

---

This problem arises from an incompatibility between the JDK and Gradle, specifically in the context of the M1 architecture. Despite the absence of a comprehensive solution available in the online, I have taken the initiative to provide a resolution based on my findings and insights. This solution method uses JDK of Android studio to build instead of M1 Mac's Termurin JDK.

## **The ZSH command**

```bash
npx expo prebuild && npx expo run:android --device
```

### **The error:**

```plaintext
✔ Select a device/emulator › Pixel_3a_API_TiramisuPrivacySandbox (emulator)
› Using --device Pixel_3a_API_TiramisuPrivacySandbox
› Building app...
Configuration on demand is an incubating feature.

FAILURE: Build failed with an exception.

* What went wrong:
Could not open settings generic class cache for settings file '/Users/joy/Dev/Projects/Kallardo/mobile/android/settings.gradle' (/Users/joy/.gradle/caches/7.5.1/scripts/9kz1kv2g6929u11lqmx2zd9z3).
> BUG! exception in phase 'semantic analysis' in source unit '_BuildScript_' Unsupported class file major version 64
```

---

## **Let's jump into a Quick solution:**

**Open Android studio-&gt; File-&gt; Project Structure-&gt; SDKs**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685910038919/f8dfd126-ce57-44b9-9d53-34020c2c73aa.png align="center")

**Copy** the **JDK home path**, i.e the path Android studio default JDK

Open terminal

```bash
nano ~/.zprofile
```

**or**

```bash
subl ~/.zprofile
```

Add the following code in the `~/.zprofile`

```bash
export JAVA_HOME="The value we copied"
```

Close all terminals using the **dock!**

Open the terminal again and run your code again (in my case expo prebuild && npx expo run:android --device) it might work :)

---

If the problem still exists follow the Clearing Cache steps and run again

1. Clearing the [**Cache of expo**](https://docs.expo.dev/troubleshooting/clear-cache-macos-linux/#expo-cli-and-npm)
    
2. Deleting cache of global Gradle
    
    ```bash
     rm -rf $HOME/.gradle/caches/
    ```
    
3. Deleting Cache of project Gradle
    
    ```bash
    cd project_dir/android && ./gradlew clean
    ```
    
4. Check the JVM and other configs using
    
    ```bash
    ./gradlew --version
    ```