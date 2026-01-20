# TODO – Implement New Gesture-Based UI System

## Business Logic Status
✓ **All business logic is preserved** from running_code.txt (files are identical)
✓ **Controllers**: WeatherController, VoiceController (with all features)
✓ **Services**: GoogleSearchService, SoundEffectManager, SongDatabase
✓ **Models**: ApiConfig, personas, games list
✓ **Features**: STT, TTS, Image Generation, History, Settings

## Phase 1 – Add New UI Architecture (on top of existing business logic)

### 1.1 Import & Dependencies
- [ ] Verify GetX dependency exists (package:get/get.dart)
- [ ] Verify vibration package exists (package:vibration/vibration.dart)
- [ ] Add HapticFeedback import (package:flutter/services.dart)

### 1.2 Create Design Tokens Class
- [ ] Create DesignTokens class with colors (primaryBackground, chromeGold, deepAmber, neutralCyan, softWhite)
- [ ] Add spacing constants (XS, S, M, L, XL)
- [ ] Add radius constants (S, M, L)
- [ ] Add animation durations and curves

### 1.3 Create Helper Widgets
- [ ] GlassContainer widget (BackdropFilter, blur, border, shadow)
- [ ] ChromeButton widget (animated gradient, pressed state)
- [ ] ChromeRing widget (animated circular container)

### 1.4 Create Gesture System
- [ ] Create GestureHandler controller class
  - [ ] RxInt currentScreenIndex for navigation
  - [ ] dragDirection (up/down/left/right enum)
  - [ ] dragProgress (0.0 to 1.0)
  - [ ] isDragging flag
  - [ ] showPreview flag
  - [ ] startDrag(Offset) method
  - [ ] updateDrag(Offset) method
  - [ ] endDrag() method
  - [ ] cancelDrag() method
  - [ ] _commitGesture(GestureDirection) method
- [ ] Add gesture constants (previewThreshold: 0.4, commitThreshold: 0.7, maxDragDistance: 300.0)
- [ ] Implement haptic feedback (HapticFeedback.light/heavyImpact)

### 1.5 Create Visual Feedback
- [ ] Create GestureArcPainter (CustomPainter)
  - [ ] Draw arc based on drag direction
  - [ ] Glow effects at commit threshold
  - [ ] Color coding per direction
  - [ ] Commit indicator circle

### 1.6 Create Screen Enum
- [ ] Create AppScreen enum (home, personaSelection, voiceGames, settings, expandedRecording, expandedEditing, voiceStudio, imageCreator, history, subScreenNameInput, subScreenSpeakingVisualizer, subScreenGameResult)

## Phase 2 – Create New Main VoiceAssistantPage

### 2.1 Main Widget
- [ ] Create VoiceAssistantPage StatefulWidget
- [ ] Initialize GestureHandler in main()
- [ ] Initialize WeatherController in main()
- [ ] Initialize VoiceController in main()

### 2.2 State-Driven Navigation
- [ ] Replace Navigator.push() with GestureHandler.currentScreenIndex
- [ ] Build switch statement based on AppScreen enum
- [ ] Add GetX Obx() for reactive updates

### 2.3 Screen Routing
- [ ] Home screen → _buildHomeScreen()
- [ ] Persona Selection → _buildPersonaSelectionScreen()
- [ ] Voice Games → _buildVoiceGamesScreen()
- [ ] Settings → _buildSettingsScreen()
- [ ] Expanded Recording → _buildExpandedRecordingScreen()
- [ ] Expanded Editing → _buildExpandedEditingScreen()
- [ ] Voice Studio → _buildVoiceStudioScreen()
- [ ] Image Creator → _buildImageCreatorScreen()
- [ ] History → _buildHistoryScreen()

## Phase 3 – Screen Implementation (keeping existing business logic)

### 3.1 Home Screen (Screen 1)
- [ ] Glass AppBar with WeatherController.weatherData
- [ ] Center REC button with ChromeRing
- [ ] GestureDetector on REC button (onPanStart/Update/End)
- [ ] Bind to GestureHandler for drag detection
- [ ] Gesture hints (hidden by default, reveal on tap)
- [ ] Remove old Navigator-based navigation
- [ ] Keep VoiceController business logic

### 3.2 Persona Selection Screen (Screen 2)
- [ ] Glass AppBar with back arrow (GestureHandler.currentScreenIndex = home)
- [ ] Category selector (Standard, Gen-Z, Fun/Animal, Professional)
- [ ] Persona grid (2-column)
- [ ] Persona cards with VoiceController.getPersonaIcon()
- [ ] Selection animation (scale, border glow)
- [ ] On tap → VoiceController.setPersona() + auto-return to home

### 3.3 Voice Games Screen (Screen 3)
- [ ] Glass AppBar with trophy icon + back arrow
- [ ] Difficulty selector (Easy/Medium/Hard) → VoiceController.gameDifficulty
- [ ] Active game banner (if VoiceController.activeGame.value)
- [ ] Game grid (2-column) using VoiceController.games list
- [ ] Game cards (icons, descriptions, ChromeButton wrapper)
- [ ] On tap → VoiceController.startGame(gameId)

### 3.4 Settings Screen (Screen 4)
- [ ] Glass AppBar with save indicator + back arrow
- [ ] User profile card (VoiceController.userName, avatar)
- [ ] Toggle switches (isSoundEnabled, imageGenerationEnabled)
- [ ] Dropdowns (selectedApi, selectedVoice, selectedPersona)
- [ ] Voice speed selector (0.5x to 1.5x) → VoiceController.voiceSpeed
- [ ] Pitch slider (0.5 to 2.0) → VoiceController.pitch
- [ ] About section with Alpha badge

### 3.5 Expanded Recording Screen (Screen 5)
- [ ] Glass AppBar with back arrow
- [ ] Status bar with timer (recordingTime)
- [ ] Stats bar (word/char count from recordedText)
- [ ] Live transcription area (TextField with VoiceController.recordedText)
- [ ] Stop recording button (VoiceController.speech.stop())
- [ ] Clear button (recordedText.clear())

### 3.6 Expanded Editing Screen (Screen 6)
- [ ] Glass AppBar with back arrow
- [ ] Status bar with word count
- [ ] Editable TextField (VoiceController.textController)
- [ ] Send button → VoiceController.sendText() + navigate home
- [ ] Re-record button
- [ ] Discard button → navigate home

### 3.7 Voice Studio Screen (Screen 7)
- [ ] Glass AppBar with music icon + back arrow
- [ ] Visual EQ (simulated animation)
- [ ] Preset chips (Normal, Bass, Chip, Slow) → update pitch/speed
- [ ] Pitch slider → VoiceController.pitch
- [ ] Speed slider → VoiceController.voiceSpeed
- [ ] Preview button → VoiceController.speak()

### 3.8 Image Creator Screen (Screen 8)
- [ ] Glass AppBar with sparkles icon + back arrow
- [ ] Image display area (VoiceController._currentImage or loading state)
- [ ] Text input + Generate button
- [ ] Quick suggestion chips (tap to fill input)
- [ ] Generate → VoiceController._generateImage()

### 3.9 History Screen (Screen 9)
- [ ] Glass AppBar with search icon + back arrow
- [ ] Scrollable message list (VoiceController.messages)
- [ ] Empty state (if messages.isEmpty)
- [ ] Message cards (role, content, timestamp)
- [ ] Tap to copy/reuse message

## Phase 4 – Sub-Screens & Overlays

### 4.1 Name Input Dialog (Sub-Screen A)
- [ ] Keep existing _showNameInputDialog() logic
- [ ] Update to show using Get.defaultDialog
- [ ] On save → VoiceController.userName + close

### 4.2 Speaking Visualizer Overlay (Sub-Screen B)
- [ ] Keep existing SpeakingVisualizer widget
- [ ] Animate based on VoiceController.isSpeaking
- [ ] Show during TTS playback

### 4.3 Game Result Overlay (Sub-Screen C)
- [ ] Keep existing game result display logic
- [ ] Overlay during active games
- [ ] Show score, feedback, continue/retry options

### 4.4 Dropdown Menu Component
- [ ] Keep existing DropdownButton implementations
- [ ] Style with GlassContainer
- [ ] ChromeGold accents for selected items

### 4.5 Alert Dialogs
- [ ] Keep existing Get.defaultDialog calls
- [ ] Style with glassmorphism
- [ ] Error, info, confirmation dialogs

## Phase 5 – Controller Integration

### 5.1 Add to VoiceController
- [ ] Add selectedPersona = 'Straight Forward'.obs
- [ ] Add gameDifficulty = 'Medium'.obs
- [ ] Add games list (6 games with icons, descriptions)
- [ ] Add isSoundEnabled = true.obs
- [ ] Add imageGenerationEnabled = true.obs

### 5.2 Update Existing Methods
- [ ] setPersona() method (update selectedPersona, apply voice effects)
- [ ] applyPersonaEffects() method (adjust pitch, speed based on persona)
- [ ] getPersonasByCategory() method (filter personas list)
- [ ] getPersonaIcon() method (map persona to IconData)
- [ ] startGame() method (set activeGame, play sound)
- [ ] endGame() method (reset game state)

## Phase 6 – Screen Transitions

- [ ] Use GetX transitions (fade, slide, zoom)
- [ ] Configure in GetMaterialApp
- [ ] Smooth animations for GestureHandler.currentScreenIndex changes
- [ ] Spring-back effect for cancelled gestures

## Phase 7 – Testing

### 7.1 Unit Tests
- [ ] Test GestureHandler (drag thresholds, haptic feedback)
- [ ] Test screen switching (currentScreenIndex changes)
- [ ] Test controller bindings

### 7.2 Integration Tests
- [ ] Test all screens build without errors
- [ ] Test gesture recognition (drag directions)
- [ ] Test navigation flow (home → sub-screen → back)
- [ ] Test VoiceController integration (speak, record, settings)

### 7.3 Manual Testing
- [ ] Run app on emulator/device
- [ ] Test all gestures
- [ ] Verify no crashes
- [ ] Check performance (60fps)

## Phase 8 – Final Polish

- [ ] Optimize animations
- [ ] Verify all colors match DesignTokens
- [ ] Check accessibility (contrast, touch targets)
- [ ] Remove unused old Navigator code
- [ ] Add inline comments for gesture logic
- [ ] Final code review

## Notes

**Important**: Do NOT replace existing business logic in VoiceController, WeatherController, etc.
- Keep ALL methods: speak(), listen(), generateImage(), search(), etc.
- Keep ALL features: STT, TTS, weather, games, history, settings
- ONLY replace the UI navigation (Navigator → GestureHandler)

**Strategy**:
1. Add NEW classes at top of file (DesignTokens, GlassContainer, ChromeButton, GestureHandler, GestureArcPainter)
2. Modify VoiceAssistantPage to use NEW gesture-based navigation
3. Create NEW screen builder methods that call EXISTING business logic
4. Keep all EXISTING controllers and services UNCHANGED
