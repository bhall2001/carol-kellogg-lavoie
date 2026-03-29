# Memorial Slideshow

A fullscreen photo slideshow hosted on GitHub Pages with photos stored on Google Drive. Scan the QR code or visit the link to start.

**Live:** https://bhall2001.github.io/carol-kellogg-lavoie/

## QR Code

Scan to open the slideshow:

![QR Code](qr.png)

## How It Works

1. User scans QR code or opens the link
2. Splash screen shows "Tap anywhere to begin"
3. Tap enters fullscreen and starts the slideshow
4. Photos display in random order with crossfade, looping forever

## Adding or Removing Photos

1. Upload/delete photos in the [Google Drive folder](https://drive.google.com/drive/folders/19lQWvKuKKoZnLJxK1JjjOS2YZlAchBXd)
2. Make sure the folder is shared as "Anyone with the link"
3. Run the build script to regenerate `photos.js`:
   ```
   ./build-photos-js.sh 19lQWvKuKKoZnLJxK1JjjOS2YZlAchBXd
   ```
4. Commit and push — GitHub Pages will update automatically

## Adjusting Timing

Edit `index.html` and change these values near the top of the script:

```js
const CROSSFADE_MS = 2500;  // fade duration in milliseconds
const SLIDE_MS     = 7000;  // how long each photo stays on screen
```

If you change CROSSFADE_MS, also update the matching CSS line:
```css
transition: opacity 2.5s ease-in-out;
```

## Local Testing

Open `index.html` directly in a browser. Photos load from Google Drive so internet is required.

## Notes

- Photos are served via `lh3.googleusercontent.com` direct links
- HEIC files are skipped (browsers don't support them)
- Remove duplicates directly in the Google Drive folder before running the build script
- iOS does not support the Fullscreen API — slideshow works but stays in the normal browser viewport
