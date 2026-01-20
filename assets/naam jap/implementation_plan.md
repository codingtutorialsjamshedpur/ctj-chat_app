# Implementation Plan - Smart Alarm & Naam Jap

## Goal Description

Implement two new major features: **Smart Alarm Clock** (with day-wise ringtones) and **Naam Jap Assistant** (mantra chanting with counter), integrating them into the existing Cosmic/Glassmorphism UI.

## User Review Required

> [!IMPORTANT] > **Dependencies**: Adding `flutter_local_notifications`, `file_picker`, `fl_chart`, and `timezone`.
> **Permissions**: Android permissions for Notifications and Alarms will need to be configured in `AndroidManifest.xml` (I will handle this, but user should be aware).

## Proposed Changes

### Dependencies

#### [MODIFY] [pubspec.yaml](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/pubspec.yaml)

- Add `flutter_local_notifications`, `file_picker`, `fl_chart`, `timezone`.

### Feature: Naam Jap (Mantra Chanting)

#### [NEW] [naam_jap_controller.dart](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/lib/controllers/naam_jap_controller.dart)

- `NaamJapController`: Manages TTS loop, counter logic, and saving history to Hive.
- `NaamJapSession`: Model class for history.

#### [NEW] [naam_jap_view.dart](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/lib/views/naam_jap_view.dart)

- `NaamJapView`: UI with pulsing `CosmicBlob`, large counter, and controls (Start/Stop).
- `NaamJapHistoryView`: List of past sessions and a simple chart using `fl_chart`.

### Feature: Smart Alarm Clock

#### [NEW] [alarm_controller.dart](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/lib/controllers/alarm_controller.dart)

- `AlarmController`: Handles scheduling notifications/alarms.
- `checkDayAndPlayRingtone()`: Logic to check the current day and play the specific deity's ringtone.

#### [NEW] [alarm_view.dart](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/lib/views/alarm_view.dart)

- `AlarmView`: List of active alarms.
- `DayWiseSettingsView`: UI to map days (Mon-Sun) to audio files.

### Integration

#### [MODIFY] [main.dart](file:///c:/Users/shour/OneDrive/Desktop/flutter%20practise/chat_ai/lib/main.dart)

- Register new routes: `/naam_jap`, `/alarm`, `/alarm_settings`.
- Update `HomeController` to parse voice commands:
  - "Set alarm for [time]" -> Triggers alarm logic.
  - "Set [mantra] and counter for [count]" -> Navigates to Naam Jap.

## Verification Plan

### Automated Tests

- None (Visual/Audio features are hard to unit test without extensive mocking).

### Manual Verification

1.  **Naam Jap**:
    - Say "Set Ram and counter for 5 times".
    - Verify TTS speaks "Ram" 5 times.
    - Verify counter decrements.
    - Check History screen for the entry.
2.  **Alarm**:
    - Set an alarm for 1 minute from now.
    - Wait for notification.
    - Verify correct ringtone plays (based on day).
    - Test "Snooze" logic (if feasible in short time).
