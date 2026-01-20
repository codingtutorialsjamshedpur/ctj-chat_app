# CTJ AI Voice Assistant - Implementation Plan

## Project Overview
- **App Name:** CTJ AI (Voice Assistant)
- **Type:** Flutter Application with AI Integration
- **Current Status:** ALPHA v1.0.0 (Testing & Feedback Phase)
- **Developer:** SHOURAV (CTJ TEAM)
- **Launch Date:** January 2026
- **Website:** codingtutorialsjamshedpur.fun

---

## Current Features Analysis

### ✅ Implemented Features
1. **Voice Input/Output**
   - Speech-to-Text (STT) using speech_to_text package
   - Text-to-Speech (TTS) using flutter_tts
   - Recording timer and live transcription display
   - Expanded recording and editing UI

2. **AI Chat Integration**
   - Multiple API support: Gemini 1.5 Flash, Gemini 1.5 Pro
   - Fallback APIs via OpenRouter (Xiaomi Mimo, Qwen)
   - Automatic key rotation to avoid rate limits
   - Chat history persistence (Hive)

3. **Real-Time Data Fetching**
   - Weather data (Open-Meteo API)
   - Air Quality Index (AQI)
   - Google Custom Search integration
   - Cryptocurrency prices (CoinGecko)
   - Local news
   - Nearby restaurants
   - Latest movies
   - Current time/date

4. **Interactive Voice Games**
   - 20 Questions
   - Roast Battle
   - Compliment Generator
   - Story Time
   - Debate Mode
   - Trivia Challenge
   - Astro Talk (Vedic Astrology, Numerology, Tarot, Losho Grid)

5. **Personas & Voice Customization**
   - Standard Personas (Straight Forward, Brief, etc.)
   - Gen-Z Personas (Slay Queen, No Cap, Bestie, Main Character)
   - Fun/Animal Personas (Dog, Cat, Lion, Monkey, Pig, Donkey, Toddler)
   - Professional Personas (Coach, Therapist, Teacher)
   - Voice speed control (0.5x - 2.0x)
   - Pitch/Bass control
   - Voice Studio with presets

6. **Sound Effects System**
   - Emotion-based sound effects
   - Animal sound effects for personas
   - Game sounds (level complete, time up, etc.)
   - Sound toggle in settings

7. **Image Generation**
   - Hugging Face Stable Diffusion API
   - BuildPicoapps fallback
   - Image display in chat with URL detection
   - Image Creator modal

8. **User Experience Features**
   - Weather and AQI display in AppBar
   - Animated splash screen
   - Liquid rainbow animated background
   - Digital face speaking visualizer
   - Glass morphism UI components
   - Message selection, copy, delete
   - Gesture controls (swipe to stop/repeat)
   - Swipe to delete messages
   - Like/favorite messages

9. **Settings & Profile**
   - User name/title (Mr./Mrs.) customization
   - Persistent user profile with topics tracking
   - Analytics logging
   - High score tracking for games
   - Settings persistence (SharedPreferences)

10. **Localization Support**
   - Hinglish TTS normalization
   - Multi-language support (Hindi/English)
   - Festival greetings calendar
   - Indian phone number support (for Wake Word - disabled)

---

## Phased Implementation Plan

### Phase 1: Code Organization & Architecture (Priority: HIGH)
**Objective:** Refactor monolithic main.dart into modular structure for maintainability

1.1 **Create Modular File Structure**
   - `/lib/services/` - API services, TTS, STT, etc.
   - `/lib/controllers/` - GetX controllers
   - `/lib/models/` - Data models
   - `/lib/widgets/` - Reusable UI components
   - `/lib/utils/` - Helper functions
   - `/lib/config/` - Constants and app config

1.2 **Extract Services**
   - `ApiService` - Handle all API calls
   - `TtsService` - Text-to-Speech wrapper
   - `SttService` - Speech-to-Text wrapper
   - `SoundEffectService` - Sound management
   - `StorageService` - Local storage wrapper
   - `AnalyticsService` - Event tracking

1.3 **Extract Controllers**
   - Move `VoiceController` to separate file
   - Move `WeatherController` to separate file
   - Create `GameController` for game logic
   - Create `SettingsController` for settings management

**Estimated Time:** 4-6 hours

---

### Phase 2: Feature Enhancements (Priority: HIGH)

#### 2.1 Enhanced Wake Word Detection
**Current State:** Disabled (Porcupine dependency error)
**Improvement:**
- Implement alternative wake word detection using local speech recognition
- Add custom wake word setting (e.g., "Hey CTJ", "Hello AI")
- Add "Hey Google" style hotword detection using on-device ML
- Consider TensorFlow Lite for wake word

**Files to Create:**
- `lib/services/wake_word_service.dart`

**Estimated Time:** 6-8 hours

#### 2.2 Cricket Integration
**Objective:** Add live cricket scores and updates (mentioned in idle prompts)

**Implementation:**
- Use cricapi or similar free cricket API
- Fetch live match scores, upcoming matches, player stats
- Create cricket-specific game or trivia

**Files to Create:**
- `lib/services/cricket_service.dart`
- `lib/models/cricket_match.dart`

**Estimated Time:** 4-5 hours

#### 2.3 Enhanced Song Database
**Current State:** Local song files with basic metadata
**Improvements:**
- Add Spotify integration for streaming
- YouTube Music search and playback
- Lyrics fetching and display
- Personalized recommendations based on listening history

**Files to Create:**
- `lib/services/music_service.dart`
- `lib/models/song.dart`

**Estimated Time:** 8-10 hours

#### 2.4 Context-Aware Suggestions
**Objective:** Smart proactive suggestions based on:
- Time of day
- User location
- Recent conversation topics
- Weather conditions

**Implementation:**
- Add suggestion engine in VoiceController
- Display floating suggestion chips
- Learn from user preferences

**Estimated Time:** 4-5 hours

---

### Phase 3: UI/UX Improvements (Priority: MEDIUM)

#### 3.1 Dark Mode Enhancement
**Objective:** Add proper dark/light theme toggle with smooth transitions

**Implementation:**
- Add theme controller with multiple themes (Dark, Light, OLED, Cyberpunk)
- Persist theme preference
- Add theme picker modal

**Files to Create:**
- `lib/controllers/theme_controller.dart`
- `lib/widgets/theme_selector.dart`

**Estimated Time:** 3-4 hours

#### 3.2 Accessibility Improvements
**Enhancements:**
- Larger text option
- High contrast mode
- Screen reader support for non-visual users
- Better focus indicators

**Estimated Time:** 4-5 hours

#### 3.3 Chat Enhancements
**Features to Add:**
- Message reactions (emoji)
- Reply threading
- Edit sent messages
- Search in chat history
- Export chat as PDF/Text
- Message categories/tags

**Estimated Time:** 6-8 hours

---

### Phase 4: Advanced Features (Priority: MEDIUM)

#### 4.1 Multi-Language Support
**Objective:** Full internationalization (i18n)

**Implementation:**
- Add ARB files for multiple languages (Hindi, English, etc.)
- Auto-detect device language
- Add language picker in settings

**Estimated Time:** 6-8 hours

#### 4.2 Offline Mode
**Objective:** Limited functionality without internet

**Implementation:**
- Cache common responses
- Use local LLM (e.g., smaller model on device)
- Show offline indicator in UI
- Queue requests for when connection returns

**Estimated Time:** 8-10 hours

#### 4.3 Voice Profiles
**Objective:** Multiple voice presets for different contexts

**Implementation:**
- Create voice profiles (Professional, Casual, Storytelling)
- Auto-switch based on content type
- User can create custom profiles
- Profile switching in quick settings

**Estimated Time:** 4-5 hours

---

### Phase 5: Performance & Optimization (Priority: MEDIUM)

#### 5.1 Code Optimization
**Tasks:**
- Reduce rebuilds with better Obx usage
- Implement lazy loading for chat history (beyond 50)
- Optimize image loading with better caching
- Debounce search/filter inputs
- Reduce memory footprint of controllers

**Estimated Time:** 4-6 hours

#### 5.2 Asset Optimization
**Tasks:**
- Compress all audio files
- Optimize images and icons
- Use vector (SVG) icons instead of PNG where possible
- Asset bundling strategy

**Estimated Time:** 2-3 hours

---

### Phase 6: Testing & Bug Fixes (Priority: HIGH)

#### 6.1 Unit Testing
**Coverage Goals:**
- Service layer: 80%+
- Controllers: 70%+
- Utility functions: 90%+

**Estimated Time:** 8-10 hours

#### 6.2 Integration Testing
**Test Cases:**
- API fallback scenarios
- Permission handling flows
- Game state transitions
- Storage operations
- Network error handling

**Estimated Time:** 6-8 hours

#### 6.3 UI Testing
**Tools:**
- Golden tests for UI components
- Widget tests
- Accessibility tests

**Estimated Time:** 6-8 hours

---

### Phase 7: Deployment Preparation (Priority: LOW)

#### 7.1 App Store Preparation
**Tasks:**
- Prepare screenshots
- Write app descriptions
- Create promotional assets
- Set up app icons for all sizes
- Prepare for iOS (TestFlight) and Android (Play Store)

**Estimated Time:** 4-6 hours

#### 7.2 Documentation
**Tasks:**
- User guide
- API documentation (for contributors)
- Contributor guide
- Privacy policy
- Terms of service

**Estimated Time:** 4-5 hours

---

## Risk Assessment

| Risk | Impact | Mitigation |
|-------|---------|------------|
| API quota limits | HIGH | Implement robust fallback chain, caching |
| Memory issues with large history | MEDIUM | Implement pagination/lazy loading |
| TTS compatibility issues | MEDIUM | Test on multiple devices, provide fallback voices |
| Network errors affecting UX | MEDIUM | Implement graceful degradation, offline mode |
| Wake word battery drain | MEDIUM | Implement smart activation/deactivation |
| Asset bloat increasing app size | LOW | Asset optimization, on-demand loading |

---

## Success Metrics

### Metrics to Track
1. **User Engagement**
   - Daily active users
   - Average session duration
   - Messages per session

2. **Performance**
   - App startup time (< 3 seconds)
   - API response time (< 2 seconds)
   - TTS latency (< 100ms)

3. **Quality**
   - Crash-free sessions > 99%
   - API success rate > 95%
   - User satisfaction rating > 4.0/5.0

---

## Dependencies to Consider Adding

```yaml
# Existing dependencies to evaluate:
- flutter_tts: ^3.8.5 ✅ (already have)
- speech_to_text: ^7.3.0 ✅ (already have)

# New dependencies to consider:
- flutter_tts: ^4.0.0 (upgrade for better voice support)
- flutter_local_notifications: ^17.0.0 (for proactive prompts)
- path_provider: ^2.1.0 (file export)
- share_plus: ^7.2.0 (share functionality)
- google_ml_kit: ^0.16.0 (on-device ML for wake word)
- spotify_sdk: ^2.3.0 (music integration)
- youtube_explode_dart: ^2.0.0 (YouTube integration)
- connectivity_plus: ^6.0.0 ✅ (already have)
- hive: ^2.2.3 ✅ (already have)
```

---

## Implementation Order Recommendation

**Week 1-2:** Phase 1 (Architecture) + Phase 2.1 (Wake Word)
**Week 3:** Phase 2.2-2.3 (Cricket + Music)
**Week 4:** Phase 3 (UI/UX Improvements)
**Week 5:** Phase 4 (Advanced Features)
**Week 6:** Phase 5 (Performance) + Phase 6 (Testing)
**Week 7:** Phase 7 (Deployment)

---

## Notes for Developer

1. **API Keys Security:** Consider moving hardcoded API keys to environment variables or secure storage
2. **Code Style:** Follow existing conventions (GetX for state management, reactive Obx widgets)
3. **Asset Management:** Keep sound files organized under assets/sounds/
4. **Testing Strategy:** Test each phase before moving to next
5. **Version Control:** Use feature branches for each phase

---

*Last Updated: January 16, 2026*
