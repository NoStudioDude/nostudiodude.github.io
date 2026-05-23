# Kira Website Spec — GitHub Pages Production Landing Page

## Context

I currently host simple app landing pages on GitHub Pages:

- `/flowreadapp/`
- `/fluentify/`

I want to add a new production page:

```text
/kira/
````

The page should be created inside the same GitHub Pages project/repository and follow the same deployment approach as the existing pages.

This page is for **Kira**, a privacy-first iOS expense tracker.

The website must include:

1. A main marketing landing page
2. A support page
3. A privacy page

These pages are needed for:

* App Store listing
* in-app Settings links
* user support
* trust/privacy explanation

The visual direction should be inspired by modern minimal app websites like MonAi, but it must use Kira’s own identity, color palette, mascot, copy, and product positioning. Do not copy MonAi directly.

---

# Required Routes

Create these routes/pages:

```text
/kira/
/kira/support/
/kira/privacy/
```

Optional but recommended:

```text
/kira/terms/
```

If adding `/terms/` is easy, include it. Since the app uses subscriptions, it is useful for App Store readiness.

---

# Product Summary

Kira is a calm, private, local-first expense tracking app for iOS.

It helps users track expenses with minimal effort using:

* voice input
* manual quick entry
* receipt scanning
* smart categorization
* AI assistant/chat
* category spending limits
* Apple Pay Shortcut integration
* local-first storage
* freemium + Premium subscription model

Core message:

```text
Track expenses without making expense tracking feel like work.
```

Kira should feel:

* calm
* private
* effortless
* warm
* premium
* friendly
* native iOS
* emotionally soft, not corporate

Kira is named after a real cat and uses a cartoon Kira mascot as part of the brand identity.

---

# Brand Direction

## Brand personality

Kira should feel like:

```text
A calm companion that helps you stay aware of your spending without judgment.
```

Avoid:

* aggressive finance language
* banking-style corporate visuals
* cold SaaS design
* dark “AI startup” branding
* overpromising automation
* implying direct Apple Wallet access

Use:

* soft shapes
* warm backgrounds
* large clean typography
* product screenshots
* mascot accents
* honest privacy messaging
* minimal, premium copy

---

# Color Palette

Use Kira’s app palette.

## Primary

```css
--kira-bg: #F6F3EE;          /* warm ivory */
--kira-card: #FCFBF8;        /* soft near-white */
--kira-text: #262220;        /* deep charcoal */
--kira-muted: #9A938B;       /* soft taupe gray */
--kira-sage: #7B9770;        /* primary sage */
--kira-sage-soft: #AFC4A6;   /* soft sage */
```

## Accents

```css
--kira-lavender: #D8CDED;
--kira-apricot: #EDC4AA;
--kira-butter: #E6CF8E;
--kira-line: rgba(38, 34, 32, 0.10);
```

## Background feel

Use:

* warm ivory base
* soft radial gradients
* gentle blur blobs
* subtle cards
* no harsh borders
* no pure white page feeling unless inside cards

---

# Typography

Use system fonts.

Recommended:

```css
font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "SF Pro Text", system-ui, sans-serif;
```

Headings:

* large
* rounded/native feel
* strong but soft

Body:

* readable
* muted
* not too small

Avoid:

* overly SaaS-looking typography
* too many font weights
* playful childish fonts

---

# Assets

Use provided Kira app screenshots.

Screenshots available from current app include:

* Home screen with spending bars and bottom sheet
* Home screen with expanded expenses
* Kira chat assistant
* Manual/add expense screen
* Receipt camera scan
* Receipt parsed result screen

Use them in the landing page.

Important:

* Do not show screenshots raw in a boring grid.
* Present them in premium device mockups or soft rounded image frames.
* Use subtle shadows.
* Crop where needed.
* Keep the page airy.

Use Kira mascot artwork where appropriate:

* hero accent
* support page
* privacy page
* “Named after Kira” section

---

# Main Landing Page Structure

Route:

```text
/kira/
```

## 1. Top Navigation

Simple sticky or static header.

Left:

```text
Kira
```

Optionally include small mascot/icon.

Right nav:

```text
Features
Privacy
Support
Download
```

`Download` should be a button, but if App Store link is not ready yet, use:

```text
Coming soon
```

or an anchor to a placeholder section.

Do not use fake App Store badges unless the app is actually available.

---

## 2. Hero Section

### Goal

Immediately communicate:

* what Kira does
* why it is different
* that it is effortless
* that it is privacy/local-first

### Headline options

Preferred:

```text
Track expenses without the effort.
```

Alternative:

```text
A calmer way to track spending.
```

Alternative:

```text
Speak, scan, or tap. Kira handles the rest.
```

### Subtitle

```text
Kira is a private expense tracker for iPhone that helps you log spending by voice, receipt scan, or quick entry — then keeps everything organized by category.
```

### CTA buttons

Primary:

```text
Download on the App Store
```

If app is not live:

```text
Coming soon to the App Store
```

Secondary:

```text
How Kira works
```

### Trust line

Below CTA:

```text
Local-first. No bank connection required. AI only when you ask for it.
```

Important:
Do not say “100% offline” because AI features use Gemini through a Cloudflare proxy.

### Visual

Right side / below hero:

* use the Home screen screenshot in a large iPhone mockup
* optionally overlay small Kira mascot
* add soft category bar shapes in background

Hero should feel similar in quality to MonAi’s landing style: product-first, large clean headline, clear value proposition, and app screenshot focus, but with Kira’s warmer palette and privacy-first message.

---

## 3. Problem Section

### Section headline

```text
Expense tracking usually fails because it takes too much effort.
```

### Supporting copy

```text
Most apps expect you to remember every purchase, fill out forms, and check dashboards. Kira is built around the opposite idea: capture expenses naturally, then stay gently aware.
```

### Cards

Use 3 soft cards:

#### Card 1

```text
You forget small purchases
```

```text
Coffee, groceries, parking, subscriptions — they add up before you notice.
```

#### Card 2

```text
Manual entry feels like work
```

```text
Kira lets you speak, scan, or quickly tap it in.
```

#### Card 3

```text
You want clarity, not complexity
```

```text
Simple category bars show where your money is going.
```

---

## 4. How It Works Section

### Section headline

```text
Three easy ways to log an expense.
```

### Layout

Use 3 columns on desktop, stacked cards on mobile.

### Feature 1 — Voice

Title:

```text
Speak naturally
```

Copy:

```text
Say something like “Spent €12 at Lidl” and Kira turns it into an expense with amount, merchant, category, and tags.
```

Use screenshot:

* chat/voice UI or microphone button from home screen

### Feature 2 — Scan

Title:

```text
Snap receipts
```

Copy:

```text
Take a photo of a receipt and Kira extracts the merchant, total, date, and category suggestion.
```

Use screenshot:

* receipt camera scan
* parsed Jumbo receipt result

### Feature 3 — Quick entry

Title:

```text
Add it manually
```

Copy:

```text
Prefer typing? Add the merchant, amount, category, date, and recurrence in a clean focused screen.
```

Use screenshot:

* add expense screen

---

## 5. Main Product Feature Section

### Section headline

```text
A spending overview that stays calm.
```

### Supporting copy

```text
Kira avoids overwhelming dashboards. Your home screen gives you the essentials: total spent, category bars, and a smooth expense list you can expand when you need details.
```

### Visual

Use two screenshots side by side:

* home collapsed
* home expanded bottom sheet

### Bullet points

```text
- Category bars show where spending goes
- Expenses live in a smooth draggable sheet
- Tap the total to open deeper statistics
- Search and review entries without clutter
```

---

## 6. AI Assistant Section

### Headline

```text
Ask Kira about your spending.
```

### Copy

```text
Ask questions like “What was my top category this month?” or “How can I save €100?” Kira uses your local spending summary to answer clearly.
```

### Privacy note

```text
AI requests are stateless. Kira only sends the information needed for the current question.
```

### Visual

Use chat assistant screenshot.

### Feature bullets

```text
- Ask spending questions in plain language
- Get category and trend explanations
- Free plan includes daily AI messages
- Premium unlocks more smart help
```

---

## 7. Limits / Budget Section

### Headline

```text
Set gentle limits without spreadsheet stress.
```

### Copy

```text
Add spending limits to categories and see when you are under or over. Kira keeps limits visual and lightweight.
```

### Visual

If no screenshot exists yet, create simple HTML/CSS visual:

* capsule category bars
* dotted outline for limit
* filled bar for current spending
* one category over limit

### Bullets

```text
- One free category limit
- Unlimited limits with Premium
- Visual progress per category
- No complex budgeting setup
```

---

## 8. Apple Pay Shortcut Section

### Headline

```text
Optional Apple Pay Shortcut support.
```

### Copy

```text
Apple does not allow apps to read Wallet transactions directly. Kira can still help through iOS Shortcuts, so Apple Pay transactions can open a quick review flow.
```

### Important wording

Do not claim:

```text
Automatic Apple Wallet sync
```

Do claim:

```text
Apple Pay Shortcut integration
```

### Bullets

```text
- Uses iOS Shortcuts
- No bank login required
- Review before saving
- Premium automation feature
```

### CTA

```text
Learn how it works
```

This can link to a support page section.

---

## 9. Privacy Section

### Headline

```text
Private by design. Local-first by default.
```

### Copy

```text
Kira stores your core expense data on your device. AI features are optional and use stateless requests through a secure proxy, with only the minimum information needed for that action.
```

### Cards

#### Card 1

```text
No bank connection required
```

```text
Kira does not need your bank login to work.
```

#### Card 2

```text
On-device first
```

```text
Receipt text is extracted locally before AI is considered.
```

#### Card 3

```text
Stateless AI
```

```text
AI requests are used for the current action only.
```

#### Card 4

```text
Export your data
```

```text
Kira lets you export your expenses.
```

### CTA

```text
Read privacy policy
```

Links to:

```text
/kira/privacy/
```

---

## 10. Freemium / Premium Section

### Headline

```text
Free to start. Premium when you want Kira to do more.
```

### Copy

```text
Kira’s free plan is useful for everyday tracking. Premium unlocks more smart input, receipt help, category limits, automation, and deeper insights.
```

### Pricing cards

If pricing is finalized:

```text
Monthly
€4.99 / month

Yearly
€29.99 / year
Best value
```

If not finalized:

```text
Premium
Monthly and yearly options available in the app.
```

### Free includes

```text
- Unlimited manual expenses
- Basic local tracking
- 5 smart voice parses per day
- 3 AI chats per day
- 3 AI receipt helps per month
- 1 category limit
```

### Premium includes

```text
- More smart voice parsing
- More AI assistant messages
- More AI receipt help
- Unlimited category limits
- Apple Pay Shortcut automation
- Advanced insights
- Export features
```

Important:
Do not overuse the word “unlimited” unless the implementation and terms support fair use.

Recommended wording:

```text
Generous Premium usage with fair use protection.
```

---

## 11. About Kira Section

### Headline

```text
Named after Kira.
```

### Copy

```text
Kira is named after a very special cat who brought calm and warmth into everyday life. This app carries a little of that spirit: simple, gentle, and always on your side.
```

Use Kira mascot illustration.

Keep this section tasteful and short.

---

## 12. Final CTA

### Headline

```text
Start tracking with less effort.
```

### CTA

```text
Download on the App Store
```

or:

```text
Coming soon to the App Store
```

Secondary links:

```text
Support
Privacy
```

---

# Footer

Footer should include:

```text
Kira
A calm, private expense tracker for iPhone.
```

Links:

```text
Support
Privacy
Terms
Contact
```

Copyright:

```text
© 2026 NoStudioDude. All rights reserved.
```

If “NoStudioDude” is not the final publisher name, make it easy to update.

---

# Support Page

Route:

```text
/kira/support/
```

## Purpose

This page is for App Store support URL and in-app Settings.

It must be clear, simple, and production-ready.

## Page title

```text
Kira Support
```

## Subtitle

```text
Need help with Kira? Here are the most common answers.
```

## Sections

### 1. Contact

```text
For support, feedback, or bug reports, contact:
```

Use actual support email placeholder for now:

```text
support@nostudiodude.com
```

If the final email is different, make it easy to replace.

### 2. Common Questions

#### How does Kira store my data?

```text
Kira stores your core expense data locally on your device.
```

#### Does Kira connect to my bank?

```text
No. Kira does not require a bank connection.
```

#### Does Kira use AI?

```text
Yes, for optional smart features like voice parsing, assistant chat, and receipt help. AI requests are stateless and only include the information needed for the current action.
```

#### Can Kira read Apple Wallet transactions?

```text
No app can freely read all Apple Wallet transactions directly. Kira can support Apple Pay logging through iOS Shortcuts where available.
```

#### How do I restore Premium?

```text
Open Kira → Settings → Restore purchases.
```

#### How do I delete my data?

```text
Open Kira → Settings → Data & Privacy → Delete all expenses.
```

#### How do I export my data?

```text
Open Kira → Settings → Data & Privacy → Export data.
```

### 3. Troubleshooting

Include:

```text
Voice input does not understand me
```

Suggestions:

* check Voice language in Settings
* check microphone permission
* speak naturally with amount and merchant

```text
Receipt scan did not detect the right amount
```

Suggestions:

* retake photo in good light
* align receipt
* review extracted result before saving

```text
Notifications do not work
```

Suggestions:

* check iOS notification permission
* check daily reminder settings

### 4. Legal links

Add:

```text
Privacy Policy
Terms of Use
```

---

# Privacy Page

Route:

```text
/kira/privacy/
```

## Purpose

This page must be suitable for App Store review and user trust.

Do not make legal claims that are false.

Kira is local-first, not fully offline, because AI features use Gemini via a Cloudflare Worker proxy.

## Page title

```text
Kira Privacy Policy
```

## Last updated

Use current date or placeholder:

```text
Last updated: [DATE]
```

## Required Sections

### 1. Overview

```text
Kira is designed as a local-first expense tracker. Your core expense data is stored on your device. Some optional AI features may send limited information to process a specific request.
```

### 2. Data Stored on Device

Explain:

* expenses
* categories
* tags
* settings
* usage counters
* preferences
* onboarding selections

### 3. AI Features

Explain the current AI usage accurately:

```text
Kira uses AI for optional features such as voice input parsing, chat assistant responses, and receipt categorization help.
```

Specify:

* voice parsing sends transcript
* chat sends question + spending summary
* receipt help sends extracted receipt text when needed
* requests are stateless
* no permanent AI storage by Kira

### 4. Cloudflare Proxy

Explain:

```text
Kira routes AI requests through a secure proxy so the AI provider API key is not stored in the app.
```

Mention:

* requests are processed to provide the feature
* no user account required unless implemented later

### 5. No Bank Connection

```text
Kira does not require your bank login and does not connect directly to your bank account.
```

### 6. Apple Pay Shortcut

```text
If you use Apple Pay Shortcut integration, payment details are sent to Kira only through the shortcut action you configure.
```

Do not claim direct Wallet syncing.

### 7. Subscriptions

Mention RevenueCat if used:

```text
Kira uses RevenueCat to manage subscription status and purchases. Payment processing is handled by Apple.
```

### 8. Data Export / Deletion

Explain:

* users can export data
* users can delete expenses in-app
* deleting the app may remove local data if not backed up

### 9. Contact

Support email.

### 10. Changes

Standard privacy policy change notice.

---

# Terms Page

Route:

```text
/kira/terms/
```

If implementing:

Use a simple terms page with:

* subscription terms
* free trial
* cancellation through Apple
* no financial advice disclaimer
* acceptable use
* limitation of liability
* contact email

Important:
Kira gives spending insights, but should not present itself as professional financial advice.

Suggested disclaimer:

```text
Kira provides personal expense tracking and informational insights only. It does not provide financial, legal, tax, or investment advice.
```

---

# Design Inspiration Notes

Use MonAi only as broad inspiration for structure:

* strong hero
* clear app screenshot
* feature sections
* how-it-works flow
* automation explanation
* user benefit-focused copy

Do not copy:

* exact layout
* exact copy
* exact claims
* exact colors
* exact review claims

Kira’s positioning is different:

* calmer
* more privacy-first
* mascot-driven
* local-first
* softer and warmer

---

# Implementation Requirements

## Technical

Use the same stack/style as existing GitHub Pages pages if possible.

The site should work as static pages.

No backend required.

Recommended:

* plain HTML/CSS/JS
* or same framework already used in the repository
* mobile-first responsive design
* SEO metadata
* Open Graph metadata
* favicon/app icon if available

## Folder structure suggestion

```text
/kira/
  index.html
  support.html
  privacy.html
  terms.html
  assets/
    kira-home.png
    kira-home-expanded.png
    kira-chat.png
    kira-add-expense.png
    kira-camera.png
    kira-receipt-result.png
    kira-mascot.png
    kira-icon.png
```

If existing repo uses subfolders with `index.html`, prefer:

```text
/kira/index.html
/kira/support/index.html
/kira/privacy/index.html
/kira/terms/index.html
```

This gives cleaner URLs.

---

# SEO Requirements

## Main page title

```text
Kira — Private Expense Tracker for iPhone
```

## Meta description

```text
Kira is a calm, private expense tracker for iPhone. Log expenses by voice, receipt scan, or quick entry, with smart categorization and local-first storage.
```

## Keywords to naturally include

* expense tracker
* spending tracker
* budget tracker
* receipt scanner
* voice expense tracker
* private expense tracker
* iPhone expense tracker
* local-first expense tracker
* AI expense assistant

Do not keyword-stuff.

---

# Accessibility Requirements

* Good contrast
* Buttons must have readable labels
* Images need meaningful alt text
* Do not rely only on color
* Mobile navigation must be usable
* Font sizes must be readable on small screens
* Respect reduced motion if animations are added

---

# Screenshots Usage

Use the provided screenshots as follows:

## Hero

Use:

* home screen collapsed

## Product overview

Use:

* home collapsed
* home expanded

## AI assistant

Use:

* chat screen

## Expense input

Use:

* add expense screen
* receipt camera
* receipt parsed result

Screenshots should be framed:

* rounded corners
* subtle shadow
* no overly heavy device frame unless it looks premium
* consistent sizes
* avoid clutter

---

# Copy Tone

Use short, clean, warm copy.

Avoid:

```text
Revolutionary
Game-changing
AI-powered financial freedom
Never worry about money again
Automatically syncs Wallet
```

Use:

```text
Calm
Private
Effortless
Local-first
Quick
Gentle
Smart when you need it
```

---

# Main Page Copy Draft

## Hero

```text
Track expenses without the effort.

Kira is a private expense tracker for iPhone. Speak, scan, or quickly add expenses — Kira organizes them into calm category views.

Local-first. No bank connection required. AI only when you ask for it.
```

## Problem

```text
Expense tracking usually fails because it takes too much effort.

Kira is built for quick capture: the moment you remember, the moment you pay, or the moment you find the receipt.
```

## How it works

```text
Speak naturally.
Say “Spent €12 at Lidl” and Kira turns it into an organized expense.

Scan receipts.
Take a photo and Kira extracts the merchant, total, date, and category suggestion.

Add quickly.
Prefer typing? Use a clean focused entry screen without unnecessary fields.
```

## Home

```text
A spending overview that stays calm.

See your total, category bars, and recent expenses without opening a complicated dashboard.
```

## AI

```text
Ask Kira about your spending.

Kira can answer questions about your expenses using a small spending summary from your device.
```

## Privacy

```text
Private by design. Local-first by default.

Your core expense data lives on your device. Optional AI features use stateless requests only when needed.
```

## Premium

```text
Free to start. Premium when you want Kira to do more.

Use Kira for everyday tracking for free, or unlock more smart input, receipt help, category limits, and automation with Premium.
```

---

# Acceptance Criteria

The implementation is complete when:

* `/kira/` exists and looks production-ready
* `/kira/support/` exists and can be used as App Store support URL
* `/kira/privacy/` exists and can be used as App Store privacy URL
* `/kira/terms/` exists if subscription/legal flow requires it
* page is fully responsive
* screenshots are integrated cleanly
* Kira color palette is used
* copy is accurate and does not overclaim
* privacy wording correctly explains local-first + optional AI
* Apple Pay Shortcut wording does not imply direct Wallet access
* App Store CTA is ready or clearly marked as coming soon
* links work
* footer links work
* legal/support pages are accessible from the main page
* visual quality is close to a premium iOS app landing page