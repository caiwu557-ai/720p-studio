# 720p Studio — Editorial Edition v2.2

A dependency-free, static browser application for batch-converting browser-decodable videos to MP4 with a maximum output canvas of 1280×720 (or 720×1280 in portrait orientation). The browser performs processing locally; the application does not upload video data to any server.

## Editorial Edition v2.2

- Warm-paper editorial interface with serif display typography, restrained olive and terracotta palette, responsive desktop/mobile layout.
- Reorganized workspace, settings, system capabilities and processing log to prevent large empty regions on wide screens.
- Live three-stage workflow indicator, informative progress animation, and drag/drop/button/list feedback, with reduced-motion support.
- Browser encoding functionality, local-only processing and codec limitations are retained.

## Using the app

Open `index.html` in current Chrome/Edge or visit its GitHub Pages deployment. Choose one or more video files, select a quality preset, and start. Choose an output folder if your browser exposes the File System Access API; otherwise download each converted video using the task's download button.

## Privacy and security

- No video upload, login, analytics, external scripts, or network endpoint in the application.
- Content-Security-Policy explicitly disables JavaScript network connections (`connect-src 'none'`).
- Input files are read locally via browser File API and object URLs. Output is downloaded or written to an explicitly selected local folder.
- **The public GitHub repository contains source code only, never users' media.** Do not commit real videos or personal/private data.

## Important compatibility boundaries

- Uses `MediaRecorder`, `Canvas.captureStream` and browser-native video decoding, **not FFmpeg**. Not all video formats/codecs are supported. Unsupported browsers disable compression.
- Exports an MP4 video stream using the H.264 MediaRecorder capability where available. Audio codec **may be Opus inside MP4 rather than AAC** in some Chromium environments; compatibility with players varies.
- Processes video at approximately playback speed, not a fast offline transcoder; keep the tab open and active during processing.
- Output bitrate is advisory, and output size may be larger than input. By default, the application discards such results.
- Preserves aspect ratio, does not upscale source video, and does not retain multiple audio tracks, subtitle tracks, or HDR metadata.
- Browser performance, media support, folder-saving permissions and MP4 codec output must be checked in the actual target environment.

## GitHub Pages deployment

1. Create an empty **public** repository named `720p-studio` under your GitHub account (do not initialize with sample videos).
2. Upload `index.html`, `.nojekyll`, `README.md`, `.gitignore`, and `PRIVACY.md` to its `main` branch.
3. In the repository, go to **Settings → Pages → Build and deployment → Source: Deploy from a branch**, choose `main` and `/(root)`, and save.
4. GitHub manages subsequent Pages deployments automatically when `main` is updated. Verify the **Visit site** URL displayed under Pages.

Expected URL **only after publishing**: `https://caiwu557-ai.github.io/720p-studio/`.

## Testing

See [TESTING.md](TESTING.md). Do not claim end-to-end GitHub Pages or Windows verification before running those tests.

## License

This repository uses the MIT License; see [LICENSE](LICENSE).