This is an [Expo](https://expo.dev) project.

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
    npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

Install recommended VSCode extensions:
[ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
[Prettier extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

Get connected to EAS project - Contact Brad - give him the email that you want to use for your EAS account

If you're using `nvm` then execute `nvm use`. If not, we recommend Node v22.12.0.

`npm install -g expo-cli`
`npm install -g eas-cli`

Run `eas login` and login with your email and password that you used when you setup your account.
Run `npm run build:android:devclient:remote` or `npm run build:ios:simulator:devclient:remote` (if you're on MacOS)
Install the results on your emulator or simulator.
Run `npm run start`
Hit 'a' or 'i' to open up the Android emulator or iOS Simulator respectively.
The app should automatically open on the emulator/simulator for you.

Next Steps:
Work on building the devclient locally.
Run `npm run build:android:devclient` or `npm run build:ios:simulator:devclient` and install build dependencies as needed.
At a mimimum, you'll need the Android SDK with at least 1 OS, Emulator and Build tools installed.
For iOS, you'll need Xcode, an iOS Framework SDK and Simulator installed. Also, you'll need Fastlane for iOS builds.
Here are the Fastlane docs, there are a couple of ways ti install it. I believe that I just did `brew install fastlane` on my Mac.
https://docs.fastlane.tools/getting-started/ios/setup/

Customized build commands

Local build commands (these build using your local machine resources/configuration)
We have a limited number of remote builds per month so local builds are the recommended way to build.
It does take additional effort to configure your system for local builds though (you need all of the sdks and build tools installed).

```shell
npm run build:android:devclient
npm run build:ios:devclient
```

The devclient (short for development client) is a native mobile app that hosts the React Native rendering platform. Think of it like the native shell in which your React code runs. It does not contain a version of your react code itself. It connects to a Metro Server (typically running on your local machine) to receive the relevant markup and js files for rendering and execution.

Since devclients are native apps, they need to be installed on devices (or emulators) just like normal apps that are outside the context of an app store. They need to be side-loaded.

For iOS I do this by plugging my device into my Mac. Opening Finder. Clicking on the device in Finder; this will open an information screen about the device. Open another Finder window and locate your .ipa file in it; it's typically generated/located in the root of your repo. Click, drag and drag the .ipa onto the information screen for your device in the other Finder window. As long as the .ipa has been signed for your device (this is specified during the steps of the build process), the devclient should install on the device.

TODO: Include instructions on where to look if the app does not install correctly. In my experience, you don't typically receive an error; it just ignores the drop. You have to go looking for the error. Maybe in the Organizer (in xcode) somewhere? I can't remember.

For Android, I typically side-load the .apk onto devices or emulators using `adb` commands (`adb` is installed as part of the Android SDK, Build Tools I believe).
You'll likely find the following commands useful:

List android devices

`adb devices`

Install apk on Android device

`adb install build-1685398802155.apk`
`adb -s deviceid install build-####.apk`

The iOS Simulator is different from normal iOS devices, you cannot install .ipa files on it. So you need a different build artifact to install on iOS Simulators, hence the below command.

`npm run build:ios:simulator:devclient`

This command generates a .tar.gz file at the root of your repo. When you extract it, you will see an iOS application file. Find this file in a Finder window then drag and drop it onto an iOS Simulator window. This will install the app on the Simulator.

The below commands generate production builds (.apk or .ipa) for their respective OSes.

```shell
npm run build:android:production
npm run build:ios:production
```

The below command generates a iOS preview build (a .ipa). Preview builds are typically distinguished from Production builds somehow visually (tag on the icon, different color scheme or something). These are typically used for distributing builds to testers via TestFlight. Their devices need to be configured in the Apple Developer account first though and you'll need to specify the appropriate device ids for the build during the build steps.

`npm run build:ios:preview`

Remote build commands (these build using Expo Application Services (EAS) build servers)
We have 30 remote builds per month as we're on the free plan. These builds can also have rather long queue lines/wait times.
You also need to have access to our Expo Application Services project to do this. Contact Brad for access. You'll need to provide an email address to use for your EAS account.
The remote versions of the commands generate the same output. It's just on Expo's servers. The cli provides you a way to download the artifacts.

```shell
npm run build:android:devclient:remote
npm run build:ios:devclient:remote
npm run build:ios:simulator:devclient:remote
npm run build:android:production:remote
npm run build:ios:production:remote
npm run build:ios:preview:remote
```

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.

Onboarding for iOS real device builds
Get connected to iOS developer account - Contact Brad
