# Availability Finder

A lightweight tool that reads your Outlook calendar (.ics export) and generates a clean list of your available time slots. Built as a Progressive Web App — works in the browser and can be installed on desktop or mobile.

## Features

- **Import .ics files** from Outlook, Google Calendar, or Apple Calendar via drag-and-drop
- **Set working hours** so it never shows times outside your bounds
- **Single day or date range** queries
- **Buffer time** between events (5–30 min)
- **Minimum slot duration** filter (15 min, 30 min, 1 hour)
- **Smart grouping** — when you copy a week's availability, days with identical schedules are grouped together (e.g. "Monday, Wednesday, and Friday:")
- **One-click copy** — copies only your free times, never your event details
- **Works offline** — full PWA with service worker caching
- **Installable** — add to home screen on mobile, or install as a desktop app from your browser
- **Settings persist** between sessions via localStorage

## Quick Start

### Option 1: Use online (GitHub Pages)

1. Visit **[AlexaGonzalesTuesta.github.io/availability-finder](https://AlexaGonzalesTuesta.github.io/availability-finder)**
2. Export your calendar as an .ics file ([how-to guide below](#exporting-from-outlook))
3. Drag the .ics file into the app
4. Pick a date and click **Find Free Times**

### Option 2: Install as a desktop/mobile app

1. Visit the GitHub Pages link above
2. In Chrome: click the install icon (⊕) in the address bar
3. In Safari (iOS): tap Share → Add to Home Screen
4. The app now runs standalone, even offline

### Option 3: Run locally

```bash
git clone https://github.com/AlexaGonzalesTuesta/availability-finder.git
cd availability-finder
# Any static file server works:
python3 -m http.server 8000
# Then open http://localhost:8000
```

## Exporting from Outlook

**First time (~30 seconds):**

1. Go to [Outlook Web → Shared Calendars Settings](https://outlook.live.com/calendar/0/options/calendar/SharedCalendars)
2. Under **"Publish a calendar"**, select your calendar → set to **"Can view all details"**
3. Click **Publish**
4. Right-click the **ICS** link → **Save link as...** to download the .ics file
5. Drag it into the app

**Every time after (~5 seconds):**

Bookmark the ICS download link. Click it → drag the new file into the app. Done.

## Deploying to GitHub Pages

1. Create a new repository on GitHub (e.g. `availability-finder`)
2. Push this project to it:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/AlexaGonzalesTuesta/availability-finder.git
   git push -u origin main
   ```
3. Go to **Settings → Pages** in your repo
4. Under **Source**, select **Deploy from a branch** → **main** → **/ (root)**
5. Click **Save**
6. Your app will be live at `https://AlexaGonzalesTuesta.github.io/availability-finder` within a minute

## How the Copy Grouping Works

When you query a date range, the copy button intelligently groups days with identical availability:

**Instead of:**
```
Available on Monday, April 6:
- Available anytime before 10:20am
- 1:25pm – 4:20pm
- Available anytime after 5:30pm

Available on Wednesday, April 8:
- Available anytime before 10:20am
- 1:25pm – 4:20pm
- Available anytime after 5:30pm

Available on Friday, April 10:
- Available anytime before 10:20am
- 1:25pm – 4:20pm
- Available anytime after 5:30pm
```

**You get:**
```
Monday, April 6, Wednesday, April 8, and Friday, April 10:
- Available anytime before 10:20am
- 1:25pm – 4:20pm
- Available anytime after 5:30pm
```

## Project Structure

```
availability-finder/
├── index.html      ← The entire app (single file, no build step)
├── manifest.json   ← PWA manifest (app name, icons, theme)
├── sw.js           ← Service worker (offline caching)
├── icons/
│   ├── icon.svg    ← Vector icon
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## Tech Stack

- Vanilla HTML/CSS/JS — no frameworks, no dependencies, no build step
- Segoe UI typography (Microsoft Fluent design language)
- PWA with service worker for offline support
- localStorage for settings and calendar data persistence

## License

MIT
