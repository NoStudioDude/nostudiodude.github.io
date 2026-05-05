---

## STYLE REFERENCE

Match the style and structure of the app, read spec_flow.md for more details about the app

---

## ABOUT THE APP

**Name:** FlowRead  
**Tagline:** One word. Total focus.  
**Platform:** iOS only (iPhone, landscape orientation)  
**Developer:** nostudiodude  
**Bundle ID:** com.nostudiodude.flowread  
**Category:** Books / Productivity  
**Price:** 2.99 eur / USD one time payment   
**Contact email:** nostudiodude@hotmail.com

---

## WHAT IT DOES

FlowRead is a gesture-first RSVP (Rapid Serial Visual Presentation) focus reader for iPhone. It solves a single problem: people who want to read more but lose focus, drift off the line, or find traditional e-readers too visually noisy.

The core concept: show one word at a time, dead center on screen, at a controlled speed. The eye never moves. There are no toolbars, no buttons, only the word you are reading right now.

**Key facts:**
- Zero on-screen buttons — every action is a gesture (tap, swipe, hold, drag)
- Runs exclusively in landscape orientation (wider reading field, less vertical space)
- Imports EPUB, TXT, and Markdown files from iCloud or local storage
- Saves reading position per book, restores automatically on next open
- Last opened book launches automatically on app start
- Fully offline — no internet connection, no account, no sync
- All reading data stays on device

---

## READING MODES

| Mode | Words shown | Description |
|---|---|---|
| Large | 1 | Single word, large and centered |
| Medium | 3 | Three words, center highlighted |
| Small | 5 | Five words, center highlighted |
| Skim / Context View | Full paragraph | Swipe left to enter; drag to scrub |

---

## GESTURE CONTROLS (the full "haptic language")

| Gesture | Action |
|---|---|
| Tap anywhere | Start / pause reading |
| Swipe up | Increase reading speed (WPM) |
| Swipe down | Decrease reading speed (WPM) |
| Swipe left | Enter Context / Skim View |
| Drag in Skim View | Scrub through text (left = back, right = forward) |
| Long press (paused) | Open navigation menu |
| Swipe right (in menu) | Close menu / return to reader |

The app also has a full haptic feedback system — each gesture has a distinct tactile feel (e.g. ramp-up pulse when starting, dial-tick per WPM step, elastic double-pulse at speed limits, two-phase pulse when entering skim mode).

---

## SETTINGS AVAILABLE IN THE APP

**Reading**
- Display Mode: Large / Medium / Small
- Word Anchor Position: Left / Center / Right
- Word Highlight: Full word or ORP center letter only
- Long Word Extension: On/Off
- Sentence Pause: On/Off

**Appearance**
- Theme: Dark (default, deep navy) / Light / Night (OLED pure black)
- Accent Color: Amber (default) / Red
- Font: Default / Atkinson Hyperlegible / Lexend
- Letter Spacing: Normal / Wide / Wider
- Word Spacing: Normal / Wide / Wider

**Speed**
- Default WPM: adjustable in 50 WPM steps in settings, and 10 WPM during reading session (range: 60–1000 WPM)

---

## ONBOARDING

The app includes an interactive 6-step tutorial that teaches all gestures before the user opens their first book. It uses a sample excerpt from Alice's Adventures in Wonderland (public domain). Steps: Welcome → Play/Pause → Speed Control → Skim View → Long Press Menu → Ready. The user must perform each real gesture to advance — it is not just a slideshow.

---

## PRIVACY

FlowRead collects absolutely no data:
- No analytics
- No tracking
- No user accounts
- No network requests of any kind
- No third-party SDKs
- All data (books, progress, settings) stored locally on device via SQLite and the iOS file system
- Files are processed fully on-device; nothing is uploaded anywhere

The app's Info.plist declares `ITSAppUsesNonExemptEncryption: false`.

---

## PAGE REQUIREMENTS

### index.html — Landing Page

Structure:
1. **Hero** — App name, tagline ("One word. Total focus."), App Store badge/link (placeholder if not live yet), short one-liner about what it does
2. **The problem it solves** — 2–3 sentences: losing the reading line, distraction from UI chrome, the eye drifting. Target readers with ADHD, dyslexia, or high-stimulation environments
3. **How it works** — 3 simple steps (e.g. "Import your book → Tap to start → Words flow at your speed")
4. **Key features** — short bullet list: gesture-only, RSVP display modes, landscape layout, auto-saves progress, EPUB/TXT/MD support, haptic feedback, accessibility fonts, fully offline
5. **Gesture reference** — brief table or icon list of the main gestures
6. **Privacy callout** — one-liner: "No accounts. No tracking. Your books stay on your device."
7. **Footer** — link to Privacy Policy, link to Support, © 2026 nostudiodude

### privacy-policy.html — Privacy Policy

Match the structure of https://nostudiodude.github.io/fluentify/privacy-policy exactly. Sections:

- **What data FlowRead processes** — None. The app stores your books, reading progress, and settings locally on your device. No data leaves your device.
- **What FlowRead does not do** — No analytics, no tracking, no cookies, no accounts, no network requests, no transmission of any data to any server.
- **Local storage** — SQLite database and iOS file system only. Stored: imported books (.rsvp format), reading progress per book, reading preferences/settings.
- **Third-party SDKs** — None. The app uses only Apple system frameworks and open-source libraries (expo-haptics, expo-sqlite, expo-file-system, react-native-gesture-handler, react-native-reanimated, JSZip, fast-xml-parser). None of these collect data.
- **Fonts** — Atkinson Hyperlegible (SIL Open Font License) and Lexend (SIL Open Font License) are bundled as static assets. No font services are called.
- **Your choices** — You can delete all app data by deleting the app from your device.
- **Contact** — nostudiodude@hotmail.com
- Last updated: 05/05/2026

### support.html — Support Page

Sections:

1. **Getting Started** — Brief: import an EPUB, TXT, or MD file from Files app or iCloud. Tap to start reading.

2. **Gesture Reference** (full table):

| Gesture | What it does |
|---|---|
| Tap | Start / pause |
| Swipe up | Speed up (WPM) |
| Swipe down | Slow down (WPM) |
| Swipe left | Enter Skim/Context View |
| Drag in Skim View | Scrub through text |
| Long press (paused) | Open menu |
| Swipe right (in menu) | Return to reader |

3. **FAQ**

- *What file formats are supported?* — EPUB, plain text (.txt), and Markdown (.md). PDF is not supported.
- *Where is my reading progress saved?* — On your device only. Progress is saved automatically whenever you pause or leave the reader.
- *Can I change the reading speed?* — Yes. Swipe up to increase WPM, swipe down to decrease. The current WPM is shown briefly after each adjustment. You can also set a default WPM in Settings.
- *What is WPM?* — Words Per Minute. The app supports 60–1000 WPM. Most people read comfortably at 200–400 WPM.
- *What does "ORP" mean in the Word Highlight setting?* — Optimal Recognition Point — the letter in a word your brain uses to identify it fastest. When set to "Letter", only that center letter is highlighted. This is the default and recommended setting.
- *The app is stuck in landscape — can I rotate it?* — FlowRead is designed exclusively for landscape orientation. This is intentional: it gives more horizontal reading space and keeps your eye focused on a single vertical band.
- *How do I open the menu?* — Long press anywhere on the reading screen while reading is paused.
- *How do I get back to my library?* — Long press to open the menu → tap LIBRARY.
- *Does the app require internet?* — No. FlowRead is fully offline. No account needed.
- *My book isn't importing* — Make sure it's an EPUB, TXT, or MD file. Large files may take a few seconds to process. If the issue persists, try exporting the file from a different app first.

4. **Contact** — "Have a question not covered here? Email nostudiodude@hotmail.com"

5. **Footer** — same as landing page

---

## TECHNICAL NOTES

- All three pages must be plain HTML/CSS files (no build step, just static files for GitHub Pages)
- Use a consistent `<nav>` with links to all three pages
- The favicon should reference `assets/favicon.png`
- All internal links should be root-relative (e.g. `/flowreadapp/support.html`) 
- App Store link placeholder: use `#` until the app is live, with a comment marking it for replacement
- Add `© {CURRENT_YEAR} nostudiodude` to the footer