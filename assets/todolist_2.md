# TODO List - UI/UX Implementation

Based on Complete Screen & Sub-Screen Mapping Document

## Phase 1: Core Screens (Priority: High)

- [ ] SCREEN 1: Home/Voice Control (Rest State)
  - [ ] Implement AppBar with Weather widget, User name, Icon row
  - [ ] Create REC Control (Chrome Ring) with SHOURAV A.I. branding
  - [ ] Add gesture hints (hidden by default, reveal on touch)
  - [ ] Implement idle state animation (metallic sweep)

- [ ] SCREEN 1A: Drag Up (Change Persona)
  - [ ] Implement touch start state (0-20% drag)
  - [ ] Implement anticipatory zone (20-60% drag) with arc illumination
  - [ ] Implement commit zone (60-100% drag) with haptic feedback
  - [ ] Implement release before commit with spring-back animation
  - [ ] Add transition to Persona Selection screen

- [ ] SCREEN 1B: Drag Down (Send/Confirm)
  - [ ] Implement touch start state
  - [ ] Implement anticipatory zone with lower arc illumination
  - [ ] Implement commit zone with checkmark icon
  - [ ] Add send action trigger with visual feedback

- [ ] SCREEN 1C: Drag Left (Interactive Voice Games)
  - [ ] Implement touch start state (horizontal)
  - [ ] Implement anticipatory zone with left arc and game icons
  - [ ] Implement commit zone with playful haptic feedback
  - [ ] Add transition to Voice Games Hub

- [ ] SCREEN 1D: Drag Right (Settings)
  - [ ] Implement touch start state
  - [ ] Implement anticipatory zone with gear icon rotation
  - [ ] Implement commit zone with mechanical haptic feedback
  - [ ] Add transition to Settings screen

## Phase 2: Secondary Screens

- [ ] SCREEN 2: Persona Selection
  - [ ] Create header bar with back arrow and title
  - [ ] Implement category cards (Standard, Gen-Z, Fun/Animal, Professional)
  - [ ] Create persona cards with icons and descriptions
  - [ ] Add tap interaction with scale animation and confirmation
  - [ ] Implement selection state with gold glow

- [ ] SCREEN 3: Voice Games Hub
  - [ ] Create header bar with trophy icon
  - [ ] Implement active game banner (conditional display)
  - [ ] Add difficulty selector (Easy/Medium/Hard)
  - [ ] Create game grid with 7 game cards
  - [ ] Implement tap interaction with game start sequence

- [ ] SCREEN 4: Settings
  - [ ] Create header bar with auto-save indicator
  - [ ] Implement user profile card with avatar
  - [ ] Add toggle switches (Sound Effects, Image Generation)
  - [ ] Create dropdown selectors (AI Model, Voice, Persona)
  - [ ] Implement voice speed selector buttons
  - [ ] Add voice pitch slider with range markers
  - [ ] Create About section with alpha badge

## Phase 3: Expanded Views

- [ ] SCREEN 5: Expanded Recording (While Listening)
  - [ ] Create status bar with pulsing red indicator and timer
  - [ ] Implement stats bar (word/char count)
  - [ ] Add live transcription area with scrolling text
  - [ ] Implement blinking cursor
  - [ ] Create action buttons (Stop Recording, Clear)

- [ ] SCREEN 6: Expanded Editing (After Recording)
  - [ ] Create status bar with review badge
  - [ ] Implement editable text field with keyboard support
  - [ ] Add action buttons (Send Message, Re-record, Discard)
  - [ ] Implement send action with animation

## Phase 4: Feature Screens

- [ ] SCREEN 7: Voice Studio
  - [ ] Create header bar with music note icon
  - [ ] Implement visual EQ with animated bars
  - [ ] Add preset buttons (Normal, Bass, Chipmunk, etc.)
  - [ ] Create pitch slider
  - [ ] Add speed slider

- [ ] SCREEN 8: Image Creator
  - [ ] Create header bar with sparkles icon
  - [ ] Implement image display area (empty/loading/generated states)
  - [ ] Add text input field with generate button
  - [ ] Create quick suggestion chips

- [ ] SCREEN 9: History/Conversation List
  - [ ] Create header bar with search icon
  - [ ] Implement scrollable message list
  - [ ] Add empty state design
  - [ ] Create message item components with tap interaction

## Phase 5: Sub-Screens

- [ ] SUB-SCREEN A: Name Input Dialog
  - [ ] Create dialog container with glassmorphism
  - [ ] Implement title/subtitle text
  - [ ] Add Mr./Mrs. toggle buttons
  - [ ] Create text input field
  - [ ] Implement confirm button with save action

- [ ] SUB-SCREEN B: Speaking Visualizer (Overlay)
  - [ ] Create thinking state animation (rotating gradient)
  - [ ] Implement digital face with eyes and mouth
  - [ ] Add blink animation
  - [ ] Create emotion-based color changes
  - [ ] Implement stop button

- [ ] SUB-SCREEN C: Game Result Card (Overlay)
  - [ ] Create dialog container
  - [ ] Implement game over display with score
  - [ ] Add new high score badge (conditional)
  - [ ] Create close button

## Phase 6: Integration & Polish

- [ ] Connect all gesture handlers to corresponding screens
- [ ] Implement smooth transitions between screens
- [ ] Add consistent animations (150ms fast, 300ms normal, 500ms slow)
- [ ] Apply design tokens across all screens
- [ ] Test all interactions and haptic feedback
- [ ] Ensure responsive layout for different screen sizes
- [ ] Optimize performance for smooth gesture handling
