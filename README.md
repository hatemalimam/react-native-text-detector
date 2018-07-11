# react-native-text-detector

## Getting started

`$ npm install react-native-text-detector --save` or `yarn add react-native-text-detector`

### Mostly automatic installation

`$ react-native link react-native-text-detector`

### Manual installation

#### iOS

1.  In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2.  Go to `node_modules` ➜ `react-native-text-detector` and add `RNTextDetector.xcodeproj`
3.  In XCode, in the project navigator, select your project. Add `libRNTextDetector.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4.  Run your project (`Cmd+R`)<

#### Android

1.  Open up `android/app/src/main/java/[...]/MainActivity.java`

- Add `import com.fetchsky.RNTextDetector.RNTextDetectorPackage;` to the imports at the top of the file
- Add `new RNTextDetectorPackage()` to the list returned by the `getPackages()` method

2.  Append the following lines to `android/settings.gradle`:
    ```
    include ':react-native-text-detector'
    project(':react-native-text-detector').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-text-detector/android')
    ```
3.  Insert the following lines inside the dependencies block in `android/app/build.gradle`:
    ```
      compile project(':react-native-text-detector')
    ```

## Usage

```javascript
/**
 *
 * This Example uses react-native-camera for getting image
 *
 */

import RNTextDetector from "react-native-text-detector";

export class TextDetectionComponent extends PureComponent {
  ...

  detectText = async () => {
    try {
      const options = {
        quality: 0.8,
        base64: true,
        skipProcessing: true,
      };
      const { uri } = await this.camera.takePictureAsync(options);
      const visionResp = await RNTextDetector.detectFromUri(uri);
      console.log('visionResp', visionResp);
    } catch (e) {
      console.warn(e);
    }
  };

  ...
}
```