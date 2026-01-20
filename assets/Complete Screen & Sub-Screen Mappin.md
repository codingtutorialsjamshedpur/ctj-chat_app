Complete Screen & Sub-Screen Mapping for UI/UX Redesign
This document maps all screens from running_code.txt to the new gesture-based UI system in convert into this.txt, organized for sequential creation in Google Stitch.

🎯 DESIGN SYSTEM FOUNDATION
Global Design Tokens
Create First in Stitch:

yaml
Design System: "SHOURAV A.I. OS"
Theme: Nothing OS + Automotive + Voice-First

Colors:
  - Primary: Chrome/Soft Gold (#C0C0C0 / #FFD700)
  - Accent: Subtle Blue Glow (#4A90E2 with 20% opacity)
  - Background: Pure Black (#000000)
  - Surface: Translucent Glass (rgba(255,255,255,0.03))
  - Border: White 10% opacity with subtle glow
  - Text Primary: White (#FFFFFF)
  - Text Secondary: White 70% (#FFFFFFB3)

Typography:
  - Primary Font: SF Pro Display / Inter
  - Heading: 22px Bold
  - Body: 16px Regular
  - Caption: 12px Medium
  - Monospace: Courier (for timers)

Spacing:
  - Base Unit: 8px
  - Small: 12px
  - Medium: 16px
  - Large: 24px
  - XLarge: 32px

Shadows & Glows:
  - Soft Glow: 0 0 20px rgba(74,144,226,0.2)
  - Neon Glow: 0 0 30px currentColor at 30% opacity
  - Depth Shadow: 0 4px 16px rgba(0,0,0,0.4)

Animations:
  - Duration Fast: 150ms
  - Duration Normal: 300ms
  - Duration Slow: 500ms
  - Easing: cubic-bezier(0.4, 0.0, 0.2, 1)
  - Spring: Elastic bounce for cancellations
```

---

## 📱 SCREEN HIERARCHY & CREATION ORDER

### Phase 1: Core Screens (Create in Order 1-3)

---

## **SCREEN 1: HOME / VOICE CONTROL (Rest State)**
**File: `screen_1_home_rest.stitch`**

### Layout Structure
```
┌─────────────────────────────────────┐
│   [Weather]  [User Name]  [Icons]   │ ← AppBar (Translucent Glass)
├─────────────────────────────────────┤
│                                     │
│          [Pure Black BG]            │
│                                     │
│                                     │
│             ┌───────┐               │
│             │  REC  │ ← Center Control
│             │ CTRL  │   (Chrome Ring)
│             └───────┘               │
│                                     │
│         "SHOURAV A.I."              │ ← Engraved Text
│                                     │
│                                     │
└─────────────────────────────────────┘
```

### Design Specifications

#### AppBar (Glassmorphism)
- **Height:** 60px
- **Background:** `rgba(255,255,255,0.03)` with 10px blur
- **Border Bottom:** 1px solid `rgba(255,255,255,0.1)`
- **Layout:** Horizontal Row
  - **Left:** Weather Widget
    - Icon: Thermometer (12px, Cyan)
    - Text: "24°C" (10px, Cyan)
    - Spacing: 8px
    - Icon: Air Quality (12px, Green)
    - Text: "AQI: 50" (10px, Green)
  - **Center:** User Name
    - Text: Dynamic from `controller.userName.value`
    - Font: 16px Bold
    - Color: White
    - Tap: Opens name edit dialog
  - **Right:** Icon Row (spacing 12px)
    - Games (sports_esports)
    - Voice Studio (graphic_eq)
    - Image Creator (palette)
    - History (history)
    - Settings (settings_outlined)
    - Clear Chat (delete_outline)

#### REC Control (Center)
**Position:** Absolute center (row + column aligned)
**Size:** 160px diameter
**Structure:**
- **Outer Ring:**
  - Diameter: 160px
  - Border: 4px solid Chrome/Gold
  - Glow: `0 0 30px rgba(192,192,192,0.3)`
  - Metallic Gradient: `linear-gradient(135deg, #E8E8E8, #C0C0C0, #A8A8A8)`
- **Inner Circle:**
  - Diameter: 140px
  - Background: Pure Black
  - Text: "SHOURAV A.I."
    - Font: 14px Bold Engraved Style
    - Color: `rgba(255,255,255,0.6)`
    - Letter Spacing: 2px
    - Text Shadow: Inset depth effect
- **Idle State Animation:**
  - Subtle metallic sweep (rotating gradient 8s infinite)
  - No pulsing, no neon

#### Gesture Hints (Hidden by Default)
**Reveal on Touch:**
- **Position:** Radiating from REC center
- **Opacity:** 0 → 0.6 (fade in 150ms)
- **Directional Labels:**
  - **UP:** "CHANGE PERSONA" (60° arc, 180px from center)
  - **DOWN:** "SEND" (60° arc, 180px from center)
  - **LEFT:** "VOICE GAMES" (60° arc, 180px from center)
  - **RIGHT:** "SETTINGS" (60° arc, 180px from center)
- **Visual Style:**
  - Font: 12px Medium
  - Color: White 60%
  - Background: Glass pill shape
  - Border: White 10% glow

---

## **SCREEN 1A: DRAG UP (Change Persona)**
**File: `screen_1a_drag_up_persona.stitch`**

### Interaction Flow
```
User touches REC → Drags UP 40% → Preview activates
                 → Drags UP 70% → Commits to Persona Select
                 → Releases early → Spring-back to center
```

### Visual Feedback States

#### State 1: Touch Start (0-20% drag)
- REC moves 1:1 with finger
- Outer ring begins to glow cyan
- UP directional hint fades in
- Other directions fade out

#### State 2: Anticipatory Zone (20-60% drag)
- Upper arc illuminates progressively
- Arc: 120° span from -60° to +60° (top)
- Color: Gradient from White 10% → Cyan 40%
- Label "CHANGE PERSONA" scales up 1.0 → 1.2
- Resistance increases (ease-out curve)

#### State 3: Commit Zone (60-100% drag)
- Haptic feedback (heavy impact)
- Arc reaches full cyan glow
- REC locks to finger
- Background dims to 50%
- Transition begins

#### State 4: Release Before Commit
- Spring animation back to center
- Easing: Elastic bounce (500ms)
- Arc fades out
- Hints disappear

### Post-Commit Transition
**Animation:** Vertical slide up (300ms ease-out)
**Destination:** Persona Selection Screen (SCREEN 2)

---

## **SCREEN 1B: DRAG DOWN (Send/Confirm)**
**File: `screen_1b_drag_down_send.stitch`**

### Interaction Flow
```
User touches REC → Drags DOWN 40% → Preview activates
                 → Drags DOWN 70% → Commits to Send
                 → Releases early → Spring-back to center
```

### Visual Feedback States

#### State 1: Touch Start (0-20% drag)
- REC moves 1:1 with finger
- Chrome ring begins compression effect
- DOWN hint fades in
- Other directions fade out

#### State 2: Anticipatory Zone (20-60% drag)
- Lower arc illuminates progressively
- Arc: 120° span from 120° to 240° (bottom)
- Color: Gradient from White 10% → Green 40%
- Label "SEND" scales up 1.0 → 1.2
- Visual compression: Ring tightens inward
- Resistance increases

#### State 3: Commit Zone (60-100% drag)
- Haptic feedback (success pattern)
- Arc reaches full green glow
- Ring fully compressed
- Checkmark icon appears inside REC
- Background dims to 50%

#### State 4: Release Before Commit
- Spring animation back to center
- Ring expands back to original size
- Arc fades out

### Post-Commit Action
**Trigger:** `controller.sendText()`
**Visual:** Loading indicator inside REC
**Animation:** Pulsing green glow while processing

---

## **SCREEN 1C: DRAG LEFT (Interactive Voice Games)**
**File: `screen_1c_drag_left_games.stitch`**

### Interaction Flow
```
User touches REC → Drags LEFT 40% → Preview activates
                 → Drags LEFT 70% → Commits to Games
                 → Releases early → Spring-back to center
```

### Visual Feedback States

#### State 1: Touch Start (0-20% drag)
- REC moves 1:1 with finger (horizontal only)
- Left arc begins to glow
- LEFT hint fades in
- Playful game glyphs start appearing

#### State 2: Anticipatory Zone (20-60% drag)
- Left arc illuminates progressively
- Arc: 120° span from 150° to 210° (left side)
- Color: Gradient from White 10% → Purple 40%
- Game icons animate in along arc:
  - 🎮 Controller icon
  - 🎲 Dice icon
  - 🎤 Microphone icon
  - ⭐ Star icon
- Label "VOICE GAMES" scales up
- Resistance increases near commit

#### State 3: Commit Zone (60-100% drag)
- Haptic feedback (playful pattern)
- Arc reaches full purple glow
- Game icons pulse
- Background dims
- Transition leftward

#### State 4: Release Before Commit
- Spring animation back to center
- Game icons fade out
- Arc disappears

### Post-Commit Transition
**Animation:** Slide left (300ms ease-out)
**Destination:** Voice Games Hub (SCREEN 3)

---

## **SCREEN 1D: DRAG RIGHT (Settings)**
**File: `screen_1d_drag_right_settings.stitch`**

### Interaction Flow
```
User touches REC → Drags RIGHT 40% → Preview activates
                 → Drags RIGHT 70% → Commits to Settings
                 → Releases early → Spring-back to center
```

### Visual Feedback States

#### State 1: Touch Start (0-20% drag)
- REC moves 1:1 with finger
- Right arc begins to glow
- RIGHT hint fades in
- Gear outline appears

#### State 2: Anticipatory Zone (20-60% drag)
- Right arc illuminates progressively
- Arc: 120° span from -30° to 30° (right side)
- Color: Gradient from White 10% → Orange 40%
- Gear icon rotates slowly
- Label "SETTINGS" scales up
- Mechanical resistance feel

#### State 3: Commit Zone (60-100% drag)
- Haptic feedback (mechanical click)
- Arc reaches full orange glow
- Gear snaps to locked position
- Background dims
- Transition rightward

#### State 4: Release Before Commit
- Spring animation back to center
- Gear fades out
- Arc disappears

### Post-Commit Transition
**Animation:** Slide right (300ms ease-out)
**Destination:** Settings Screen (SCREEN 4)

---

## **SCREEN 2: PERSONA SELECTION**
**File: `screen_2_persona_select.stitch`**

### Layout Structure
```
┌─────────────────────────────────────┐
│  ← Back        PERSONA       [?]    │ ← Header
├─────────────────────────────────────┤
│                                     │
│   ┌─────────────────────────────┐   │
│   │  Standard Personas          │   │ ← Category 1
│   │  ┌───┐ ┌───┐ ┌───┐ ┌───┐   │   │
│   │  │ A │ │ B │ │ C │ │ D │   │   │
│   │  └───┘ └───┘ └───┘ └───┘   │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │  Gen-Z Personas             │   │ ← Category 2
│   │  ┌───┐ ┌───┐ ┌───┐ ┌───┐   │   │
│   │  │ E │ │ F │ │ G │ │ H │   │   │
│   │  └───┘ └───┘ └───┘ └───┘   │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │  Fun/Animal Personas        │   │ ← Category 3
│   │  ┌───┐ ┌───┐ ┌───┐ ┌───┐   │   │
│   │  │ I │ │ J │ │ K │ │ L │   │   │
│   │  └───┘ └───┘ └───┘ └───┘   │   │
│   └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘
```

### Design Specifications

#### Header Bar
- **Height:** 60px
- **Background:** Glass with blur
- **Left:** Back arrow (mechanical slide-out animation)
- **Center:** "PERSONA" title (22px Bold)
- **Right:** Info icon (opens persona explanation)

#### Category Cards
**Each Category Container:**
- **Background:** `rgba(255,255,255,0.03)`
- **Border:** 1px solid `rgba(255,255,255,0.1)`
- **Border Radius:** 16px
- **Padding:** 16px
- **Margin:** 12px horizontal, 8px vertical

**Category Header:**
- **Text:** Category name (14px Bold)
- **Color:** White 70%
- **Margin Bottom:** 12px

#### Persona Cards
**Each Persona Card:**
- **Size:** 80px × 100px
- **Background:** Glass with subtle gradient
- **Border:** 2px solid White 10%
- **Border Radius:** 12px
- **Hover State:** Border glows cyan, scale 1.05
- **Selected State:** Border glows gold, checkmark overlay

**Card Content:**
- **Icon:** 32px (persona-specific icon)
- **Label:** 12px Medium
- **Description:** 10px (on hover tooltip)

**Persona Card Layout:**
```
┌──────────┐
│   Icon   │ ← 32px Icon (top 20px)
│          │
│  Label   │ ← 12px Text (bottom 16px)
└──────────┘
```

#### Standard Personas (Category 1)
1. **Straight Forward**
   - Icon: Arrow pointing right
   - Color: White
2. **Jolly and Elaborate**
   - Icon: Smiling face
   - Color: Yellow
3. **Brief (One/Two Lines)**
   - Icon: Minimalist lines
   - Color: Cyan
4. **Non-Diplomatic Short**
   - Icon: Lightning bolt
   - Color: Orange
5. **Non-Diplomatic Descriptive**
   - Icon: Fire
   - Color: Red

#### Gen-Z Personas (Category 2)
1. **Slay Queen**
   - Icon: Crown
   - Color: Pink
2. **No Cap Casual**
   - Icon: Baseball cap
   - Color: Purple
3. **Bestie Mode**
   - Icon: Heart hands
   - Color: Rose
4. **Main Character**
   - Icon: Star burst
   - Color: Gold

#### Fun/Animal Personas (Category 3)
1. **Toddler**
   - Icon: Baby face
   - Color: Pastel Blue
2. **Dog**
   - Icon: Dog face
   - Color: Brown
3. **Cat**
   - Icon: Cat face
   - Color: Gray
4. **Lion**
   - Icon: Lion mane
   - Color: Gold
5. **Monkey**
   - Icon: Monkey face
   - Color: Orange
6. **Donkey**
   - Icon: Donkey face
   - Color: Gray
7. **Pig**
   - Icon: Pig snout
   - Color: Pink

#### Professional Personas (Category 4)
1. **Coach Mode**
   - Icon: Whistle
   - Color: Green
2. **Therapist Mode**
   - Icon: Heart with pulse
   - Color: Blue
3. **Teacher Mode**
   - Icon: Graduation cap
   - Color: Purple

### Interaction Behavior
**Tap Persona Card:**
- Scale animation: 1.0 → 0.95 → 1.05
- Haptic feedback
- Border glows
- Confirmation: Check icon animates in
- Wait 500ms
- Auto-navigate back to SCREEN 1

**Visual Confirmation:**
- Selected card gets persistent gold glow
- Other cards dim to 50% opacity
- Success sound plays

---

## **SCREEN 3: VOICE GAMES HUB**
**File: `screen_3_voice_games_hub.stitch`**

### Layout Structure
```
┌─────────────────────────────────────┐
│  ← Back      VOICE GAMES       🏆   │ ← Header
├─────────────────────────────────────┤
│                                     │
│   ┌─────────────────────────────┐   │
│   │ Active Game Indicator       │   │ ← IF game running
│   │ "Playing: Trivia Challenge" │   │
│   │ "Score: 150"                │   │
│   │ [END GAME]                  │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │  Difficulty Selector         │   │
│   │  [Easy] [Medium] [Hard]     │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌────────┬────────┬────────┐     │
│   │ Game 1 │ Game 2 │ Game 3 │     │ ← Game Grid (2 columns)
│   ├────────┼────────┼────────┤     │
│   │ Game 4 │ Game 5 │ Game 6 │     │
│   ├────────┼────────┼────────┤     │
│   │ Game 7 │        │        │     │
│   └────────┴────────┴────────┘     │
│                                     │
└─────────────────────────────────────┘
```

### Design Specifications

#### Header Bar
- **Height:** 60px
- **Background:** Glass with blur
- **Left:** Back arrow
- **Center:** "VOICE GAMES" (22px Bold)
- **Right:** Trophy icon (high scores)

#### Active Game Banner (Conditional)
**Display Only When:** `controller.activeGame.value != null`
**Background:** Green glow (`rgba(0,255,0,0.2)`)
**Border:** 2px solid Green
**Padding:** 16px
**Margin:** 12px
**Border Radius:** 12px

**Content:**
- **Row 1:** "Playing: [Game Name]" (14px Bold)
- **Row 2:** "Score: [Score]" (12px Medium)
- **Row 3:** "Time: [MM:SS]" (12px Mono, if timed)
- **Button:** "END GAME" (Red, 12px Bold)

#### Difficulty Selector
**Container:**
- **Height:** 48px
- **Margin:** 12px
- **Layout:** Horizontal row (center)

**Buttons:**
- **Size:** 80px × 36px
- **Border Radius:** 18px
- **Spacing:** 10px
- **States:**
  - **Unselected:** Glass background, White 30% border
  - **Selected:** Cyan glow, Cyan 100% border, scale 1.05

**Labels:** "Easy", "Medium", "Hard"

#### Game Grid
**Layout:** 2-column responsive grid
**Gap:** 12px
**Padding:** 12px horizontal

**Game Card Design:**
- **Size:** (Screen Width - 36px) / 2 per card
- **Aspect Ratio:** 0.85 (slightly taller)
- **Background:** Glass with subtle gradient
- **Border:** 2px solid White 10%
- **Border Radius:** 16px
- **Padding:** 12px

**Game Card Content:**
```
┌──────────────┐
│    Icon      │ ← 48px Icon (colored circle bg)
│              │
│  Game Name   │ ← 16px Bold
│              │
│ Description  │ ← 10px, 3 lines max, ellipsis
│              │
└──────────────┘
```

**Icon Circle:**
- **Size:** 56px diameter
- **Background:** Game color at 20% opacity
- **Icon:** 32px, game color at 100%
- **Margin:** Center, 12px from top

### Available Games

1. **20 Questions**
   - Icon: help_outline
   - Color: Purple (#9B59B6)
   - Description: "Think of something and I'll try to guess it in 20 questions!"

2. **Roast Battle**
   - Icon: local_fire_department
   - Color: Orange (#FF6F00)
   - Description: "Friendly roasting exchange - see who has the best comebacks!"

3. **Compliment Generator**
   - Icon: favorite
   - Color: Pink (#E91E63)
   - Description: "Get wholesome affirmations and boost your mood!"

4. **Story Time**
   - Icon: auto_stories
   - Color: Teal (#00BCD4)
   - Description: "Interactive storytelling where you choose the adventure!"

5. **Debate Mode**
   - Icon: gavel
   - Color: Blue (#2196F3)
   - Description: "I'll argue the opposite of whatever position you take!"

6. **Trivia Challenge**
   - Icon: quiz
   - Color: Green (#4CAF50)
   - Description: "Test your knowledge with fun trivia questions!"

7. **Astro Talk**
   - Icon: stars
   - Color: Amber (#FFC107)
   - Description: "Discover astrological insights using Vedic Astrology, Numerology, Tarot & more!"

### Interaction Behavior
**Tap Game Card:**
- Scale animation: 1.0 → 0.95 → 1.1
- Haptic feedback (game start pattern)
- Card glows in game color
- Sound: Game start sequence
  - Play "get_ready" sound
  - Wait 2s
  - Play "go" sound
- Navigate back to SCREEN 1
- Start game logic

---

## **SCREEN 4: SETTINGS**
**File: `screen_4_settings.stitch`**

### Layout Structure
```
┌─────────────────────────────────────┐
│  ← Back       SETTINGS         ✓    │ ← Header
├─────────────────────────────────────┤
│                                     │
│   ┌─────────────────────────────┐   │
│   │ User Profile                │   │
│   │ ┌────┐  Name: Shourav       │   │
│   │ │ SP │  Title: Mr.          │   │
│   │ └────┘  [Edit]              │   │
│   └─────────────────────────────┘   │
│                                     │
│   Sound Effects          [Toggle]   │
│   Image Generation       [Toggle]   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ AI Model                    │   │
│   │ ▼ Gemini 1.5 Flash          │   │
│   └─────────────────────────────┘   │
│                                     │
│   Voice Speed                       │
│   [0.75x] [1.0x] [1.2x] [1.5x]     │
│                                     │
│   Voice Pitch (Bass)                │
│   [━━━━━━○━━━] 0.9                 │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ Select Voice                │   │
│   │ ▼ Hinglish — Female         │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ Select Persona              │   │
│   │ ▼ Straight Forward          │   │
│   └─────────────────────────────┘   │
│                                     │
│   ───────────────────────────────   │
│                                     │
│   ABOUT                             │
│   [ALPHA v1.0.0]                   │
│   Developer: SHOURAV (CTJ TEAM)     │
│   Launch: January 2026              │
│   City: Jamshedpur                  │
│   Website: codingtutorialsjam...    │
│                                     │
└─────────────────────────────────────┘
Design Specifications
Header Bar
Height: 60px
Background: Glass with blur
Left: Back arrow
Center: "SETTINGS" (22px Bold)
Right: Checkmark icon (auto-save indicator)
User Profile Card
Container:

Background: Glass with gradient
Border: 2px solid White 10%
Border Radius: 16px
Padding: 16px
Margin: 12px
Layout:

Left: Avatar (48px circle)
Background: Gradient (Cyan → Purple)
Text: Initials (20px Bold, White)
Right: User Info (Column)
Name: 16px Bold
Title: 14px Medium, White 70%
Edit Button: 12px, Cyan
Tap Avatar or Edit:

Opens name input dialog
Toggle Switches
Design:

Track Width: 48px
Track Height: 28px
Track Border Radius: 14px
Thumb Size: 24px diameter
States:
Off: Track = White 10%, Thumb = White 30%
On: Track = Cyan 30%, Thumb = Cyan 100%
Animation: Slide + scale (300ms ease-out)
Items:

Sound Effects
Label: "Sound Effects" (16px)
Subtitle: "Enable immersive audio feedback" (12px, White 54%)
Image Generation
Label: "Image Generation" (16px)
Subtitle: "Generate images by voice or text" (12px, White 54%)
Dropdown Selectors
Design:

Height: 48px
Background: Glass with gradient
Border: 1px solid White 10%
Border Radius: 12px
Padding: 12px
Icon: Chevron down (right aligned)
Items:

AI Model
Options:
Gemini 1.5 Flash (Primary)
Gemini 1.5 Pro
Xiaomi Mimo V2 Flash (Free)
Qwen 2.5 Coder (Free)
Select Voice
Options:
English (US) — Male
English (US) — Female
Hinglish — Male
Hinglish — Female
Select Persona
Options: Same as SCREEN 2 personas
Tap Behavior:

Expand dropdown (slide down animation)
Dim background
Show options list
Tap option to select
Collapse dropdown
Voice Speed Selector
Design:

Label: "Voice Speed" (16px, White 70%)
Layout: Horizontal row (center aligned)
Spacing: 8px between buttons
Buttons:

Size: 64px × 32px
Border Radius: 16px
States:
Unselected: Glass background, White 10% border
Selected: Cyan background (30%), Cyan border, scale 1.1
Options: 0.75x, 1.0x, 1.2x, 1.5x, 2.0x

Voice Pitch Slider
Design:

Label Row:
Left: "Voice Pitch (Bass)" (16px, White 70%)
Right: Current value "0.9" (14px, Cyan)
Track:
Height: 4px
Background: White 10%
Active: Cyan gradient
Border Radius: 2px
Thumb:
Size: 20px diameter
Background: Cyan with glow
Border: 2px solid White
Range: 0.5 (Deep Bass) → 1.5 (High Pitch)
Markers:
0.5: "Deep"
1.0: "Normal"
1.5: "High"
About Section
Design:

Divider: 1px solid White 10% (margin 24px)
Heading: "ABOUT" (14px Bold, White 70%)
Spacing: 12px
Alpha Badge:

Container:
Background: Orange gradient
Border: 1.5px solid Orange (50%)
Border Radius: 15px
Padding: 6px 16px
Inline: Icon + Text
Icon: science_outlined (14px, White)
Text: "ALPHA v1.0.0" (11px Bold, White, Letter Spacing 0.8px)
Subtitle: "Testing & Feedback Phase" (10px, White 50%, italic)
Info Rows: Each row:

Icon: 20px (left aligned, Cyan)
Label: 12px (White 70%)
Value: 14px Medium (White)
Spacing: 12px vertical
Items:

code → Developer: SHOURAV (CTJ TEAM)
calendar_today → Launch: January 2026
location_city → City: Jamshedpur
language → Website: codingtutorialsjamshedpur.fun
SCREEN 5: EXPANDED RECORDING (While Listening)
File: screen_5_recording_expanded.stitch

Layout Structure
┌─────────────────────────────────────┐
│  [●] Recording...        [00:45]    │ ← Status Bar
├─────────────────────────────────────┤
│                                     │
│  [150 words • 890 chars]            │ ← Stats
│                                     │
│  ┌─────────────────────────────┐   │
│  │                             │   │
│  │   Transcribed text appears  │   │ ← Live Text (3/4 screen)
│  │   here in real-time...      │   │   Scrollable
│  │                             │   │
│
Continue

1:23 AM
│   User's speech is shown    │   │
│  │   as it's recognized        │   │
│  │                             │   │
│  │   |  ← Cursor               │   │
│  │                             │   │
│  └─────────────────────────────┘   │
│                                     │
│  [    STOP RECORDING    ] [Clear]   │ ← Actions
└─────────────────────────────────────┘


### Design Specifications

#### Status Bar
**Container:**
- **Height:** 48px
- **Background:** Glass with red tint (`rgba(255,0,0,0.1)`)
- **Border Bottom:** 2px solid Red

**Left Side:**
- **Indicator:** Pulsing red dot (14px, 1s pulse)
- **Label:** "Recording in Progress..." (14px Bold, Red)
- **Spacing:** 12px

**Right Side:**
- **Timer Container:**
  - Background: Red 30% gradient
  - Border: 2px solid Red
  - Border Radius: 12px
  - Padding: 8px 14px
  - Box Shadow: Red glow
- **Timer Display:**
  - Format: "MM:SS" (20px Bold, Red, Monospace)
  - Subtitle: "⏱ Recording" (11px, Red 70%)

#### Stats Bar
**Container:**
- **Height:** 32px
- **Background:** Cyan 10%
- **Border:** 1px solid Cyan 30%
- **Border Radius:** 8px
- **Padding:** 4px 10px
- **Margin:** 12px

**Content:**
- **Text:** "[Word Count] words • [Char Count] chars"
- **Font:** 11px Medium
- **Color:** Cyan 80%

#### Live Transcription Area
**Container:**
- **Height:** `0.65 * Screen Height`
- **Min Height:** 120px
- **Background:** White 3%
- **Border:** 2px solid Cyan 40%
- **Border Radius:** 14px
- **Box Shadow:** Cyan glow (10px blur)
- **Padding:** 14px
- **Margin:** 12px

**Text Display:**
- **Font:** 16px Regular
- **Line Height:** 1.6
- **Color:** White
- **Scroll:** Vertical, smooth physics

**Cursor:**
- **Character:** "|"
- **Font:** 20px Bold
- **Color:** Cyan 60%
- **Animation:** Blink (500ms)

**Empty State:**
- **Text:** "Listening for your voice...\n\n💬 Speak clearly and naturally"
- **Font:** 16px Regular
- **Color:** White 40%

#### Action Buttons
**Container:**
- **Height:** 60px
- **Margin:** 12px
- **Layout:** Horizontal row
- **Gap:** 12px

**Stop Recording Button (Primary):**
- **Flex:** 2
- **Height:** 48px
- **Background:** Red
- **Border Radius:** 12px
- **Elevation:** 4
- **Icon:** stop_circle (White, 20px)
- **Label:** "Stop Recording" (14px Bold, White)
- **Tap:** Scale 0.95 → 1.0, haptic, stop listening

**Clear Button (Secondary):**
- **Flex:** 1
- **Height:** 48px
- **Background:** Transparent
- **Border:** 1.5px solid Orange
- **Border Radius:** 12px
- **Icon:** refresh (Orange, 20px)
- **Label:** "Clear" (12px Bold, Orange)
- **Tap:** Clear text, restart listening

---

## **SCREEN 6: EXPANDED EDITING (After Recording)**
**File: `screen_6_editing_expanded.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│  ✓ Review & Edit      [150 words]   │ ← Status Bar
├─────────────────────────────────────┤
│                                     │
│  ┌─────────────────────────────┐   │
│  │                             │   │
│  │   Editable text field       │   │ ← Editable Area (3/4 screen)
│  │   User can modify before    │   │   Scrollable + Keyboard
│  │   sending...                │   │
│  │                             │   │
│  │   Tap to edit cursor here   │   │
│  │                             │   │
│  │                             │   │
│  └─────────────────────────────┘   │
│                                     │
│  [      SEND MESSAGE       ]        │ ← Primary
│  [  Re-record  ] [  Discard  ]      │ ← Secondary
└─────────────────────────────────────┘


### Design Specifications

#### Status Bar
**Container:**
- **Height:** 48px
- **Background:** Green 20%
- **Border Bottom:** 2px solid Green

**Left Side:**
- **Badge:**
  - Background: Green 20%
  - Border: 1.5px solid Green
  - Border Radius: 12px
  - Padding: 6px 12px
  - Box Shadow: Green glow
- **Icon:** check_circle (Green, 14px)
- **Label:** "Review & Edit" (12px Bold, Green)

**Right Side:**
- **Stats:** "[Word Count] words • [Char Count] chars"
- **Font:** 11px Medium
- **Color:** Cyan 70%

#### Editable Text Area
**Container:**
- **Height:** `0.65 * Screen Height`
- **Min Height:** 120px
- **Background:** White 3%
- **Border:** 2px solid Cyan 40%
- **Border Radius:** 14px
- **Box Shadow:** Cyan glow
- **Padding:** 14px
- **Margin:** 12px

**TextField:**
- **Font:** 16px Regular
- **Line Height:** 1.6
- **Color:** White
- **Max Lines:** null (unlimited)
- **Scroll Physics:** Bouncing
- **Cursor Color:** Cyan
- **Cursor Width:** 2px
- **Placeholder:**
  - Text: "Edit your text here...\n\n💡 You can modify the text before sending."
  - Color: White 30%
  - Font: 15px

#### Action Buttons

**Send Message Button (Primary):**
- **Width:** Full (100%)
- **Height:** 48px
- **Background:** Cyan 30%
- **Border Radius:** 12px
- **Elevation:** 4
- **Icon:** send_rounded (White, 20px)
- **Label:** "Send Message" (14px Bold, White)
- **Tap:**
  - Scale animation
  - Haptic feedback
  - Trigger send
  - Close expanded view

**Secondary Actions Row:**
- **Layout:** Horizontal row
- **Gap:** 12px
- **Margin Top:** 12px

**Re-record Button:**
- **Flex:** 1
- **Height:** 44px
- **Background:** Transparent
- **Border:** 1.5px solid Orange
- **Border Radius:** 12px
- **Icon:** mic (Orange, 20px)
- **Label:** "Re-record" (12px Bold, Orange)
- **Tap:**
  - Clear text
  - Close editing view
  - Restart listening

**Discard Button:**
- **Flex:** 1
- **Height:** 44px
- **Background:** Transparent
- **Border:** 1.5px solid Red
- **Border Radius:** 12px
- **Icon:** close (Red, 20px)
- **Label:** "Discard" (12px Bold, Red)
- **Tap:**
  - Clear text
  - Close editing view
  - Return to home

---

## **SCREEN 7: VOICE STUDIO**
**File: `screen_7_voice_studio.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│  ← Back    VOICE STUDIO        🎵    │ ← Header
├─────────────────────────────────────┤
│                                     │
│   Customize your AI's voice         │
│   signature                         │
│                                     │
│   ┌─────────────────────────────┐   │
│   │  ▂▄▅▇█▇▅▄▂                  │   │ ← Visual EQ (Simulated)
│   └─────────────────────────────┘   │
│                                     │
│   Presets                           │
│   [Normal] [Bass] [Chip] [Slow]    │
│                                     │
│   Pitch                    1.0      │
│   [━━━━━○━━━━]                     │
│                                     │
│   Speed                    1.0x     │
│   [━━━━━○━━━━]                     │
│                                     │
└─────────────────────────────────────┘


### Design Specifications

#### Header Bar
- **Height:** 60px
- **Background:** Glass with blur
- **Left:** Back arrow
- **Center:** "VOICE STUDIO" (22px Bold)
- **Right:** Music note icon (play test voice)

#### Subtitle
- **Text:** "Customize your AI's voice signature"
- **Font:** 12px Regular
- **Color:** White 70%
- **Margin:** 12px horizontal, 20px top

#### Visual EQ (Simulated)
**Container:**
- **Height:** 60px
- **Background:** Transparent
- **Margin:** 20px
- **Layout:** Row (10 bars)
- **Gap:** 8px

**Each Bar:**
- **Width:** 20px
- **Height:** Random 30-60px
- **Background:** Cyan gradient (opacity 0.5 + index * 0.05)
- **Border Radius:** 4px
- **Animation:** Random pulse (1-2s repeat)

#### Presets Section
**Label:**
- **Text:** "Presets"
- **Font:** 14px Medium
- **Color:** White 70%
- **Margin:** 20px top

**Preset Buttons:**
- **Layout:** Horizontal scrollable row
- **Spacing:** 10px
- **Margin:** 10px top

**Each Preset:**
- **Size:** 80px × 36px
- **Background:** Glass
- **Border:** 1px solid White 20%
- **Border Radius:** 20px
- **Label:** 14px Medium, White
- **States:**
  - **Unselected:** Default
  - **Selected:** Cyan background (20%), Cyan border, scale 1.05

**Presets:**
1. **Normal:** Pitch 1.0, Speed 1.0
2. **Bass Boost:** Pitch 0.7, Speed 0.9
3. **Chipmunk:** Pitch 1.4, Speed 1.2
4. **Slow Motion:** Pitch 0.8, Speed 0.5
5. **Hyper:** Pitch 1.2, Speed 1.5

#### Sliders
**Common Design:**
- **Label Row:**
  - Left: Parameter name (16px, White)
  - Right: Current value (14px, Cyan)
- **Track:**
  - Height: 4px
  - Background: White 10%
  - Active: Cyan gradient
  - Border Radius: 2px
- **Thumb:**
  - Size: 20px diameter
  - Background: Cyan with glow
  - Border: 2px solid White

**Pitch Slider:**
- **Range:** 0.5 → 2.0
- **Step:** 0.1
- **Default:** 1.0

**Speed Slider:**
- **Range:** 0.5 → 2.0
- **Step:** 0.1
- **Default:** 1.0
- **Label Suffix:** "x"

---

## **SCREEN 8: IMAGE CREATOR**
**File: `screen_8_image_creator.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│  ← Back   IMAGE CREATOR       ✨    │ ← Header
├─────────────────────────────────────┤
│                                     │
│   Describe what you want to see     │
│   Example: 'A sunset over mtns'     │
│                                     │
│   ┌─────────────────────────────┐   │
│   │                             │   │
│   │    [Generated Image]        │   │ ← Image Display (Expandable)
│   │    or                       │   │   3/4 of screen
│   │    [Empty State Icon]       │   │
│   │                             │   │
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ What would you like to      │   │ ← Text Input
│   │ create?                     │   │
│   └─────────────────────────────┘   │
│   [✨]                               │ ← Generate Button
│                                     │
│   Quick Ideas:                      │
│   [Sunset] [Forest] [Abstract]     │
│                                     │
└─────────────────────────────────────┘


### Design Specifications

#### Header Bar
- **Height:** 60px
- **Background:** Glass with blur
- **Left:** Back arrow
- **Center:** "IMAGE CREATOR 🎨" (22px Bold)
- **Right:** Sparkles icon (inspiration)

#### Subtitle
- **Text:** "Describe what you want to see. Example: 'A sunset over mountains'"
- **Font:** 12px Regular
- **Color:** White 70%
- **Margin:** 12px horizontal, 20px top

#### Image Display Area
**Container:**
- **Height:** `0.5 * Screen Height`
- **Background:** Transparent
- **Border:** 1px solid White 24%
- **Border Radius:** 12px
- **Margin:** 12px

**Empty State:**
- **Icon:** image_not_supported_outlined (60px, White 54%)
- **Label:** "Enter a description and generate"
- **Font:** 14px Medium
- **Color:** White 54%
- **Center aligned**

**Loading State:**
- **Background:** Glass with pulse
- **Spinner:** Circular progress (Cyan)
- **Label:** "Creating your image..." (14px, White)
- **Sublabel:** "(This may take 30-45 seconds)" (12px, White 54%)

**Generated Image State:**
- **Image:** Fit cover, border radius 12px
- **Border:** Cyan glow (2px)
- **Tap:** Full screen preview

**Error State:**
- **Icon:** error_outline (60px, Red)
- **Label:** "Could not load image"
- **Font:** 14px Medium
- **Color:** White 54%

#### Text Input Area
**Container:**
- **Margin:** 12px
- **Layout:** Row

**TextField:**
- **Flex:** 1
- **Height:** 48px
- **Min Lines:** 1
- **Max Lines:** 2
- **Background:** Glass
- **Border:** 1px solid White 24%
- **Focus Border:** Cyan
- **Border Radius:** 12px
- **Padding:** 12px
- **Font:** 16px Regular
- **Color:** White
- **Placeholder:** "What would you like to create?"
- **Placeholder Color:** White 50%

**Generate Button:**
- **Size:** 48px × 48px
- **Background:** Cyan
- **Border Radius:** 12px
- **Icon:** auto_awesome (Black, 28px)
- **Margin Left:** 10px
- **States:**
  - **Idle:** Default
  - **Loading:** Spinner (20px, White)
  - **Disabled:** Gray 30%

#### Quick Suggestions
**Label:**
- **Text:** "Quick Ideas:"
- **Font:** 12px Medium
- **Color:** White 70%
- **Margin:** 20px top, 8px bottom

**Suggestion Chips:**
- **Layout:** Horizontal scrollable row
- **Spacing:** 10px

**Each Chip:**
- **Padding:** 8px 12px
- **Background:** Glass
- **Border:** 1px solid Cyan 30%
- **Border Radius:** 16px
- **Label:** 12px Medium, White 70%
- **Tap:** Fill input, auto-generate

**Suggestions:**
1. "Sunset over beach"
2. "Mystical forest"
3. "Abstract art"
4. "City lights"

---

## **SCREEN 9: HISTORY / CONVERSATION LIST**
**File: `screen_9_history.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│  ← Back   CONVERSATION HISTORY      │ ← Header
├─────────────────────────────────────┤
│                                     │
│   ┌─────────────────────────────┐   │
│   │ USER: Hello, how are you?   │   │ ← Message 1
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ ASSISTANT: I'm doing well!  │   │ ← Message 2
│   └─────────────────────────────┘   │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ USER: What's the weather?   │   │ ← Message 3
│   └─────────────────────────────┘   │
│                                     │
│   ... (scrollable list)             │
│                                     │
└─────────────────────────────────────┘


### Design Specifications

#### Header Bar
- **Height:** 60px
- **Background:** Glass with blur
- **Left:** Back arrow
- **Center:** "CONVERSATION HISTORY" (22px Bold)
- **Right:** Search icon (future feature)

#### Message List
**Container:**
- **Padding:** 16px
- **Background:** Transparent
- **Scroll:** Vertical, physics bouncing

**Empty State:**
- **Icon:** history (60px, White 54%)
- **Label:** "No history yet"
- **Font:** 16px Medium
- **Color:** White 54%
- **Center aligned**

**Message Item:**
- **Margin:** 8px vertical
- **Background:** Glass
- **Border:** 1px solid White 10%
- **Border Radius:** 12px
- **Padding:** 12px

**Message Header:**
- **Text:** "USER" or "ASSISTANT"
- **Font:** 10px Bold
- **Color:**
  - USER: Cyan
  - ASSISTANT: Purple
- **Letter Spacing:** 1px

**Message Content:**
- **Text:** Message text
- **Font:** 14px Regular
- **Color:** White
- **Max Lines:** 3
- **Ellipsis:** Overflow

**Tap Message:**
- Scale animation
- Navigate to full chat view (SCREEN 1)
- Scroll to message

---

## **SUB-SCREEN A: NAME INPUT DIALOG**
**File: `subscr_a_name_input.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│                                     │
│   ┌─────────────────────────────┐   │
│   │      Welcome                │   │ ← Dialog
│   │                             │   │
│   │  How should I address you?  │   │
│   │                             │   │
│   │  [Mr.] [Mrs.]               │   │ ← Title Toggle
│   │                             │   │
│   │  ┌───────────────────────┐  │   │
│   │  │ Your Name             │  │   │ ← Text Input
│   │  └───────────────────────┘  │   │
│   │                             │   │
│   │        [Confirm]            │   │ ← Action
│   └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘


### Design Specifications

**Dialog Container:**
- **Width:** 90% of screen
- **Background:** Black 87% with blur
- **Border:** 1px solid White 10%
- **Border Radius:** 16px
- **Padding:** 20px
- **Shadow:** Large depth shadow

**Title:**
- **Text:** "Welcome"
- **Font:** 20px Bold
- **Color:** White
- **Align:** Center

**Subtitle:**
- **Text:** "How should I address you?"
- **Font:** 14px Regular
- **Color:** White 70%
- **Align:** Center
- **Margin:** 15px top

**Title Toggle:**
- **Layout:** Horizontal row (center)
- **Gap:** 0
- **Margin:** 15px vertical

**Mr. Button:**
- **Padding:** 10px 20px
- **Background:** Selected ? Cyan 30% : White 10%
- **Border:** Selected ? Cyan : White 24%
- **Border Radius:** Left 20px
- **Label:** "Mr." (14px Bold)
- **Color:** Selected ? Cyan : White 70%

**Mrs. Button:**
- **Padding:** 10px 20px
- **Background:** Selected ? Pink 30% : White 10%
- **Border:** Selected ? Pink : White 24%
- **Border Radius:** Right 20px
- **Label:** "Mrs." (14px Bold)
- **Color:** Selected ? Pink : White 70%

**Text Input:**
- **Height:** 48px
- **Background:** Transparent
- **Border Bottom:** 1px solid Cyan
- **Padding:** 12px 0
- **Font:** 16px Regular
- **Color:** White
- **Placeholder:** "Your Name"
- **Placeholder Color:** White 38%

**Confirm Button:**
- **Width:** Full
- **Height:** 44px
- **Background:** Cyan
- **Border Radius:** 12px
- **Label:** "Confirm" (14px Bold, White)
- **Margin:** 20px top
- **Tap:** Save name, close dialog

---

## **SUB-SCREEN B: SPEAKING VISUALIZER (Overlay)**
**File: `subscr_b_speaking_viz.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│                                     │
│          [Visualization]            │ ← Animated Face (Center)
│                                     │
│          [STOP Button]              │ ← Control (Below)
│                                     │
└─────────────────────────────────────┘


### Design Specifications

#### Container
- **Position:** Overlay on SCREEN 1
- **Height:** Auto (220px when visible)
- **Background:** Transparent
- **Align:** Top center
- **Margin Top:** 80px (below AppBar)

#### Thinking State (Loading)
**Animation:**
- **Type:** Rotating gradient sweep
- **Duration:** 2s infinite
- **Size:** 80px diameter circle
- **Colors:** Cyan 0%, Cyan 50%, Cyan 100% (sweep)
- **Inner Circle:** Black 26%, 76px diameter
- **Icon:** auto_awesome (32px, Cyan, center)

#### Speaking/Idle State (Digital Face)
**Canvas Size:** 120px × 120px
**Animation:** Custom painter

**Eyes (2):**
- **Shape:** Oval
- **Width:** 15% of canvas (18px)
- **Height:** 15% of canvas × blinkOpen (18px → 0px)
- **Color:** Dynamic based on emotion
- **Position:**
  - Left Eye: 30% from left, 35% from top
  - Right Eye: 70% from left, 35% from top
- **Glow:** When blinkOpen > 0.5, outer glow (4px spread)

**Mouth:**
- **Shape:** Rounded rectangle
- **Width:** 40% of canvas (48px)
- **Height:** 4px (idle) → 30px (speaking, animated)
- **Position:** Center, 70% from top
- **Color:** Dynamic based on emotion
- **Animation:** Height oscillates 0.0 → 1.0 (300ms, emotion speed adjusted)
- **Glow:** When speaking, outer glow

**Blink Animation:**
- **Frequency:** Random 1000-4000ms
- **Duration:** 200ms (close + open)

**Emotion Colors:**
- happy: Yellow (#FFEB3B)
- sad: Blue Grey (#607D8B)
- excited: Purple (#9C27B0)
- angry: Red (#F44336)
- calm: Teal (#009688)
- neutral: Cyan (#00BCD4)

#### Stop Button (When Speaking)
**Container:**
- **Padding:** 4px 12px
- **Background:** Red 80%
- **Border Radius:** 20px
- **Margin Top:** 5px

**Label:**
- **Text:** "STOP"
- **Font:** 12px Bold
- **Color:** White

**Tap:** Stop TTS playback

---

## **SUB-SCREEN C: GAME RESULT CARD (Overlay)**
**File: `subscr_c_game_result.stitch`**

### Layout Structure
┌─────────────────────────────────────┐
│                                     │
│   ┌─────────────────────────────┐   │
│   │     🎮 GAME OVER            │   │
│   │                             │   │
│   │     Final Score: 250        │   │
│   │                             │   │
│   │     Great game session!     │   │
│   │     You scored 250 points!  │   │
│   │                             │   │
│   │     [NEW HIGH SCORE! 🏆]    │   │ ← If applicable
│   │                             │   │
│   │     [Close]                 │   │
│   └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘


### Design Specifications

**Dialog Container:**
- **Width:** 85% of screen
- **Background:** Black 90% with blur
- **Border:** 2px solid Gold (if high score) or Cyan
- **Border Radius:** 20px
- **Padding:** 24px
- **Shadow:** Large depth shadow with color glow

**Icon:**
- **Size:** 48px
- **Color:** Gold (high score) or Cyan
- **Align:** Center

**Title:**
- **Text:** "GAME OVER"
- **Font:** 24px Bold
- **Color:** White
- **Align:** Center

**Score Display:**
- **Text:** "Final Score: [Score]"
- **Font:** 20px Bold
- **Color:** Gold (high score) or Cyan
- **Align:** Center
- **Margin:** 16px vertical

**Summary Text:**
- **Text:** Dynamic summary from game
- **Font:** 14px Regular
- **Color:** White 90%
- **Align:** Center
- **Max Lines:** 5

**High Score Badge (Conditional):**
- **Background:** Gold gradient
- **Border:** 2px solid Orange 50%
- **Border Radius:** 20px
- **Padding:** 8px 16px
- **Margin:** 12px vertical
- **Label:** "🏆 NEW HIGH SCORE!"
- **Font:** 12px Bold, White

**Close Button:**
- **Width:** Full
- **Height:** 44px
- **Background:** Cyan 30%
- **Border Radius:** 12px
- **Label:** "Close" (14px Bold, White)
- **Margin:** 20px top

---

## 🎬 ANIMATION SPECIFICATIONS

### Global Animation Library
**Create as reusable components:**

#### 1. Spring Back Animation
```yaml
Type: Physics-based spring
Duration: 500ms
Damping: 0.7
Stiffness: 300
Usage: Cancel gestures, return to center
```

#### 2. Commit Haptic Pattern
```yaml
Type: Heavy impact
Duration: 50ms
Delay: 0ms
Usage: Threshold crossing
```

#### 3. Glow Pulse
```yaml
Type: Opacity + Scale
Duration: 1500ms
Loop: Infinite reverse
Opacity: 0.3 → 1.0
Scale: 1.0 → 1.1
Usage: Active states, loading
```

#### 4. Slide Transition
```yaml
Type: Position offset
Duration: 300ms
Easing: Ease-out cubic
Usage: Screen transitions
```

#### 5. Scale Press
```yaml
Type: Scale transform
Duration: 150ms
Scale: 1.0 → 0.95 → 1.05
Usage: Button taps
```

---

## 📊 GESTURE DETECTION PARAMETERS

### Drag Thresholds
```yaml
Touch Start Sensitivity: 10px movement
Preview Zone: 20-60% of radius (approx 32-96px)
Commit Zone: 60-100% of radius (approx 96-160px)
Cancel Distance: Release before 60%
Direction Lock: After 15° deviation
Resistance Curve: Ease-out (accelerating difficulty)
```

### Physics Values
```yaml
Spring Constant: 300
Damping Ratio: 0.7
Mass: 1.0
Velocity Threshold: 200px/s (for inertia)
```

---

## 🎨 STITCH CREATION WORKFLOW

### Recommended Order:

1. **Phase 1: Foundation (Day 1)**
   - Design System tokens
   - SCREEN 1 (Home/Rest)
   - SUB-SCREEN B (Speaking Visualizer)

2. **Phase 2: Core Gestures (Day 2)**
   - SCREEN 1A (Drag Up)
   - SCREEN 1B (Drag Down)
   - SCREEN 1C (Drag Left)
   - SCREEN 1D (Drag Right)

3. **Phase 3: Destinations (Day 3)**
   - SCREEN 2 (Persona Select)
   - SCREEN 3 (Voice Games Hub)
   - SCREEN 4 (Settings)

4. **Phase 4: Advanced Features (Day 4)**
   - SCREEN 5 (Recording Expanded)
   - SCREEN 6 (Editing Expanded)
   - SCREEN 7 (Voice Studio)
   - SCREEN 8 (Image Creator)

5. **Phase 5: Polish (Day 5)**
   - SCREEN 9 (History)
   - SUB-SCREEN A (Name Dialog)
   - SUB-SCREEN C (Game Result)
   - Animation refinements

---

## 🔗 INTEGRATION NOTES FOR CLAUDE/GEMINI

Each Stitch screen export should include:

### Metadata Comments
```dart
/// SCREEN: screen_1_home_rest
/// MAPS TO: VoiceAssistantPage (Main Scaffold)
/// BUSINESS LOGIC:
/// - controller.startListening() on REC drag
/// - controller.sendText() on DOWN commit
/// - Navigate to PersonaScreen on UP commit
/// - Navigate to GamesScreen on LEFT commit
/// - Navigate to SettingsScreen on RIGHT commit
```

### Widget Replacement Points
```dart
// REPLACE: Static REC control
// WITH: Obx(() => GestureDetector(...))
// CONNECT: VoiceController gesture handlers

// REPLACE: Static AppBar weather
// WITH: Obx(() => WeatherController display)

// REPLACE: Mock speaking visualizer
// WITH: Obx(() => SpeakingVisualizer(emotion: controller.currentEmotion.value))
```

---

## ✅ VALIDATION CHECKLIST

Before generating each screen in Stitch:

- [ ] All dimensions use 8px base unit
- [ ] Colors match design tokens
- [ ] Fonts use SF Pro Display / Inter
- [ ] Shadows include color glow
- [ ] Borders have blur/transparency
- [ ] Animations use specified durations
- [ ] Touch targets minimum 44px
- [ ] Text contrast ratio > 4.5:1
- [ ] Glass effect uses backdrop blur
- [ ] Gesture thresholds documented
- [
Continue

1:26 AM
] Haptic feedback points marked

 Sound effect triggers noted
This complete mapping provides pixel-perfect specifications for every screen and sub-screen in the app, ready for sequential creation in Google Stitch. Each screen is self-contained with exact measurements, colors, interactions, and business logic connection points for final integration.






Claude is AI and can make mistakes. Please double-check responses.
