# Availability Finder

A lightweight tool that reads your calendar (.ics export) and generates a clean list of your available time slots. Built as a Progressive Web App — works in the browser and can be installed on desktop or mobile.

## Use It Now

**[alexagonzalestuesta.github.io/availability-finder](https://alexagonzalestuesta.github.io/availability-finder)**

No account, no install, no setup. Just open the link and import your calendar.

Quick Demo Video:

https://github.com/user-attachments/assets/1d9f3115-c702-4dcb-87b6-0828a8e4f0c2

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
- **Settings persist** between sessions automatically

## How to Use

### Step 1: Export your calendar

1. Open [Outlook Web → Shared Calendars Settings](https://outlook.live.com/calendar/0/options/calendar/SharedCalendars)
2. Under **"Publish a calendar"**, select your calendar → set to **"Can view all details"**
3. Click **Publish**
4. Right-click the **ICS** link → **Save link as...** to download the .ics file

> **Tip:** Bookmark the ICS download link. Next time you just click it to download a fresh copy — takes 5 seconds.

### Step 2: Import into the app

1. Open the [Availability Finder](https://alexagonzalestuesta.github.io/availability-finder)
2. Drag your .ics file into the drop zone (or click to browse)
3. Set your working hours (e.g. 8:00am – 9:00pm)
4. Pick a date or date range and click **Find Free Times**
5. Click **Copy** to grab your availability and paste it into a message

### Install as an app (optional)

- **Chrome (desktop):** Click the install icon in the address bar to pin it as a standalone app
- **Safari (iOS):** Tap Share → Add to Home Screen
- **Android:** Tap the "Add to Home Screen" prompt

## How the Copy Grouping Works

When you query a date range, the copy button intelligently groups days with identical availability.

Instead of listing Monday, Wednesday, and Friday separately with the same times, you get:

```
Monday, April 6, Wednesday, April 8, and Friday, April 10:
- Available anytime before 10:20am
- 1:25pm – 4:20pm
- Available anytime after 5:30pm
```

This makes it easy to paste into a message without overwhelming the recipient.

## Deploying Your Own Copy

Want to host your own version? Fork this repo, then:

1. Go to **Settings → Pages** in your forked repo
2. Under Source, select **Deploy from a branch → main → / (root)**
3. Click **Save**
4. Your copy will be live at `your-username.github.io/availability-finder` within a minute

Or run it locally:

```bash
git clone https://github.com/AlexaGonzalesTuesta/availability-finder.git
cd availability-finder
python3 -m http.server 8000
# Open http://localhost:8000
```

## Tech Stack

- Vanilla HTML/CSS/JS — no frameworks, no dependencies, no build step
- Segoe UI typography (Microsoft Fluent design language)
- PWA with service worker for offline support
- localStorage for settings and calendar data persistence

## License

MIT
