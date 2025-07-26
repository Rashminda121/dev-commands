# Fixing Missing Gradle Wrapper and Cleaning Flutter Android Project

If you get the error:

```
zsh: no such file or directory: ./gradlew
```

this means your project is missing the Gradle wrapper script.

---

## Step 1: Navigate to the Android folder

Make sure you are inside your Flutter project’s Android directory:

```bash
cd android
```

---

## Step 2: Check if `gradlew` exists

List the gradlew file:

```bash
ls gradlew
```

If you see `No such file or directory`, proceed to Step 3.

---

## Step 3: Install Gradle (if not installed)

If you don't have Gradle installed on your Mac, install it via Homebrew:

```bash
brew install gradle
```

---

## Step 4: Regenerate Gradle Wrapper

Run this command inside the `android` folder to generate the Gradle wrapper:

```bash
gradle wrapper
```

This will create the following files:

- `gradlew`
- `gradlew.bat`
- `gradle/wrapper/gradle-wrapper.properties`
- `gradle/wrapper/gradle-wrapper.jar`

---

## Step 5: Make the wrapper executable

Make sure `gradlew` has execute permission:

```bash
chmod +x gradlew
```

---

## Step 6: Clean the Gradle build

Now you can clean your project:

```bash
./gradlew clean
```

---

## Step 7: Clean Flutter build and rebuild

Back to your Flutter project root directory:

```bash
flutter clean
flutter pub get
flutter build apk
```

or run the app:

```bash
flutter run
```

---

## Summary

This fixes the missing Gradle wrapper issue and cleans the Android build environment for Flutter.

---
