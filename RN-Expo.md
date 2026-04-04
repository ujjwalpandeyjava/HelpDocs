# React Native - Expo

Android + iOS apps

## Build app with base template uses TS

TS, basic, navbar

`npx create-expo-app@latest --template default@sdk-55`

`npx create-expo-app app-abc --template tabs`

`npx create-expo-app`

## Export an app build

EAS: Expo account

Repo is uploaded to the Expo account and app is build there not on local system.

### Process

- Install EAS: `npm install -g eas-cli`
- Login EAS: `eas login`
- Configure project: `eas build:configure`
  - Both platform: `eas build --platform all`
  - Build Android: `eas build -p android`
  - Build iOS: `eas build -p ios`

### Local build

Common

- npx expo prebuild

Android:

- cd android
- ./gradlew assembleRelease

output: android/app/build/outputs/apk/release/app-release.apk

iOS (need mac)

- cd ios
- open .xcworkspace
- Then build using Xcode → Archive → .ipa

### Rename Project

npx react-native-rename "GrowthLog"
