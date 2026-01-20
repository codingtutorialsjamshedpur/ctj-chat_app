# Task List: Alarm & Naam Jap Features

- [ ] **Setup & Dependencies**
  - [ ] Check existing `pubspec.yaml`
  - [ ] Add `flutter_local_notifications`, `audioplayers`, `file_picker`, `hive`, `flutter_tts`, `fl_chart`, `intl`
  - [ ] Run `flutter pub get`

- [ ] **Feature: Naam Jap (Mantra Chanting)**
  - [ ] Create `NaamJapController` (Logic: TTS loop, counter, history)
  - [ ] Create `NaamJapView` (UI: Cosmic theme, counter, controls)
  - [ ] Implement History & Stats (Hive storage, Graph UI)

- [ ] **Feature: Smart Alarm Clock**
  - [ ] Create `AlarmController` (Logic: Scheduling, Day-wise check, Snooze)
  - [ ] Create `AlarmView` (UI: List, Toggle, Day-wise settings)
  - [ ] Implement Ringing Screen (Slide to stop, Snooze)

- [ ] **Integration**
  - [ ] Register new routes in `main.dart`
  - [ ] Update `HomeController` to handle voice commands for these features
  - [ ] Add navigation icons/buttons if needed

- [ ] **Verification**
  - [ ] Verify Naam Jap flow
  - [ ] Verify Alarm setting flow (mocking time if needed)
