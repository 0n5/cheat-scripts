React Native Install
=====


#### OSX

Requires Xcode

Install Node via NVM or Homebrew

Install Watchman

    npm install -g watchman

Install React Native CLI

    npm install -g react-native-cli


#### App Creation

    react-native init cats  # scaffolds application


#### Run IOS Simulator

    cd cats
    react-native run-ios

xcrun: error: unable to find utility "instruments", not a developer tool or in PATH

    Open Xcode
    Click Xcode menu
    Select Preferences
    Select Location
    Set Command Line Tools to Xcode x.x if blank


#### Run on Mac (Xcode)

    Open cats/ios/cats.xcodeproj in Xcode
    Hit run # ios simulator should launch


