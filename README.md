# ctj-chat_app
CTJ AI is a production-oriented Flutter application that combines an AI-style voice assistant with devotional utilities such as Naam Jaap, alarms, smart notifications, and contextual sound feedback.

This project is built with a strong focus on **clean architecture**, **real-world edge cases**, and **professional user experience**, making it suitable for showcasing advanced Flutter development skills.

---

## ✨ Key Features

### 🎙 Voice Assistant
- Real-time Speech-to-Text (STT)
- Text-to-Speech (TTS) responses
- Wake-style interaction flow
- Context-aware speaking pace (story vs utility mode)

### 🕉 Naam Jaap System
- Custom mantra or sentence input
- Configurable repetition count (default 108)
- Start, progress, stop, and completion notifications
- Professional toast notifications with sound & glow effects
- Notification queue to prevent overlap
- Safe fallback when system notifications fail

### ⏰ Alarm & Scheduling
- Day-wise alarm configuration
- Devotional day mapping
- Custom ringtone support (local or asset-based)
- Snooze & retry handling

### 🌦 Live Environment Data
- Current temperature using Open-Meteo API
- AQI (Air Quality Index)
- GPS-based location detection
- Internet & permission validation before fetch

### 🔊 Sound & Feedback System
- Contextual sound effects (UI, success, alerts, emotions)
- Centralized sound manager with failure recovery
- Vibration support (device dependent)

---

## 🧠 Architecture & Tech Stack

- **Flutter (Material + Dark Theme)**
- **GetX** – State management, routing, dependency injection
- **Hive** – Lightweight local storage
- **SharedPreferences** – User settings persistence
- **Flutter Local Notifications**
- **Speech-to-Text & Flutter TTS**
- **AudioPlayers**
- **Geolocator & Connectivity Plus**
- **REST APIs (Weather, AQI, Search)**

---

## 🧩 Highlights for Recruiters

- Clean separation of services, controllers, and UI
- Defensive programming with fallback mechanisms
- Queue-based notification handling
- Graceful permission & connectivity management
- Scalable architecture for future AI expansion
- Real-world feature complexity beyond tutorials

---

## 🚀 How to Run

```bash
flutter pub get
flutter run
