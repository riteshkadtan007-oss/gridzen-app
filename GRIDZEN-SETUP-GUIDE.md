# GridZen — Complete Publishing Guide
## GitHub + AdMob Ads + Play Store

---

## WHAT YOU HAVE
```
gridzen-final.html   ← Your complete game (1 file)
```
That's it. One file = full game. Let's publish it.

---

# PART 1 — GITHUB SETUP (Free, 10 mins)

## Step 1 — Create Repository
1. Go to github.com → Sign in
2. Click "+" (top right) → "New repository"
3. Name: gridzen-app
4. Set to: PUBLIC
5. Check ✅ "Add a README file"
6. Click "Create repository"

## Step 2 — Upload Your Game File
1. In your new repo, click "Add file" → "Upload files"
2. Drag gridzen-final.html into the box
3. Change the commit message to: "Initial GridZen release"
4. Click "Commit changes"

## Step 3 — Enable GitHub Pages (Free Hosting!)
This lets you test your game on any phone browser before publishing.
1. Go to repo → Settings (top tab)
2. Click "Pages" (left sidebar)
3. Under "Branch" select: main
4. Click Save
5. Wait 2 mins
6. Your game is now LIVE at:
   https://YOUR-USERNAME.github.io/gridzen-app/gridzen-final.html

Test this URL on your Android phone right now!

---

# PART 2 — ADMOB ADS SETUP (Free, 30 mins)

AdMob is Google's ad network. It pays you money every time users see ads.

## Step 1 — Create AdMob Account
1. Go to: admob.google.com
2. Sign in with your Google account
3. Fill in your details:
   - Country: India
   - Currency: INR
   - Time zone: India Standard Time
4. Click "Create AdMob account"

## Step 2 — Add Your App
1. Click "Apps" → "Add app"
2. Platform: Android
3. "Is the app listed on a supported app store?" → NO (not yet)
4. App name: GridZen
5. Click "Add app"
6. SAVE your App ID — looks like:
   ca-app-pub-XXXXXXXXXXXXXXXX~XXXXXXXXXX

## Step 3 — Create Ad Units
You need TWO ad units:

### Banner Ad (shown at top/bottom always)
1. Click your app → "Ad units" → "Add ad unit"
2. Choose: Banner
3. Name: GridZen_Banner
4. Click "Create ad unit"
5. SAVE the Ad Unit ID — looks like:
   ca-app-pub-XXXXXXXXXXXXXXXX/XXXXXXXXXX

### Interstitial Ad (full screen between levels)
1. Click "Add ad unit" again
2. Choose: Interstitial
3. Name: GridZen_Interstitial
4. Click "Create ad unit"
5. SAVE this Ad Unit ID too

## Step 4 — Add Your Real Ad IDs to the Game

Open gridzen-final.html in a text editor.
Find these two lines (search for "BANNER AD"):

REPLACE:
  📢 BANNER AD — AdMob 320×50

WITH your actual AdMob HTML ad code (AdMob gives you this code).

FOR FLUTTER (when we convert):
Replace test IDs with your real IDs:
  _bannerAdUnitId = 'ca-app-pub-YOUR-REAL-ID/YOUR-UNIT-ID'
  _interstitialAdUnitId = 'ca-app-pub-YOUR-REAL-ID/YOUR-UNIT-ID'

## Step 5 — Test IDs (Use While Testing!)
NEVER use real ad IDs during testing. Use these Google test IDs:
  Banner:        ca-app-pub-3940256099942544/6300978111
  Interstitial:  ca-app-pub-3940256099942544/1033173712
Switch to real IDs ONLY when submitting to Play Store.

---

# PART 3 — CONVERT TO ANDROID APK (Free, 1 hour)

We use TWA (Trusted Web Activity) — Google's official way to
wrap a website into an Android app. 100% free. 100% allowed on Play Store.

## Step 1 — Install Node.js
Go to: nodejs.org
Download "LTS" version for Mac
Install it (just click Next, Next, Install)
Open Terminal and type: node --version
Should show: v20.x.x ✅

## Step 2 — Install Bubblewrap (Google's TWA tool)
Open Terminal, type:
  npm install -g @bubblewrap/cli

## Step 3 — Initialize Your App
In Terminal:
  mkdir gridzen-twa
  cd gridzen-twa
  bubblewrap init --manifest https://YOUR-USERNAME.github.io/gridzen-app/manifest.json

## Step 4 — Create Web App Manifest
In your GitHub repo, create a new file called manifest.json:

{
  "name": "GridZen",
  "short_name": "GridZen",
  "description": "Block puzzle game. Place blocks, clear lines, find your zen.",
  "start_url": "/gridzen-app/gridzen-final.html",
  "display": "standalone",
  "background_color": "#08081a",
  "theme_color": "#08081a",
  "orientation": "portrait",
  "icons": [
    {
      "src": "icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}

## Step 5 — Build APK
  bubblewrap build

This creates: app-release-signed.apk
That's your Android app file!

---

# PART 4 — CREATE APP ICON (Free, 15 mins)

You need icons in these sizes:
  192x192 px  → For web manifest
  512x512 px  → For Play Store
  1024x1024   → High res Play Store icon

## Free tool: Use Canva (canva.com)
1. New design → Custom size → 1024x1024
2. Background color: #08081a (dark navy)
3. Add emoji: 🧩 (puzzle piece)
4. Add text: "GridZen" in bold
5. Export as PNG
6. Resize to 512x512 and 192x192 using:
   imageresizer.com (free, browser-based)

---

# PART 5 — PLAY STORE PUBLISHING ($25 one-time)

## Step 1 — Create Developer Account
1. Go to: play.google.com/console
2. Sign in with Google account
3. Pay one-time fee: $25 USD (~₹2,100)
4. Fill developer profile

## Step 2 — Create New App
1. Click "Create app"
2. App name: GridZen
3. Default language: English
4. App or Game: GAME ✅
5. Free or Paid: FREE ✅
6. Click "Create app"

## Step 3 — Fill Store Listing
Copy-paste these:

SHORT DESCRIPTION (80 chars max):
  Place blocks, clear lines, find your zen. Free puzzle game!

FULL DESCRIPTION:
  GridZen is the ultimate block puzzle game that's easy to learn
  but hard to master.

  🎮 HOW TO PLAY
  Drag and drop colorful blocks onto the grid. Clear complete rows
  and columns to earn points and advance through levels.

  🌍 4 AMAZING WORLDS
  ✅ Zen Valley — peaceful beginner levels
  💎 Crystal Caves — medium difficulty
  ⚡ Sky Citadel — hard challenges
  🔮 Neon Abyss — expert puzzles

  ✨ FEATURES
  • 60 levels across 4 worlds
  • Special blocks: Bomb 💣 Lightning ⚡ Wild 🌀
  • Streak system with combo multipliers
  • Daily hint system
  • Reward chests
  • Boss levels every 15 stages
  • Progress saved on your device
  • Play OFFLINE — no internet needed
  • Zero ads during gameplay — only between levels
  • Completely FREE to play

  Perfect for all ages. No time limits. No pressure. Just pure zen.

CATEGORY: Puzzle

CONTENT RATING: Everyone (E)

## Step 4 — Upload Screenshots
Take screenshots of your game on your Android phone:
  - Welcome/Profile screen
  - World map screen
  - Game being played
  - Win screen
  - Special blocks in action
Minimum: 2 screenshots. Ideal: 5-8 screenshots.

## Step 5 — Upload APK
1. Go to "Release" → "Production"
2. Click "Create new release"
3. Upload your APK file
4. Write release notes:
   "Initial release of GridZen — Block Puzzle Game"
5. Click "Save" → "Review release" → "Start rollout"

## Step 6 — Wait for Review
Google reviews your app in 1-7 days.
You'll get an email when it's approved.

---

# PART 6 — ADMOB EARNINGS ESTIMATE

Based on India market rates:

DAILY ACTIVE USERS    DAILY EARNINGS (approx)
100 users           → ₹50–₹150/day
500 users           → ₹250–₹750/day
1,000 users         → ₹500–₹1,500/day
10,000 users        → ₹5,000–₹15,000/day

How to get users for FREE:
1. Share your Play Store link in WhatsApp groups
2. Post gameplay videos on Instagram Reels
3. Share in Reddit: r/indiegaming, r/AndroidGaming
4. Post in Facebook gaming groups
5. Ask friends and family to install + rate 5 stars

---

# QUICK CHECKLIST

Before submitting to Play Store:
[ ] gridzen-final.html uploaded to GitHub
[ ] GitHub Pages URL works on phone
[ ] manifest.json created in GitHub repo
[ ] App icon created (512x512 PNG)
[ ] AdMob account created
[ ] Ad Unit IDs saved safely
[ ] APK built with Bubblewrap
[ ] Play Store developer account ($25)
[ ] Store listing filled completely
[ ] 5+ screenshots uploaded
[ ] APK uploaded to production

---

# HELP & NEXT STEPS

After launch, tell Claude:
- How many installs you got
- Any bugs users report
- What features users request

Then we build Version 1.1 with:
- Real-time leaderboard (Firebase)
- Daily challenge mode
- More worlds and levels
- Push notifications

Good luck! 🚀 GridZen is going to be amazing.
