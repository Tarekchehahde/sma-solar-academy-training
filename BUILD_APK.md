# Building the APK

## Option 1: PWA to APK using PWABuilder (Recommended - No Setup Required)

1. Host the app on GitHub Pages or any web server
2. Go to https://www.pwabuilder.com/
3. Enter your hosted URL
4. Click "Start" and then "Build My PWA"
5. Select "Android" and download the APK

## Option 2: Using Cordova (Requires Android SDK)

### Prerequisites
- Node.js 16+
- Java JDK 11+
- Android SDK with:
  - Android SDK Platform 33
  - Android SDK Build-Tools 33.0.2
  - Android SDK Platform-Tools

### Setup Android SDK
```bash
# Set environment variables
export ANDROID_SDK_ROOT=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools
export PATH=$PATH:$ANDROID_SDK_ROOT/tools/bin

# Or install via Homebrew
brew install --cask android-commandlinetools
export ANDROID_SDK_ROOT=/Users/$(whoami)/.homebrew/share/android-commandlinetools

# Accept licenses and install required packages
yes | sdkmanager --licenses
sdkmanager "platform-tools" "platforms;android-33" "build-tools;33.0.2"
```

### Build APK
```bash
# Install dependencies
npm install

# Build debug APK
npm run build:android

# The APK will be at:
# platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

## Option 3: Using Capacitor

```bash
# Install Capacitor
npm install @capacitor/core @capacitor/cli @capacitor/android

# Initialize Capacitor
npx cap init "SMA Solar Academy" "com.sma.solaracademy.training"

# Add Android platform
npx cap add android

# Copy web assets
npx cap copy

# Open in Android Studio
npx cap open android

# Build APK from Android Studio
```

## Option 4: Online APK Builders

- **AppsGeyser**: https://appsgeyser.com/
- **WebIntoApp**: https://www.webintoapp.com/
- **Gonative**: https://gonative.io/

Simply upload your HTML file or provide the GitHub Pages URL.

## Quick Deploy to GitHub Pages

```bash
# Enable GitHub Pages in repository settings
# Source: Deploy from branch -> main -> / (root)

# Your app will be available at:
# https://YOUR_USERNAME.github.io/sma-solar-academy-training/
```

Then use PWABuilder to convert to APK.
