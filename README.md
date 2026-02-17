# fenn iOS

minimal neumorphic browser for iOS built with Capacitor

## Features
- Persistent webview tabs
- Bookmarks with localStorage persistence
- Download tracking
- 7 search engines (Google, DuckDuckGo, Brave, Ecosia, Bing, Yahoo, Startpage)
- Dark mode
- Neumorphic UI design

## Setup

### Prerequisites
- Node.js 18+
- npm or yarn

### Installation

1. Clone the repo:
```bash
git clone https://github.com/ac3d1t/fenn-ios.git
cd fenn-ios
```

2. Install dependencies:
```bash
npm install
```

3. Initialize Capacitor and add iOS platform:
```bash
npx cap init fenn com.ac3d1t.fenn --web-dir=www
npx cap add ios
npx cap sync ios
```

## Building

### Automatic Build (GitHub Actions)

Push a tag to trigger an automatic build:
```bash
git tag v1.0.3-ios
git push origin v1.0.3-ios
```

The workflow will:
1. Build the iOS app
2. Generate an unsigned IPA
3. Upload it as a release asset

### Manual Build (requires macOS + Xcode)
```bash
npx cap open ios
```

Then in Xcode:
1. Select "Any iOS Device" as the build target
2. Product → Archive
3. Distribute App → Custom → Export

## Installing the IPA

### Option 1: AltStore (Recommended)
1. Download AltStore from altstore.io
2. Install AltStore on your Mac
3. Download the `.ipa` file from GitHub releases
4. Open AltStore and drag the IPA to install

### Option 2: Sideloadly
1. Download Sideloadly from sideloadly.io
2. Connect your iPhone via USB
3. Drag the IPA into Sideloadly
4. Sign with your Apple ID
5. Install to device

### Option 3: Xcode (Free, 7-day signing)
1. Connect iPhone to Mac
2. Open `ios/App/App.xcworkspace` in Xcode
3. Change bundle ID to something unique
4. Select your device as target
5. Product → Run

## Development

Edit `www/index.html` to modify the app, then:
```bash
npx cap sync ios
npx cap open ios
```

## Project Structure
```
fenn-ios/
├── www/
│   └── index.html          # Main app file
├── ios/                    # Generated iOS project
├── .github/
│   └── workflows/
│       └── build-ios.yml   # GitHub Actions workflow
├── capacitor.config.json   # Capacitor configuration
├── ExportOptions.plist     # IPA export settings
└── package.json
```

## Troubleshooting

**Build fails on GitHub Actions:**
- Check that all dependencies are installed
- Ensure capacitor.config.json has correct appId

**App crashes on launch:**
- Check Console.app for crash logs
- Verify all Capacitor plugins are compatible with iOS version

**Can't install IPA:**
- Make sure device is in Developer Mode (Settings → Privacy & Security → Developer Mode)
- For AltStore, ensure WiFi sync is enabled in iTunes

## License

MIT
