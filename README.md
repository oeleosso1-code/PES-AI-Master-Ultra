# EFootball Vision — Android source prototype

This is a **source-code prototype**, not a compiled APK or a trained autonomous game-playing bot.

Implemented:
- Consent-based MediaProjection foreground capture with acquireLatestImage and an atomic latest-frame slot.
- Advisory behavior-tree decision engine and WorldState.
- Geometry-only normalized coordinate calibration and cubic Bézier path generation. No touch injection.
- Floating tactical selector overlay.
- Generic ONNX Runtime tensor inference (model-specific preprocessing, output decoding, NMS and tracking are not included).

## Build
Open this folder in Android Studio with JDK 17 and Android SDK 35; allow Gradle dependency sync. Build the `app` module. No Gradle wrapper is included. Android API/Gradle compatibility should be validated in the target development environment. No build has been run here.

## Limitations
- No ONNX model is bundled. Inference helper is not yet connected to capture; no detections or real stats are shown.
- A 60 FPS / <16 ms end-to-end guarantee is **not** supported; measure on the target device.
- `latestFrame` is a simple atomic slot; consumers must release bitmaps after processing and coordinate ownership with the producer. It is not production-safe for simultaneous readers without a stronger ownership protocol.
- UI dimensions, control coordinates and model class labels need calibration from real, permitted capture data.
- This project does not bypass game anti-cheat, impersonate touches, or control matches automatically.
