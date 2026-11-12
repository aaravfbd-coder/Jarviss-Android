# J.A.R.V.I.S. — Phone-first starter

Target: Nothing Phone (3a) Lite, Nothing OS 4.1 / Android 16.
Build approach: HTML dashboard + native Android companion.

## What this starter actually implements
- Native Android app shell with microphone permission request from a visible activity.
- Speech-to-text while the app is open (Android SpeechRecognizer availability varies).
- Android TextToSpeech output using installed system voices.
- Flashlight toggle through CameraManager.
- Launch installed apps through package launch intents.
- Dialler handoff only (`ACTION_DIAL`), so every call requires the user to tap Call.
- Exact alarm scheduling scaffold using AlarmManager and `SCHEDULE_EXACT_ALARM`.
- Notification channel and alarm receiver.
- HTML dashboard asset bundled in the Android app.

## Important limitations
- This is a starter source project, not a signed/installed APK.
- It does NOT provide a guaranteed custom "Hey JARVIS" hotword. Android's VoiceInteractionService can be kept by the system for hotwording when selected as the active assistant, but custom hotword detection still depends on device/system hotword enrollment and supported hardware.
- Screen-off microphone use is not guaranteed. Android restricts background microphone services.
- Research requires a live web search/backend; this starter opens browser search. AI API keys must never be put in HTML or APK.
- Blinkit/Zepto/Instamart are user-assisted app handoffs; no private API/cart automation or unattended ordering.
- ElevenLabs is not connected. Android TTS is used as a zero-cost fallback. A real ElevenLabs integration requires a secure backend and an eligible API account.
- The phone's built-in alarm app remains the reliable fallback for critical wake-up alarms.

## Build without a computer
1. Upload this ZIP's extracted project to a GitHub repository using GitHub's mobile website/app.
2. Open the repository's Actions tab and run the workflow `Build Android APK`.
3. Download the generated APK artifact from the completed workflow.
4. Install it on your phone, reviewing Android's install warning and app permissions carefully.

GitHub Actions availability and free minutes/limits depend on account policy. Do not enter API keys into repository files.

## First-run permissions
- Microphone: requested while app is visible.
- Camera: only needed for flashlight hardware access on some devices; Android's torch API may work without camera preview. Runtime behaviour varies.
- Notifications: Android 13+ permission.
- Alarms & reminders: enable the special access only if JARVIS alarm scheduling is used.
- Battery optimization: do not disable system protections unless the app's tested behaviour genuinely requires it.

## Current command examples
- "turn on flashlight"
- "turn off flashlight"
- "open WhatsApp"
- "call [contact]" -> opens dialler; user confirms call
- "set alarm 7:30" -> asks Android to schedule a reminder alarm
- "research [topic]" -> opens web search

This project is an honest foundation; device testing is still required.
