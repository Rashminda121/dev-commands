# 🚀 Run Flutter App with Emulator

This guide explains how to run a Flutter app on an Android emulator using terminal commands on a macOS system (including M1/M2 chips).

---

## ✅ Prerequisites

- Flutter installed: [Flutter install guide](https://docs.flutter.dev/get-started/install/macos)
- Android Studio or command-line tools (for emulator)
- A virtual device (AVD) already created

---

## 🔍 Step 1: List Available Emulators

```bash
flutter emulators
```

Expected output:
```
1. emulator-5554 • Pixel_5_API_33 • Google • android-x86
```

---

## 🚀 Step 2: Launch the Emulator

```bash
flutter emulators --launch <emulator_id>
```

Example:
```bash
flutter emulators --launch Pixel_5_API_33
```

> If you’re not sure of the emulator name, copy it from the output of the previous step.

You can also list Android emulators via:
```bash
avdmanager list avd
```

---

## 🏃 Step 3: Run the Flutter App

```bash
flutter run
```

This command will:
- Detect the running emulator
- Build and deploy your Flutter app onto it

---

## ⚡ One-Liner Command

To launch an emulator and run the app in one step:

```bash
flutter emulators --launch Pixel_5_API_33 && flutter run
```

---

## 💡 Optional: Add Shell Alias for Quick Launch

Add this line to your `~/.zshrc` file:

```zsh
alias frun='flutter emulators --launch Pixel_5_API_33 && flutter run'
```

Then reload your shell:

```bash
source ~/.zshrc
```

Now, run your app anytime using:

```bash
frun
```

---

## 🛠 Troubleshooting

- If no emulators show up, create one using Android Studio > AVD Manager
- If Flutter can't find a device, make sure the emulator is **running** before `flutter run`
- For iOS, use `open -a Simulator` and then `flutter run`
