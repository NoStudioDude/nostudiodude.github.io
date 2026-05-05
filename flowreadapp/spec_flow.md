# FlowRead — Product & Technical Specification

> Version 1.1 | 2026-05-03 | Status: Draft for Approval

---

## Table of Contents

1. [Core Strategy & Requirements — The "Why" & "What"](#1-core-strategy--requirements)
2. [Design & User Experience — The "Look"](#2-design--user-experience)
3. [Technical & System Specs — The "How"](#3-technical--system-specs)
4. [Project Management & Legal](#4-project-management--legal)

---

## 1. Core Strategy & Requirements

### 1.1 The Problem

Millions of people want to read more but struggle to maintain focus on a page. The most common failure mode is losing the reading line — the eye drifts, the mind wanders, and the reader wastes energy searching for where they left off. This is especially pronounced for people with ADHD, dyslexia, or high-stimulation environments.

Existing e-reading apps compound the problem: they show too much text at once, surround it with toolbars, tabs, progress bars, and settings icons. Every visible UI element is a potential distraction that pulls the reader's attention away from the words.

### 1.2 The Solution

FlowRead is a **gesture-first focus reader** built around one principle: *the only thing on screen is the word you are reading right now.*

It is inspired by RSVP (Rapid Serial Visual Presentation) — a technique that presents words sequentially at a controlled speed, forcing the eye to stay in one place. By eliminating the need to scan a line, the reader can engage fully with the meaning rather than the mechanics of reading.

FlowRead brings RSVP to mobile with a fully touch-driven interface — no buttons, no toolbars, no chrome. Every action is a gesture.

### 1.3 Target Users

**Primary:** People with attention difficulties (ADHD, distractibility) who want to read more books but cannot maintain focus with traditional e-readers.

**Secondary:**
- People who frequently lose their reading line and waste time re-scanning
- Speed-reading enthusiasts who want to progressively push their WPM
- Anyone who values a distraction-free, minimal reading environment

### 1.4 Core Principles

| Principle | What it means in practice |
|---|---|
| **Text only** | Nothing competes with the current word for visual attention |
| **Gesture only** | Zero on-screen buttons during reading |
| **Speed is yours** | WPM is always under the reader's control, adjustable without stopping |
| **Never lose your place** | Context view and skim mode let readers orient instantly |
| **Minimalism is a feature** | Every UI element that does not exist cannot distract |

### 1.5 Feature Requirements

#### Reading Modes

| Mode | Description | Words shown |
|---|---|---|
| **RSVP — Large** | Single word fills the screen | 1 |
| **RSVP — Medium** | Three words shown, center word highlighted | 3 |
| **RSVP — Small** | Five words shown, center word highlighted | 5 |
| **Context / Skim View** | Triggered by swipe left; shows full paragraph context with current word highlighted | All surrounding lines |

#### Gesture Controls

| Gesture | Action |
|---|---|
| **Tap anywhere** | Start / pause reading |
| **Swipe up** | Increase reading speed (WPM) |
| **Swipe down** | Decrease reading speed (WPM) |
| **Swipe left** | Enter Context / Skim View |
| **Hold + drag (in Skim View)** | Scrub through words manually (left/right or up/down) |
| **Long press (paused)** | Open navigation menu |
| **Swipe right (in menu)** | Close menu / return to reader |

#### Speed Feedback

- When the user changes speed via swipe, the current WPM is briefly displayed below the text.
- The WPM indicator fades automatically after ~2–3 seconds.
- It also disappears immediately when reading resumes.
- During active reading, no WPM indicator is shown.

#### Context / Skim View

- Triggered by swiping left during reading (pauses playback).
- Displays the current line in full, with approximately 6–8 lines of text above and 2–3 lines below.
- The currently-focused word is highlighted using the same visual style as the RSVP anchor.
- The user can hold a finger and drag horizontally or vertically to scrub through the surrounding words manually.
- Releasing returns to the reader at the selected word position.

#### HUD (Heads-Up Display)

The following information is always present but rendered subtly so as not to compete with the text:

- **Bottom-left:** Current chapter title or number (e.g. "IV")
- **Bottom-right:** Book completion percentage (e.g. "25%")
- **Nowhere:** Phone battery, wifi status, time. The system status bar is always hidden while the app is in reading mode.

The HUD fades to near-invisible during active playback and becomes slightly more visible when paused.

#### Navigation Menu

The menu is accessed by a long press while reading is paused. It is a full-screen, minimal list with dark/light themed items. Navigation through menu items is done by swiping up/down. Activating a menu item is done by tapping it.

Menu structure:

```
RESUME
CHAPTERS
  └─ Chapter list (tap to jump)
LIBRARY
  └─ All imported books (tap to open)
SETTINGS
  └─ [see Settings section]
```

No hardware/device options (wifi, firmware updates) are included — those are specific to the reference hardware device and are not applicable to a mobile app.

#### Library & Import

- Users import books from their device's file system or cloud storage (iCloud / Google Drive).
- Supported input formats: **EPUB, TXT, Markdown (.md), HTML/XHTML**
- PDF support is deferred to v1.1 (text extraction on mobile is unreliable; quality matters more than breadth).
- Files are converted to the `.rsvp` internal format on first open (on-device, nothing uploaded).
- The library screen shows cover art (where available), title, author, and reading progress.

---

## 2. Design & User Experience

### 2.1 Visual Design Philosophy

FlowRead's visual design is derived directly from its core principle: *the word is everything.* Every design decision serves this goal.

- **Centered composition:** The reading anchor (the current word) is always in the same position on screen. The eye never moves.
- **High contrast:** Text has maximum contrast against its background at all times.
- **Zero decoration:** No borders, shadows, gradients, icons, or graphical elements during reading.
- **Typographic focus:** The only visual hierarchy is between the focused word and context words.

### 2.2 Themes

Three themes are available. All themes hide the system status bar.

| Theme | Background | Text | Highlight | Dim |
|---|---|---|---|---|
| **Dark** (default) | `#0a0f1e` (deep navy) | `#f0f4ff` | `#f5a623` (amber) | `#4a5568` |
| **Light** | `#fafaf7` (warm white) | `#1a1a2e` | `#d97706` (warm amber) | `#9ca3af` |
| **Night** | `#000000` (OLED black) | `#e0e0e0` | `#b8860b` (muted amber) | `#374151` |

**Accent color override:** The user can switch the highlight color from amber to red (`#e04040`) in Settings → Appearance → Accent Color. This overrides the theme's default highlight across all three themes.

Users switch themes from Settings. There is no in-reading theme toggle.

### 2.3 Typography

| Setting | Options |
|---|---|
| **Font family** | Default (system font, no explicit family set — `fontWeight` controls boldness), Atkinson Hyperlegible, Lexend |
| **Display mode** | Large (1 word), Medium (3 words), Small (5 words) |
| **Letter spacing** | Normal (`0`), Wide (`1.5`), Wider (`3.5`) — values in React Native `letterSpacing` units |
| **Word spacing** | Normal, Wide, Wider — Medium/Small modes only; controls slot padding |
| **Word highlight** | Word (full word in accent color) or Letter (ORP center letter only) |
| **Word anchor position** | Left-center, Center, Right-center |

**Bundled font variants:**

| Font | Weights bundled |
|---|---|
| Atkinson Hyperlegible | `AtkinsonHyperlegible_400Regular`, `AtkinsonHyperlegible_700Bold` |
| Lexend | `Lexend_400Regular`, `Lexend_700Bold` |

**Atkinson Hyperlegible** and **Lexend** are included to support readers with visual processing or reading difficulties. These are included as bundled assets under the SIL Open Font License 1.1.

### 2.4 The Reading Anchor

The focused word has a distinct visual treatment that differentiates it from any surrounding context:

- In **Large mode** (1 word): The word is large, centered, and uses the full typographic weight of the theme's highlight color. A vertical alignment marker (two short lines above and below) anchors the eye.
- In **Medium / Small mode** (3 or 5 words): The center word uses the highlight color and/or weight; flanking words are rendered in a dimmer, lower-contrast style.
- **Word Highlight setting** controls how the anchor is shown:
  - *Word* — the entire focused word is rendered in the accent color.
  - *Letter* — only the ORP (Optimal Recognition Point) center letter is in the accent color; the rest of the word renders in the base text color. This provides a fixed sub-word focal point and is the default.

### 2.5 Screen Layout During Reading

The app runs **exclusively in landscape (horizontal) orientation.** Portrait mode is not supported. The orientation is locked at the system level on app launch.

This matches the reference hardware form factor and provides the widest possible reading field for multi-word modes while keeping the screen height compact — concentrating all visual attention on a single vertical band.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │  ← Status bar hidden
│                                                                  │
│                        [CURRENT WORD]                            │  ← Vertically centered
│                                                                  │
│   [WPM: 320]                                                     │  ← Fades after ~2s
│ IV                                                          25%  │  ← HUD
└──────────────────────────────────────────────────────────────────┘
```

### 2.6 Context / Skim View Layout

```
┌──────────────────────────────────────────────────────────────────┐
│  "...and he knew it would not be easy to convince the old man.   │  ← ~6-8 lines above (dimmed)
│  He had tried before, more than once, and each time he had       │
│  walked away with nothing but a polite refusal. The morning      │
│  sun cast long shadows across the [floor] as he stepped          │  ← focused word highlighted
│  through the open door. She was already there, waiting."         │  ← ~2-3 lines below (dimmed)
└──────────────────────────────────────────────────────────────────┘
```

Landscape orientation means fewer lines are visible vertically but each line is much longer — showing more meaningful context per line, closer to natural reading width.

### 2.7 Menu Screen Layout

The menu is a full-screen overlay using the active theme. Menu items are listed vertically with generous spacing. The currently selected item is highlighted (same color as the word anchor). Navigation is swipe up/down; activation is tap.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   RESUME                                                         │  ← Highlighted (active)
│   CHAPTERS                                                       │
│   LIBRARY                                                        │
│   SETTINGS                                                       │
│                                                                  │
│                                                              87% │  ← Progress persists
└──────────────────────────────────────────────────────────────────┘
```

### 2.8 Settings Screen

Settings are grouped into sections, presented as a clean scrollable list within the same full-screen overlay style as the menu.

```
READING
  Display Mode          Large / Medium / Small
  Word Anchor Position  Left / Center / Right
  Word Highlight        Word / Letter
  Long Word Extension   On / Off
  Sentence Pause        On / Off

APPEARANCE
  Theme                 Dark / Light / Night
  Accent Color          Amber / Red
  Font                  Default / Atkinson / Lexend
  Letter Spacing        Normal / Wide / Wider
  Word Spacing          Normal / Wide / Wider

SPEED
  Default WPM           [cycles in steps of 50; tap to advance]

HELP
  Gesture Reference     [full-screen gesture reference card]
  Replay Tutorial       [resets onboarding_complete; relaunches onboarding]

DEV  (remove before App Store release)
  Reset App             [wipes all books, progress, and settings]
```

### 2.9 Onboarding & Tutorial

#### Philosophy

FlowRead has no visible buttons and every action is a gesture. For most users, this is completely unfamiliar. If they open the app and cannot figure out what to do in the first 10 seconds, they will close it and not come back.

The onboarding must:
- Teach all five gestures before the user ever reads a real book
- Feel like the app itself, not a detached tutorial mode — same visual language, same theme, same fonts
- Be **interactive**: the user must actually perform each gesture to advance, not just watch
- Be completable in under 90 seconds
- Be replayable at any time from Settings

Crucially: **the onboarding IS reading.** By the time it ends, the user has been reading a real text — they have already had the FlowRead experience. This is the strongest possible hook.

---

#### Onboarding Flow

The onboarding runs the first time the app is opened. It is a 6-step sequence that lives inside the reader interface using a bundled sample book (a short public domain excerpt — e.g. the opening of *Alice's Adventures in Wonderland*).

A subtle **"skip"** label sits in the top-right corner throughout. A single tap on it jumps to the final step. It is intentionally small — visible but not prominent, so users who want to learn are not distracted by it.

---

##### Step 1 — Welcome

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                                                                  │
│                          FlowRead                                │
│                    One word. Total focus.                        │
│                                                                  │
│                                                                  │
│                      ·  tap to begin  ·                         │  ← fades in after 2s
└──────────────────────────────────────────────────────────────────┘
```

- App name and tagline fade in over 1 second.
- "tap to begin" fades in after 2 seconds, pulses gently.
- User taps anywhere → advances to Step 2.

---

##### Step 2 — Play & Pause

The reader starts. The sample text rolls at ~140 WPM for 4–5 words, then **pauses automatically.** An animated tap indicator appears at the center of the screen.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                          Alice                                   │
│                                                                  │
│               ╭─────────────────────────────╮                   │
│               │  Tap anywhere to play        │                   │  ← overlay hint
│               │  and pause                   │                   │
│               ╰─────────────────────────────╯                   │
│                       👆  (animated)                             │
└──────────────────────────────────────────────────────────────────┘
```

- User must tap → reading resumes for another 4–5 words → pauses again.
- A small checkmark fades in briefly, then the step advances automatically.

---

##### Step 3 — Reading Speed

Reading is paused. The WPM counter is visible. An animated finger with up/down arrows appears.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                          was                                     │
│                                                                  │
│               ╭─────────────────────────────╮                   │
│               │  Swipe up to read faster  ↑  │                   │
│               │  Swipe down to slow down  ↓  │                   │
│               ╰─────────────────────────────╯                   │
│   WPM: 140                                                       │
└──────────────────────────────────────────────────────────────────┘
```

- User must perform either a swipe up or swipe down → WPM animates to the new value.
- Hint label updates briefly: "Nice — you can adjust this anytime while reading."
- Checkmark → advances.

---

##### Step 4 — Skim View

Reading is paused. An animated finger slides in from the right, gesturing leftward.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                        beginning                                 │
│                                                                  │
│               ╭─────────────────────────────╮                   │
│               │  Swipe left to see           │                   │
│               │  where you are in the text   │                   │
│               ╰─────────────────────────────╯                   │
│                              👈  (animated, sweeps left)         │
└──────────────────────────────────────────────────────────────────┘
```

- User swipes left → skim view opens, showing the sample paragraph with the current word highlighted.
- A second hint appears over the skim view:

```
┌──────────────────────────────────────────────────────────────────┐
│  Alice was beginning to get very tired of sitting by her         │
│  sister on the bank, and of having nothing to do: once or        │
│  twice she had peeped into the book her sister was reading,      │
│  but it had no pictures or conversations in it, [and]            │  ← current word highlighted
│  what is the use of a book, thought Alice, without               │
│                                                                  │
│          ╭─────────────────────────────╮                        │
│          │  Drag to move.              │                        │
│          │  Release to return.         │                        │
│          ╰─────────────────────────────╯                        │
└──────────────────────────────────────────────────────────────────┘
```

- User drags briefly → highlighted word moves through the text.
- User releases → returns to reader.
- Checkmark → advances.

---

##### Step 5 — Menu

Reading is paused. An animated finger holds on the screen with an expanding press-circle animation.

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                          pictures                                │
│                                                                  │
│               ╭─────────────────────────────╮                   │
│               │  Long press to open          │                   │
│               │  the menu                    │                   │
│               ╰─────────────────────────────╯                   │
│                       ◉  (hold animation)                        │
└──────────────────────────────────────────────────────────────────┘
```

- User long presses → the real menu slides in briefly (non-functional in onboarding — items are visible but tapping them does nothing).
- After 1.5 seconds the menu closes automatically.
- Hint: "From here you can navigate chapters, manage your library, and adjust settings."
- Checkmark → advances.

---

##### Step 6 — Ready

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│                                                                  │
│                        You're ready.                             │
│                                                                  │
│              Import a book          Read the sample              │
│                                                                  │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

- Two text-style tap targets (no button chrome), centered and spaced.
- **Import a book** → opens the file picker, then drops the user directly into the reader.
- **Read the sample** → continues the bundled excerpt from where the tutorial left off.

---

#### Ghost Hints (First Real Book)

The first time a user opens a book that is not the sample, a **single passive reminder** appears. It is a translucent strip at the bottom of the reader that cycles through four small gesture icons (tap, swipe up/down, swipe left, long press) with one-word labels.

It fades in after 3 seconds and disappears after 6 seconds. It never appears again.

This acts as a safety net for users who tapped "skip" during onboarding or who return after a break and have forgotten the gestures.

Ghost hints can be re-enabled at any time via **Settings → Replay Tutorial.**

---

#### Gesture Reference Card

Accessible from **Settings → Gesture Reference** at any time. A single full-screen landscape layout showing all gestures at a glance:

```
┌──────────────────────────────────────────────────────────────────┐
│  FLOWREAD — GESTURES                                             │
│                                                                  │
│  Tap anywhere          Play / Pause                              │
│  Swipe up              Faster  (↑ 10 WPM per step)              │
│  Swipe down            Slower  (↓ 10 WPM per step)              │
│  Swipe left            Skim View — see your place in the text    │
│  Long press (paused)   Open Menu                                 │
│                                                                  │
│                                          tap anywhere to close   │
└──────────────────────────────────────────────────────────────────┘
```

---

#### Onboarding Implementation Notes

- **State:** A `onboarding_complete` boolean is stored in the SQLite settings table. Checked on every app launch. Onboarding runs if false.
- **Sample book:** A short public domain excerpt (opening of *Alice's Adventures in Wonderland*, ~500 words) is pre-compiled as a `.rsvp` file bundled in the app assets. No conversion required.
- **Step tracking:** A local `onboardingStep` state (0–5) drives which gesture overlay is rendered. Each step registers a one-time gesture listener that resolves the step and advances.
- **Gesture detection in onboarding:** The same Gesture Handler setup used in the main reader is reused. Steps that require a specific gesture set `requiresGesture: 'tap' | 'swipeUp' | 'swipeDown' | 'swipeLeft' | 'longPress'` and only the matching gesture advances the step. Other gestures are silently ignored during tutorial steps.
- **Skip:** A small `TapGesture` zone (top-right, ~60×40pt) advances directly to Step 6 when tapped.
- **Replay:** Settings stores a `show_ghost_hints` flag. "Replay Tutorial" resets `onboarding_complete` to false and relaunches.

---

## 3. Technical & System Specs

### 3.1 Technology Stack

| Layer | Technology |
|---|---|
| **Framework** | React Native via Expo (managed workflow) |
| **Language** | TypeScript (strict mode) |
| **Styling** | NativeWind (TailwindCSS for React Native) |
| **Navigation** | Expo Router (file-based routing) |
| **Storage** | Expo SQLite (library/progress) + Expo FileSystem (book files) |
| **Gestures** | React Native Gesture Handler |
| **Animations** | React Native Reanimated |
| **Fonts** | Expo Font (Atkinson Hyperlegible, Lexend bundled via @expo-google-fonts) |
| **Orientation** | Locked to landscape via `expo-screen-orientation`; applied globally on app start |
| **Monetization** | RevenueCat SDK (in-app purchase / paywall management) |
| **Onboarding assets** | Pre-compiled `.rsvp` sample book bundled in `assets/` (public domain text, ~500 words) |

### 3.2 Supported Platforms

- **iOS** (primary target): iPhone, minimum iOS 16
- **Android**: minimum API level 31 (Android 12)

No tablet-specific layouts in v1.0 (phone form factor only).

### 3.3 The .rsvp File Format

The `.rsvp` format is a lightweight internal representation of a book, optimised for sequential word-by-word access. It is converted from the original file on first import and stored in the app's private document directory.

**Structure (JSON):**

```json
{
  "version": 1,
  "id": "<uuid>",
  "title": "<string>",
  "author": "<string>",
  "totalWords": 12345,
  "chapters": [
    { "title": "<string>", "start": 0 }
  ],
  "words": [
    { "w": "Alice", "s": false, "l": false }
  ]
}
```

Each word object has three fields: `w` (word text including any surrounding punctuation), `s` (sentence-end flag), `l` (long-word flag — stripped length ≥ 8 characters). Files are stored as UTF-8 JSON via Expo FileSystem and parsed in one pass on book open.

**Design decisions:**
- The entire word array is loaded into memory once on open; sequential access and random seek (skim view) are both O(1) array index operations — a binary format offers no runtime advantage.
- `JSON.parse` on a ~2.5 MB file (a 300-page novel) is native C++ and completes in well under 100 ms on target devices.
- Sentence boundaries and long-word flags are pre-computed at conversion time.
- Word index is the single source of truth for reading position and progress.

### 3.4 Conversion Engine

Conversion runs entirely on-device. No book content ever leaves the device.

| Input Format | Library / Approach |
|---|---|
| EPUB | `epub.js` or `foliate-js` parser; strip markup, walk spine in order |
| TXT / MD | Direct tokenization |
| HTML / XHTML | HTML parser; strip tags, extract text nodes |

PDF is deferred to v1.1. On-device PDF text extraction (especially for reflowable text vs. image-based scans) introduces quality and reliability issues that would degrade the first-run experience.

**Conversion pipeline:**

```
Raw file
  → Format detection
  → Text extraction (format-specific parser)
  → Unicode normalization (NFC)
  → Sentence boundary detection (punctuation rules)
  → Word tokenization
  → Chapter metadata extraction
  → .rsvp serialization
  → Written to Expo FileSystem documents directory
```

### 3.5 Reading Engine

The reading engine is a single TypeScript module responsible for advancing through words at the correct interval.

**Timing:**

```
baseDelay (ms) = 60000 / wpm
```

**Adaptive delay modifiers (all configurable in settings):**

| Modifier | Condition | Effect |
|---|---|---|
| Long word extension | Word length ≥ 8 characters | +35% delay (× 1.35) |
| Sentence pause | Word has sentence-end flag | +80% of base delay added after word |

These can be toggled independently in settings.

**State machine:**

```
IDLE → PLAYING (tap)
PLAYING → PAUSED (tap)
PAUSED → PLAYING (tap)
PAUSED → SKIM (swipe left)
SKIM → PAUSED (release finger)
PAUSED → MENU (long press)
MENU → PAUSED (swipe right)
```

### 3.6 Gesture System

Built on **React Native Gesture Handler** with **Reanimated** for frame-accurate response.

| Gesture | Handler type | Threshold |
|---|---|---|
| Tap → play/pause | `TapGesture` | standard tap |
| Long press → menu | `LongPressGesture` | 500ms hold (paused state only) |
| Swipe up/down → speed | `PanGesture` | min 30px vertical travel |
| Swipe left → skim | `PanGesture` | min 60px horizontal, direction lock |
| Hold + drag in skim | `PanGesture` | free after entering skim |

Speed change sensitivity: each swipe gesture changes WPM by ±10. WPM is clamped to a minimum of 60 and a maximum of 1000.

### 3.7 Data Persistence

| Data | Storage | Schema |
|---|---|---|
| Book library (metadata) | Expo SQLite | `books(id, title, author, file_path, cover_path, imported_at)` |
| Reading progress | Expo SQLite | `progress(book_id, word_index, updated_at)` |
| App settings | Expo SQLite | `settings(key, value)` — includes `onboarding_complete`, `show_ghost_hints` |
| .rsvp files | Expo FileSystem | `{documentsDir}/books/{book_id}.rsvp` |
| Cover images | Expo FileSystem | `{documentsDir}/covers/{book_id}.jpg` |
| Sample book | App bundle | `assets/sample.rsvp` (read-only, never copied to documents dir) |

### 3.8 System Status Bar

The system status bar (showing time, battery, wifi) is hidden via `expo-status-bar` with `hidden={true}` whenever the reader or menu screen is active. It is only visible on the library and import screens.

### 3.9 Performance Targets

| Metric | Target |
|---|---|
| App cold start | < 2 seconds |
| Book import (EPUB, ~300 pages) | < 5 seconds |
| Word advance latency | < 5ms deviation from target interval |
| Skim view open | < 100ms from gesture completion |
| Settings change applied | Immediate (next word) |

---

## 4. Project Management & Legal

### 4.1 Development Phases

#### Phase 1 — Foundation (Week 1–2)
- Expo project scaffold with TypeScript, NativeWind, Expo Router
- Navigation structure (Reader → Menu → Library → Settings → Onboarding)
- Gesture handler setup and basic gesture recognition
- System status bar hiding and landscape orientation lock
- Bundled sample book asset (pre-compiled `.rsvp`)

#### Phase 2 — Core Reading Engine (Week 3–5)
- `.rsvp` format definition and serialization
- EPUB conversion pipeline
- Reading engine (word advance, WPM timing, adaptive delays)
- RSVP Large mode (1 word) fully functional with gestures
- WPM indicator (appears/fades)
- Progress tracking and resume

#### Phase 3 — Full Reading Modes (Week 6–7)
- RSVP Medium and Small modes (3 and 6 words)
- Context / Skim View
- HUD (chapter + progress percentage)
- Chapter navigation

#### Phase 4 — Settings & Themes (Week 8)
- All settings screens implemented
- Dark / Light / Night themes
- Font family selection (Default, Atkinson, OpenDyslexic)
- Font size and anchor position settings

#### Phase 5 — Library & Import (Week 9)
- Library screen with cover art and progress
- File picker integration (local files, iCloud, Google Drive)
- EPUB, TXT, MD, and HTML conversion support
- Delete and manage books

#### Phase 6 — Onboarding & Polish (Week 10–11)
- Full onboarding flow (all 6 steps, interactive gesture detection per step)
- Ghost hint system (first real book, one-time appearance)
- Gesture Reference Card screen
- Gesture tuning and UX polish
- Edge case handling (very short books, single-chapter books, books with special characters)
- Performance profiling and optimisation
- App Store and Google Play submission preparation

### 4.2 Out of Scope (v1.0)

The following features are explicitly excluded from the initial version to keep scope focused:

- PDF import (deferred to v1.1)
- WiFi sync or cloud backup of books
- Text-to-speech / audio
- Social features (highlights, sharing quotes)
- Tablet or iPad layout
- Web companion app
- Annotations or bookmarks
- Portrait orientation support
- Firmware update mechanics (hardware-specific, not applicable)

### 4.3 Monetization

#### Model

FlowRead is a **paid app with a free trial.**

| Period | Access |
|---|---|
| First 3 days after install | Full app, unlimited |
| After 3 days | One-time purchase required to continue |

#### Pricing

- **Suggested price: $2.99** (one-time, no subscription)
- At $2.99, the app sits in the impulse-buy tier — low enough to avoid hesitation, high enough to signal it is a real product. If downloads are strong and reviews validate quality, bumping to $3.99 or $4.99 in a later version is straightforward without alienating early buyers.
- Pricing can be set independently per region on both App Store and Google Play.

#### Implementation

- **RevenueCat SDK** handles trial tracking, purchase flow, receipt validation, and restore purchases on both iOS and Android from a single integration.
- Trial start date is stored locally (SQLite) and validated server-side via RevenueCat on each app launch.
- After trial expiry, all reading features are paused and a minimal paywall screen is shown. The library (book list) remains visible so the user is not locked out of their own content.
- Restore Purchase option is available on the paywall screen (required by App Store guidelines).

#### App Store / Play Store Classification

- Both stores classify this as a **paid app** (upfront purchase), not a free app with IAP. This means the app appears as "$2.99" in store listings.
- Alternatively, the app can be listed as free with an IAP unlock — this increases discoverability but requires explicit "trial ends in X days" messaging inside the app.
- Decision: **paid upfront** is recommended for v1.0 to keep the experience clean and avoid the perception of a "freemium" product.

### 4.4 Open Source Dependencies & Licenses

| Dependency | License | Notes |
|---|---|---|
| React Native / Expo | MIT | Core framework |
| NativeWind | MIT | Tailwind styling |
| React Native Gesture Handler | MIT | Gesture recognition |
| React Native Reanimated | MIT | Animations |
| Expo Router | MIT | Navigation |
| Expo SQLite | MIT | Persistence |
| Expo FileSystem | MIT | File storage |
| expo-screen-orientation | MIT | Landscape lock |
| RevenueCat SDK | MIT | Trial / purchase management |
| Atkinson Hyperlegible font | SIL Open Font License 1.1 | Accessibility font |
| Lexend font | SIL Open Font License 1.1 | Reading ease font |
| EPUB parsing library (TBD) | MIT (to be confirmed at selection) | Conversion |

### 4.5 Intellectual Property

- All original FlowRead source code: proprietary, owned by the project author.
- Bundled fonts: distributed under SIL Open Font License 1.1 — permitted for embedding in commercial applications.
- The `.rsvp` file format: original design, no third-party IP.
- RSVP technique: not patentable as a concept; no known blocking IP.

### 4.6 Privacy

- No analytics, telemetry, or tracking of any kind in v1.0.
- No network requests during normal use.
- All book content and reading data stays on-device.
- No account or login required.
- App Store / Play Store privacy label: "Data Not Collected."

---

*End of FlowRead Specification v1.0*
