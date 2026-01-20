# Feature Implementation Prompt for CTJ AI App

**Role:** Expert Flutter Developer specializing in GetX, UI/UX Design (Glassmorphism), and Voice Interactions.

**Context:**
The current application (`lib/main.dart`) is a Voice AI Assistant built with Flutter and GetX. It features a distinct "Cosmic/Glassmorphism" design system using `GlassCard` and `CosmicBlob` widgets. The app currently handles Chat, Voice Studio, Settings, and History in a monolithic file structure (or loosely separated).

**Objective:**
Implement two new major features: **Smart Alarm Clock** and **Naam Jap (Mantra Chanting)**, ensuring they integrate seamlessly with the existing `AppColors`, `GlassCard` styles, and `GetX` architecture.

---

## Feature 1: Smart Alarm Clock with Day-Wise Ringtones

**Requirements:**

1.  **Voice Activation:**
    - The user should be able to say: _"Set alarm for 5 AM"_.
    - The system should parse this and set an alarm.
2.  **Day-Specific Ringtones (Gods/Deities):**
    - The app must allow setting specific ringtones for specific days (e.g., Tuesday = Hanuman Chalisa/Song).
    - **Logic:** If the alarm rings on a Tuesday, it checks the "Tuesday" configuration. If set, it plays that specific audio.
    - **Source:** Audio can be a local file (picked from storage) or a URL.
3.  **Snooze/Stop Logic:**
    - When the alarm rings, the user has **3 attempts** to stop it.
    - If snoozed or stopped, it counts as an attempt.
4.  **UI/UX:**
    - Create an `AlarmController` and `AlarmView`.
    - **Main Screen:** List of alarms with toggle switches.
    - **Settings Screen:** A "Day Wise Ringtone" configuration screen where users can map Mon-Sun to specific audio files.
    - **Ringing Screen:** A full-screen alarm view with "Slide to Stop" or "Snooze" buttons, featuring the `CosmicBlob` animation.

**Technical Implementation:**

- Use `flutter_local_notifications` or `android_alarm_manager_plus` for exact timing.
- Use `audioplayers` or `just_audio` for playing ringtones.
- Use `file_picker` for selecting local MP3s.
- Use `Hive` or `GetStorage` to save alarm data and day-wise preferences.

---

## Feature 2: Naam Jap (Mantra Chanting) Assistant

**Requirements:**

1.  **Voice Activation:**
    - User says: _"Set Ram and counter for 108 times"_.
    - App enters "Naam Jap" mode.
2.  **Core Logic:**
    - **TTS Chanting:** The AI (using `flutter_tts`) speaks the mantra (e.g., "Ram") repeatedly.
    - **Counter:** A visual counter decrements from the target (e.g., 108) or increments to it.
    - **Visuals:** A pulsing `CosmicBlob` or circular progress indicator that syncs with the chanting speed.
3.  **Stats & History:**
    - Track: Date, Mantra Name, Count, Duration.
    - **History Screen:** Show a list of past sessions.
    - **Graph:** Show "Daily Chants" or "Time Spent" using a simple chart (custom painter or package).
    - **Voice Query:** User can ask _"Provide me naam jap of 14th Jan"_, and the AI retrieves this data.
4.  **UI/UX:**
    - Create `NaamJapController` and `NaamJapView`.
    - **Active Session Screen:** Minimalist, spiritual but modern (Cosmic theme). Large counter text.
    - **History Screen:** Glassmorphic list of past sessions.

---

## Deliverables

Please generate the following code:

1.  **Dependencies:** List of packages to add to `pubspec.yaml` (hive, flutter_tts, file_picker, etc.).
2.  **Controllers:**
    - `AlarmController`: Handles scheduling, ringtone logic, and day checks.
    - `NaamJapController`: Handles the chanting loop, counter, and history saving.
3.  **Views:**
    - `AlarmView`: UI for managing alarms and day settings.
    - `NaamJapView`: UI for the chanting session.
4.  **Integration:**
    - Show how to add these pages to the `GetPage` list in `main.dart`.
    - Show how to update `HomeController` to recognize the voice commands and navigate to these new screens.

**Style Guide:**

- Use `AppColors.backgroundDark`, `AppColors.primary` (Cyan), `AppColors.secondaryOrange`.
- Use `GlassCard` for all containers.
- Use `GoogleFonts.spaceGrotesk` (as per existing theme).
- Keep code clean and modular.
