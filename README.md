# CLIPZY AI — Android starter project

This is an Android Studio Kotlin + Jetpack Compose starter for the CLIPZY AI app.

## Included now
- Dark black + electric-blue interface
- YouTube URL input UI
- Android video picker (selects a local video)
- Clip quantity selector: 1–10 clips, default 5
- Clip settings display: 30–40 seconds, 9:16, 1080×1920, 2-second hook
- Download-first product flow UI

## Important: what is not implemented yet
This is **not a finished AI clipping engine and does not yet export clips**. The app UI currently accepts a URL or lets the user pick a video, but the processing actions are integration placeholders.

A real implementation still needs a secure backend that:
1. Accepts user-authorized video uploads or an authorized source URL.
2. Transcribes audio and detects highlight candidates.
3. Scores moments (a heuristic estimate, not a promise of virality).
4. Produces 30–40 second edit decisions and hook text.
5. Generates word-timed captions (Hindi/Hinglish/English).
6. Renders a 9:16 crop with captions and exports MP4.
7. Returns a downloadable file URL.

YouTube links cannot simply be downloaded or extracted by the app. Use YouTube's permitted APIs/flows and only process videos the user owns or has permission to use. Do not bypass YouTube access controls or copyright restrictions.

## Build the Android app
1. Install Android Studio on a computer.
2. Open this folder in Android Studio.
3. Allow Gradle sync.
4. Use JDK 17 and Android SDK 35.
5. Run on an Android device, or choose **Build > Build APK(s)**.

The generated debug APK will normally be at:
`app/build/outputs/apk/debug/app-debug.apk`

## Backend API contract (suggested)
`POST /v1/jobs` — multipart upload or authorized source reference; returns `{ "jobId": "..." }`

`GET /v1/jobs/{jobId}` — returns status and candidate clips.

`GET /v1/jobs/{jobId}/clips` — returns clip metadata and MP4 download URLs.

Keep AI/provider API keys on the backend, never in the APK.
