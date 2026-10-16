# Test plan: before and after GitHub Pages deployment

## Confirmed previously in Linux headless Chromium (2026-10-15)

The earlier Browser v2.0 HTML was tested for a single MP4 conversion, portrait resizing, sequential batch processing, cancellation, invalid input handling, output-size discard and downloading. Audio was detected, but **Opus-in-MP4** rather than AAC occurred. Details remain in the earlier local package.

## This Pages adaptation

- Static site consists only of `index.html` plus documentation; no build process or server runtime.
- Added CSP restricting `connect-src` to `none`.
- Resolved a per-task cancellation polling interval that otherwise persisted after successful transcoding.
- This adaptation needs both local smoke tests and browser-specific end-to-end testing.

## Live verification checklist

1. Confirm the URL returns HTTP 200 over HTTPS.
2. Confirm the browser console shows no uncaught errors and that MP4/H.264 capability displays as available or a clear unsupported message.
3. Add a synthetic or non-sensitive MP4 with audio; compress and download output. Confirm its stream codec/audio playback using MediaInfo or FFprobe.
4. Check landscape and portrait resolutions (preserving aspect ratio, maximum 720p), sequential jobs, cancellations and the size-discard setting.
5. In Chrome/Edge, test `Choose folder` (requires secure context and user permission).
6. Open browser Network panel: ensure no file upload; only the static web page is fetched.
7. Repeat on target Windows 11 machine. Browser support differs by OS/version.

**Do not publish sample personal videos, source video thumbnails, or exported reports.**