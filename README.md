# RUN: Create a Fabric Component Without Codegen

This Run lets you create a Fabric Component without using Codegen.

To avoid to manually write a lot of boilerplate, you will still use the Codegen to get the code you need.

Then, you will move that code to the Fabric Component and you will disable the Codegen for the component.

## TOC

* [[Setup] Use the colored-view from other branch](#colored-view)
* [[App] Create an app using the latest template](#create-app)
* [[App] Add the Fabric Component to the app and generate the code](#codegen)

## Steps

### [[Setup] Use the colored-view from other branch]()

To avoid excessive boilerplate, you will use a Fabric Component we already created in other branches of this same repository.

1. Go to [RNNewArchitectureLibraries](https://github.com/react-native-community/RNNewArchitectureLibraries/tree/feat/back-fabric-component-070)
2. Download the colored-view folder into the workspace

### [[App] Create an app using the latest template]()

1. `npx react-native init NewArchitecture --version next`

**Note:** The app is not committed to the repo not to pollute it

### [[App] Add the Fabric Component to the app and generate the code]()

1. `cd NewArchitecture`
2. `yarn add ../colored-view`
3. `cd ios && bundle install && RCT_NEW_ARCH_ENABLED=1 bundle exec pod install && cd ..`
4. `npx react-native run-ios`
5. Open the `android/gradle.properties` file and turn the `newArchEnabled` flag to true.
6. `npx react-native run-android`
7. Update the `NewArchitecture/App.js` file with the following code, to make sure that the component is actually working.

```ts
/**
 * Sample React Native App
* https://github.com/facebook/react-native
*
* @format
* @flow strict-local
*/

import React from 'react';
import type {Node} from 'react';
import {
    SafeAreaView,
    StatusBar,
    Text,
    View,
} from 'react-native';

import ColoredView from 'colored-view/src/index'

const App: () => Node = () => {

return (
    <SafeAreaView>
    <StatusBar barStyle={'dark-content'} />
    <ColoredView color="#FF0099" style={{marginLeft:10, marginTop:20, width:100, height:100}}/>
    </SafeAreaView>
    );
};

export default App;
```
