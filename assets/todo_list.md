# TODO – UI + Business Logic Stitching

## Phase 1 – Architecture Setup

- [ ] Read both input files (running_code.txt and UI mapping doc)
- [ ] Create single-file main.dart skeleton structure
- [ ] Move all controllers into main.dart
- [ ] Define screen enums for state-driven navigation
- [ ] Verify GetX dependency order

## Phase 2 – Design System Implementation

- [ ] Implement global design tokens (colors, typography, spacing)
- [ ] Create glassmorphism widget helper functions
- [ ] Implement chrome/gold accent decorations
- [ ] Setup animation constants and easing curves
- [ ] Create reusable widget builders (buttons, cards, headers)

## Phase 3 – Main App & Navigation

- [ ] Create MyApp widget with GetMaterialApp
- [ ] Implement SplashScreen with existing animations
- [ ] Setup main VoiceAssistantPage with screen switcher
- [ ] Implement RxInt currentScreenIndex for navigation
- [ ] Create screen switching animations

## Phase 4 – Home / REC Screen (Screen 1)

- [ ] Implement glass AppBar with weather widget
- [ ] Bind WeatherController to UI elements
- [ ] Create REC control with chrome ring
- [ ] Implement REC idle metallic animation
- [ ] Add gesture hints (hidden by default, reveal on touch)

## Phase 5 – Gesture Recognition System

- [ ] Implement drag UP gesture (40% preview, 70% commit)
- [ ] Implement drag DOWN gesture (40% preview, 70% commit)
- [ ] Implement drag LEFT gesture (40% preview, 70% commit)
- [ ] Implement drag RIGHT gesture (40% preview, 70% commit)
- [ ] Add spring-back animation for early releases
- [ ] Add haptic feedback at commit zones
- [ ] Visual feedback states for each drag direction

## Phase 6 – Persona Selection Screen (Screen 2)

- [ ] Implement header bar with back arrow
- [ ] Create category cards (Standard, Gen-Z, Fun/Animal, Professional)
- [ ] Implement persona card grid layout
- [ ] Add persona icons and labels
- [ ] Implement selection animation and confirmation
- [ ] Auto-return to home after selection

## Phase 7 – Voice Games Hub (Screen 3)

- [ ] Implement header bar with trophy icon
- [ ] Create active game banner (conditional)
- [ ] Implement difficulty selector (Easy/Medium/Hard)
- [ ] Create game grid (2-column responsive)
- [ ] Implement game cards with icons and descriptions
- [ ] Add game start animations and sounds

## Phase 8 – Settings Screen (Screen 4)

- [ ] Implement header bar with save indicator
- [ ] Create user profile card with avatar
- [ ] Implement toggle switches (Sound, Image Generation)
- [ ] Create dropdown selectors (AI Model, Voice, Persona)
- [ ] Implement voice speed selector buttons
- [ ] Implement voice pitch slider
- [ ] Add About section with Alpha badge

## Phase 9 – Expanded Recording Screen (Screen 5)

- [ ] Implement status bar with recording timer
- [ ] Create stats bar (word/char count)
- [ ] Implement live transcription area
- [ ] Add blinking cursor animation
- [ ] Create stop recording and clear buttons
- [ ] Bind to existing VoiceController STT logic

## Phase 10 – Expanded Editing Screen (Screen 6)

- [ ] Implement status bar with word count
- [ ] Create editable text area
- [ ] Add send message button (primary)
- [ ] Create re-record and discard buttons (secondary)
- [ ] Bind to existing VoiceController text editing

## Phase 11 – Voice Studio Screen (Screen 7)

- [ ] Implement header bar with music icon
- [ ] Create visual EQ (simulated animation)
- [ ] Implement presets section (Normal, Bass, Chip, Slow)
- [ ] Add pitch slider with visual feedback
- [ ] Add speed slider with visual feedback
- [ ] Bind to existing VoiceController voice settings

## Phase 12 – Image Creator Screen (Screen 8)

- [ ] Implement header bar with sparkles icon
- [ ] Create image display area (empty/loading/generated states)
- [ ] Implement text input with generate button
- [ ] Add quick suggestion chips
- [ ] Bind to existing image generation logic

## Phase 13 – History Screen (Screen 9)

- [ ] Implement header bar with search icon
- [ ] Create scrollable message list
- [ ] Implement empty state
- [ ] Add message item cards with headers
- [ ] Bind to existing messages history

## Phase 14 – Sub-Screens & Overlays

- [ ] Implement name input dialog (Sub-Screen A)
- [ ] Create speaking visualizer overlay (Sub-Screen B)
- [ ] Implement game result card overlay (Sub-Screen C)
- [ ] Add dropdown menu component
- [ ] Implement alert dialogs

## Phase 15 – Controller Integration & Wiring

- [ ] Wire WeatherController to home screen
- [ ] Wire VoiceController to all screens
- [ ] Bind persona selection to controller state
- [ ] Bind settings changes to controller
- [ ] Wire game logic to controller
- [ ] Integrate sound effects with UI events

## Phase 16 – Animations & Transitions

- [ ] Implement all screen transition animations
- [ ] Add gesture arc glow animations
- [ ] Create REC control state animations
- [ ] Implement speaking visualizer animations
- [ ] Create visual EQ pulse animations
- [ ] Add card hover/selection animations

## Phase 17 – Testing & Refinement

- [ ] Test all gesture recognitions
- [ ] Verify screen switching works correctly
- [ ] Test haptic feedback triggers
- [ ] Verify all controllers bind properly
- [ ] Test settings persistence
- [ ] Verify TTS/STT functionality
- [ ] Test game selection and activation
- [ ] Run app and verify no crashes

## Phase 18 – Final Polish

- [ ] Optimize animations for performance
- [ ] Verify all colors match design tokens
- [ ] Check accessibility (contrast, touch targets)
- [ ] Clean up unused code
- [ ] Add inline comments for complex logic
- [ ] Final code review

## Notes & Refactoring Log

- All business logic preserved from running_code.txt
- UI completely replaced with new gesture-based system
- Navigation changed from Navigator.push to state-driven RxInt
- Screens implemented as functions, not separate widgets
- Glassmorphism implemented with BackdropFilter
- Chrome/gold accents implemented with gradients and borders
- Gesture-based navigation with commit zones at 60% drag
- All animations implemented inline with AnimationController
