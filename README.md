# USVERSE — Khushi × Gaurav

A playable private two-player website with 12 game worlds, a cinematic arcade/casino/HQ aesthetic, and real-time sync over Firebase Realtime Database. Vanilla HTML/CSS/JavaScript: **no npm, no build step, and no server code**.

## Quick preview

Open `index.html` (or serve it using `python3 -m http.server 8080`) to try the local preview. The local preview syncs two tabs in the **same browser and origin** using localStorage + BroadcastChannel. It does **not** sync different devices.

## Enable genuine two-player play

1. Visit [Firebase Console](https://console.firebase.google.com/) and create a project.
2. In **Project settings → Your apps**, register a **Web** app. Copy the Firebase config object into `firebase-config.js` (don't delete the `window.USVERSE_FIREBASE_CONFIG =` assignment).
3. In **Build → Authentication → Sign-in method**, enable **Anonymous** sign-in.
4. In **Build → Realtime Database**, create a Realtime Database and choose the location closest to you. Copy its **databaseURL** into `firebase-config.js`. Do not use a Firestore database for this project.
5. In Realtime Database → **Rules**, copy the contents of `firebase-rules.json` and **Publish**. These rules limit state writes to the two players. They are meant for a private experimental site, not a hardened production identity system.
6. Save the modified `firebase-config.js` file, and keep it alongside `index.html`, `app.js` and `styles.css`.
7. **Unzip** the supplied project. Open [Netlify Drop](https://app.netlify.com/drop) and drag the **folder** containing `index.html` into the upload zone. Netlify publishes the site and provides a URL. To update, drag the modified folder to the deploy area again.
8. Open the Netlify link on one device, choose **Khushi → Create room**, copy the eight-character code, and send the URL and code to Gaurav. On a **different device or browser profile**, choose **Gaurav → Join room** and enter that same code.

### If you get `auth/unauthorized-domain`

In Firebase Authentication, configure the authorized domains to include your Netlify site domain if required by your project's settings. Anonymous auth and the realtime database must be enabled.

## What's playable

- **The Mystery Room:** Five chapter cooperative code puzzles, separate clues per player, timer, hints for coins, and sneaky side deals.
- **Cricket Mayhem:** Secret batting/bowling choices, strategic shot placement, innings and match results.
- **Mind Games:** Predicted secret answers for points and a separate unscripted deep-talk mode.
- **The Receipts:** Who Said It? and harmless relationship-history trivia with simultaneous answers.
- **Art Attack:** A shared freehand canvas (touch/mouse/stylus) with challenges, undo, eraser and PNG export.
- **Hot Mess:** Explicit opt-in by both players, negotiated intensity, flirty cards and skip-anytime rules. Non-graphic content.
- **Love Casino:** Fictional-coin roulette. **No real money, deposits or purchases.**
- **The Courtroom:** Competitive evidence-card rock-paper-scissors, amusing allegations and written arguments.
- **Jukebox Wars:** Pop/Taylor Swift music trivia. No licensed music audio is embedded.
- **The Multiverse:** Travel roulette, hidden date choices and collaborative discovery.
- **Cinema Chaos:** Three-act story creation and screenplay export.
- **The Vault:** Hidden partner letters that unlock when both submit, and a shared reunion bucket list.
- Global scoreboard, Chaos Coins, side missions, room sharing, progress persistence, achievements in activity feed, animations, responsive layout.

## Privacy and practical notes

- This is a **personal prototype**, not an end-to-end encrypted chat or secure secret vault. Firebase RTDB data is readable by authenticated users who know a room code. Treat the link/code like a private invitation; don't use it for sensitive or highly intimate personal details.
- A Firebase web config is a public app identifier; security comes from Firebase Auth and Database Rules. Never put Firebase service-account credentials or secret API keys in these web files.
- No raw chat archives were included or uploaded. The trivia uses a **small curated selection of non-explicit quotes**.
- Only 2 intended slots (Khushi and Gaurav), but this is not strong identity verification. For a public product, add real accounts, server-side validation, rate limits and restricted reads.
- The same browser profile can accidentally share the Firebase anonymous UID between tabs. For a proper two-player test, use a separate device or private window.
- Firebase free-tier limits and availability can change; check the current limits in Firebase console.
- Sound works only after browser interaction. Canvas strokes sync on stroke completion, not every mouse movement.
- The mystery code puzzles are authored fictional clues, not reconstructed private relationship events. Personal chat trivia comes from the supplied excerpts.

## Source files

`index.html` (entry point), `styles.css` (design), `app.js` (game content + logic), `firebase-config.js` (paste Firebase settings), `firebase-rules.json` (paste into Realtime Database Rules).

No analytics or ads. Love is a competitive sport. ♥
