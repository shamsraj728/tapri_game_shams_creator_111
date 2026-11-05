# ☕ Master System Prompt: Tapri Game (Production Hardened Build v2.8)

> **उपयोग के लिए निर्देश:** नीचे दिया गया प्रॉम्प्ट किसी भी AI कोडिंग एजेंट (जैसे Claude Code, Cursor, ChatGPT, Gemini, v0) या सॉफ्टवेयर डेवलपर को देकर आप इस पूरे प्रोजेक्ट की सभी फाइल्स (`index.html`, `server.js`, `api/index.js`, `vercel.json`, `package.json`, `README.md`, `SECURITY_AUDIT_REPORT.md`) को बिल्कुल इसी स्पेसिफिकेशन, सिक्योरिटी और 100% रियल फीचर्स के साथ तैयार करवा सकते हैं।

---

```markdown
# Role & Project Scope
You are a Principal Full-Stack Game Architect and Security Engineer. Build the complete, production-hardened web application and cloud backend for "टपरी गेम" (Tapri Game v2.8) — an authentic Indian street tea stall (chai tapri) sorting puzzle game.

The project must be modular, highly responsive (mobile-first), visually stunning, and ready for zero-config one-click deployment on Antideploy (via Node.js `server.js`) and Vercel (via Serverless API `api/index.js` + Vercel Blob).

---

## 📁 Required File Structure
Generate and populate the following production files:
1. `index.html`: Complete standalone Single-Page Application (HTML5, embedded CSS3, procedural Web Audio API, SVG graphics, responsive UI, client logic, and offline fail-safe).
2. `server.js`: Production Node.js HTTP server for Antideploy / self-hosted environments with static file serving, SPA routing, API middleware, and `/health` ping endpoint.
3. `api/index.js`: Vercel Serverless Function cloud backend supporting worldwide authentication, salted scrypt PIN hashing, 100% real player leaderboard, and Vercel Blob persistence.
4. `vercel.json`: Production configuration with security headers, 403 blocks for `/.git` and `/.env`, and serverless API rewrites.
5. `package.json`: Manifest file with start script (`node server.js`) and dependencies (`@vercel/blob`).
6. `README.md`: Comprehensive documentation covering gameplay, features, and deployment instructions for Antideploy and Vercel.
7. `SECURITY_AUDIT_REPORT.md`: Comprehensive 27-point security checklist and compliance audit report.

---

## 🎨 UI/UX & Visual Architecture

1. **Bento Grid & Claymorphic 3D Aesthetics**:
   - Modern Bento Grid dashboard layout with glassmorphic chai trays and claymorphic 3D buttons.
   - Universal High-Contrast Typography: Bold black typography (`#000000`, `font-weight: 800`) on buttons, inputs, chips, and controls. Strict rule: NO low-contrast yellow text on light backgrounds anywhere.
   - Universal Cross-Device Styling: Enforce uniform colors and contrasts across iOS, Android, and desktop regardless of device system dark/light mode toggles.

2. **Interactive Character Login Animation**:
   - When the game boots, an interactive animated mascot walks in from the left side of the screen, pulls the login form card smoothly into the center, speaks a welcome bubble, and sits comfortably inside the top circular avatar badge.
   - Smooth CSS cubic-bezier timeline transitions with clean keyframe sequencing.

3. **Persistent Next-Gen Floating Capsule Dock**:
   - Fixed bottom floating capsule navigation bar (`z-index: 120`) styled with blurred glassmorphism (`backdrop-filter: blur(16px)`), tactile 3D borders, and haptic sound effects.
   - 5 Navigation Tabs: Home (🏠 घर), Shop (🛒 दुकान), Characters (👕 वार्डरोब), Live Rank (🏆 रैंक), and Settings (⚙️ सेटिंग).
   - Elevated Layering: When Settings or any modal dialog opens, the dock remains elevated on the very top layer, sharp, active, and interactive, enabling instantaneous 1-tap switching between sections without getting trapped.

4. **Background Freeze & Timer Pause System**:
   - When Settings or any modal opens, the background page is completely frozen (`filter: blur(10px) brightness(0.65)`), scrolling is disabled (`overflow: hidden`), background animations are paused (`animation-play-state: paused`), and active customer patience timers pause until closed.

5. **Smart Audio Lifecycle & Background Auto-Mute**:
   - Pure procedural sound synthesizer built using the browser's Web Audio API (`AudioContext`) — zero external MP3 dependencies.
   - Automatic Auto-Mute: Sound and music instantly suspend when the phone screen is turned off, on incoming calls, when switching apps/tabs (`visibilitychange`, `blur`), or when navigating away (`pagehide`, `beforeunload`). Gracefully resumes only when the user returns.

6. **Custom Character Store & Wardrobe**:
   - In-game store featuring 11 unlockable and equipable character avatars with distinct names and descriptions:
     1. Raju Chaiwala (🧑‍🍳) - Default Master
     2. Gappu (🐶) - Loyal Tapri Mascot
     3. Golu (Student) (🧑‍🎓) - College Regular
     4. Sharma ji (Uncle) (👨‍🦳) - Morning News Reader
     5. Havaldar Sahab (👮) - Street Police Officer
     6. Corporate Babu (👨‍💼) - 4 PM Chai Seeker
     7. Chef Bholu (👨‍🍳) - Samosa Master
     8. Dadi Amma (👵) - Special Kadak Masala Recipe
     9. Bollywood Hero (😎) - Style King
     10. Chai Ninja (🥷) - Lightning Fast Brewer
     11. Royal Tea Emperor (👑) - Golden Cup Maharaja
   - Character equip system updates the user avatar, saves to state, and reflects on leaderboards.

---

## 🎮 Game Engine & Infinite Progression

1. **Infinite Level Scaling (1 to 150+ to Infinity)**:
   - Level generation algorithm: Deterministic seeded scramble `rng(n * 7919 + k * 104729)`.
   - Guaranteed Solvability: Evaluated using an embedded A* solver (`solveMove`).
   - Dynamic Fallback: If after 25 seed iterations a locked tray creates a choke point, gracefully relax the lock (`lock = -1`). If still unsolved after 45 iterations, generate a mathematically guaranteed reverse-pour solvable puzzle. 0% generation failure rate.
   - Ultra-Fast Generation: Levels generate in under 2ms.

2. **Fair Move Limits on Challenge Levels (`lvl % 4 === 0`)**:
   - Formula: `lim0 = Math.round(c * 6.5 + 8)` (where `c` is the number of colors, capped at 8).
   - Provides 60 generous moves on 8-color puzzles so players never hit an unfair "Out of Moves" failure right before completing their puzzle.

3. **Level Map Navigation & Auto-Sync**:
   - 10 levels per page with previous (◀) and next (▶) pagination.
   - Auto-Sync: Winning a level automatically switches the map page to the player's active level page.
   - Direct Jump Button: When browsing earlier pages, a "🎯 वर्तमान लेवल पर जाएँ (Jump to Current Level)" button instantly brings the player back to their highest unlocked level.

4. **13-Tier Visual Stages & Infinite Prestige Loop**:
   - Progressive tapri visual upgrades:
     * Levels 1–2: ठेला (Thela Cart)
     * Levels 3–5: छोटी टपरी (Small Tapri)
     * Levels 6–9: सजी टपरी (Decorated Tapri)
     * Levels 10–14: बड़ी टपरी (Big Tapri)
     * Levels 15–20: चाय कैफ़े (Chai Cafe)
     * Levels 21–29: फ़ूड स्ट्रीट (Food Street)
     * Levels 30–44: मेगा कैफ़े लाउंज (Mega Cafe Lounge)
     * Levels 45–59: रॉयल टी एस्टेट (Royal Tea Estate)
     * Levels 60–79: मेट्रो चाय हब (Metro Chai Hub)
     * Levels 80–99: नेशनल टी नेटवर्क (National Tea Network)
     * Levels 100–124: गोल्डन टी एम्पायर (Golden Tea Empire)
     * Levels 125–149: ग्लोबल फ़्रेंचाइज़ी (Global Franchise)
     * Level 150+: चाय सम्राट महातीर्थ & Supreme Empire ⭐ Prestige 1, 2, 3...
   - SVG visual background clamps gracefully so customer counts never produce `undefined` or `NaN` errors at high levels.

5. **2x Snappy Gameplay Physics**:
   - Tray tap transition: `0.08s` with `cubic-bezier(0.2, 0.9, 0.3, 1)`.
   - Chai item fly duration: `130ms` with parabolic bezier curve and `25ms` per-item stagger.
   - Confetti animation: `1.5s` duration for instant celebration.
   - Fail-Safe Level Win Guarantee: Upon winning, client local state immediately increments `S.level++` and persists rewards, ensuring clicking "Next Level" always reliably advances to the next level.

---

## 🏆 100% Real-Time Worldwide Leaderboard

1. **Zero Fake / Dummy / Seeded Players**:
   - Absolute rule: Remove all pre-seeded fake player names (no dummy seeds like Aarav, Priya, Rohan, etc.).
   - Initial leaderboard count is strictly 0.
   - Only genuine players who register by entering their name appear on the leaderboard.

2. **Real-Time Dynamic Synchronization**:
   - When a player registers, their profile enters the leaderboard with name, avatar, 0 stars, and level 1.
   - As the player clears levels, their stars and level update in real-time on both local storage and cloud database.
   - Strict ranking order: sorted primarily by stars descending (`b.st - a.st`), and secondarily by level descending (`b.lv - a.lv`).

3. **Dynamic 3D Olympic Spatial Podium & Cards**:
   - **0 Players State**: Attractive empty card inviting the player: *"अभी कोई रियल खिलाड़ी नहीं है! अपना नाम डालकर खेलें और #1 रैंक हासिल करें!"*
   - **1–2 Players State**: Displays real players on the podium. Unoccupied podium pedestals show a clean, dashed open slot (*"खाली स्थान / Open"*).
   - **3+ Players State**: Displays top 3 players on Gold (🥇 1st - center & tallest with crown 👑), Silver (🥈 2nd - left), and Bronze (🥉 3rd - right) 3D pedestals showing real name, avatar, `⭐ Stars · लेवल Level`. Players ranked #4 onwards appear in the scrollable card feed below.
   - Active User Badge: Logged-in user is prominently highlighted with an emerald green `आप / You` badge on their card and podium spot.

---

## 🛡️ Production Security Hardening & AI Vibe-Coding Defenses

1. **Zero Plain-Text Credentials**:
   - Client-side offline storage uses salted SHA-256 (`name:pin:tapri_salt_2026`).
   - Cloud backend uses Node.js `crypto.scryptSync(pin, salt, 32)` with unique 16-byte cryptographic random salts.

2. **Dotfile & Sensitive Config Protection**:
   - `vercel.json` and `server.js` enforce strict HTTP 403 Forbidden on `/.git`, `/.env`, and hidden dotfiles.

3. **Anti-Account Takeover & Device Ownership Token**:
   - Registration assigns a unique cryptographic `ownerToken`.
   - PIN resets require either verified device ownership or a matching personal secret recovery word (`secHash`). Unauthorized resets from unknown devices are rejected.

4. **Exponential Backoff Rate Limiting & Admin Audit Logger**:
   - Failed authentication attempts trigger exponential lockouts (5s, 15s, 45s, 120s).
   - Suspicious activity is logged into an immutable in-memory/localStorage audit trail (`tapri_admin_audit`).

---

## 🚀 Server Architecture & Deployment

1. **Node.js Server (`server.js`)**:
   - Native `http` server (zero heavy frameworks).
   - Serves static files with correct MIME types.
   - SPA fallback: unmatched routes serve `index.html`.
   - Antideploy health endpoint: `/health` returns `{ status: 'ok', uptime: ... }`.
   - Forwards `/api` requests to `./api/index.js`.

2. **Vercel Serverless Function (`api/index.js`)**:
   - Handles `/api` POST actions: `reg`, `login`, `win`, `skip`, `lead`, `change_pin`, `reset_pin`.
   - Stores users and global leaderboard in private Vercel Blob storage (`u/<hash>.json` and `u/global_leaderboard.json`).
   - Implements in-memory IP rate limiting (120 req/min) and high-speed in-memory leaderboard cache (15s TTL).

---

## 📦 Deliverables Checklist
Ensure all files are generated with complete, clean, un-truncated code, passing all syntax tests without missing closing tags, broken braces, or placeholders.
```
