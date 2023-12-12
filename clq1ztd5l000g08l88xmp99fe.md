---
title: "Integrating Phonepe Payment SDK  with Expo"
datePublished: Tue Dec 12 2023 07:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clq1ztd5l000g08l88xmp99fe
slug: integrating-phonepe-payment-sdk-with-expo
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Q59HmzK38eQ/upload/5a1123f21313f69cdc5b5db4e87a0515.jpeg
tags: react-native, payment-gateway, expo, upi, phonepe

---

In this blog we will solving the issue of linking through expo. The Phonepe document only has React Native integration but by following this blog you can integrate with Expo also.

### First go to root of the projects directory

```bash
npx expo install @expo/config-plugins 
#or
npm expo install @expo/config-plugins
```

```bash
mkdir plugins
cd plugins
```

### Create **PhonepePlugin.js**

```javascript
//PhonepePlugin.js
const { withProjectBuildGradle } = require('@expo/config-plugins');

const withMyPlugin = (config) => {
    return withProjectBuildGradle(config, (config) => {
        if (config.modResults.language === 'groovy') {
            if(!config.modResults.contents.includes("phonepe.mycloudrepo.io")) {
                // to avoid multiple occurence
                config.modResults.contents = modify(config.modResults.contents)
            }
        } else {
            throw new Error("Can't add maven repository to the build.gradle because the project is using the 'kts' language.");
        }
        return config;
    });
};

function modify (str) {
    // Find the first occurrence of "google()"
    const firstIndex = str.indexOf("google()");

    // Check if the first occurrence is found
    if (firstIndex !== -1) {
        // Find the second occurrence starting from the index after the first occurrence
        const secondIndex = str.indexOf("google()", firstIndex + 1);

        // Check if the second occurrence is found
        if (secondIndex !== -1) {
            const result = str.slice(0, secondIndex + 8) + `
            maven {
                url  "https://phonepe.mycloudrepo.io/public/repositories/phonepe-intentsdk-android"
           }
            ` + str.slice(secondIndex + 8);
            return result;
        }
    }

    // Return the original string if not found
    return str;
}
      
      


module.exports = withMyPlugin;
```

In app.json file

```json
{
  "expo": {
    //rest of the config
    "plugins": ["./plugins/PhonepePlugin"],
    
}
```

Then link the libraries with the project

```bash
expo prebuild 
npx expo prebuild --clean # may remove some files in android/ if u havent modified in android/ u are good\
```

**Note :** Only works on virtual device,

Have a cup of tea and enjoy the rest of the day!