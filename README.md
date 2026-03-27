# Open Cast Receiver

A free, open-source Chromecast receiver with broad codec support.

## Features

- **HEVC/H.265 support** (on capable devices)
- **HLS streaming** (.m3u8)
- **DASH streaming** (.mpd)
- **MKV container** support
- **Standard formats** (MP4, WebM, etc.)
- **Clean, minimal UI**

## Receiver App ID

```
YOUR_APP_ID_HERE
```

> Replace with your registered App ID after setting up Google Cast Developer Console.

## Usage in Your App

### React Native (react-native-google-cast)

**Android** - `android/app/src/main/AndroidManifest.xml`:
```xml
<meta-data
  android:name="com.reactnative.googlecast.RECEIVER_APPLICATION_ID"
  android:value="YOUR_APP_ID_HERE"/>
```

**iOS** - `AppDelegate.swift`:
```swift
let receiverAppID = "YOUR_APP_ID_HERE"
```

### Web / Other Platforms

```javascript
const castSession = await cast.framework.CastContext.getInstance().requestSession();
// Use your registered App ID
```

## Self-Hosting Setup

### 1. Fork this repository

### 2. Enable GitHub Pages
- Go to repository Settings > Pages
- Source: Deploy from branch
- Branch: `main`, folder: `/ (root)`
- Save

Your receiver will be available at:
```
https://YOUR_USERNAME.github.io/open-cast-receiver/
```

### 3. Register with Google Cast

1. Go to [Google Cast SDK Developer Console](https://cast.google.com/publish)
2. Pay the one-time $5 registration fee
3. Click "Add New Application"
4. Choose "Custom Receiver"
5. Enter your GitHub Pages URL as the Receiver URL
6. Save and note your new **App ID**

### 4. Update your app

Replace the default receiver ID (`CC1AD845`) with your new App ID.

## How It Works

This receiver uses:
- **Google Cast Receiver Framework v3** - Required for all Cast receivers
- **Shaka Player** - Open-source player with broad codec support

When media is cast:
1. Receiver checks the content type
2. HLS/DASH/MKV streams use Shaka Player (better codec support)
3. Standard formats use the default Cast player
4. Falls back gracefully if one method fails

## Codec Support

| Codec | Support |
|-------|---------|
| H.264 | Yes |
| H.265/HEVC | Yes* |
| VP8 | Yes |
| VP9 | Yes |
| AAC | Yes |
| MP3 | Yes |
| Opus | Yes |
| DTS | Device-dependent |

*HEVC support depends on the Chromecast hardware:
- Chromecast 1st/2nd gen: No
- Chromecast 3rd gen: Limited
- Chromecast Ultra: Yes
- Chromecast with Google TV: Yes

## License

MIT License - See [LICENSE](LICENSE)

## Terms of Use

See [TERMS_OF_USE.md](TERMS_OF_USE.md)

**TL;DR:** This is just a video player. You are responsible for the content you cast.

## Contributing

Contributions welcome! Please open an issue or PR.

## Acknowledgments

- [Shaka Player](https://github.com/shaka-project/shaka-player) - Google's open-source media player
- [Google Cast SDK](https://developers.google.com/cast) - Cast framework
