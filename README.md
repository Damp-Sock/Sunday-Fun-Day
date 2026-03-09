# Sunday Fun Day — Mission Vote Poll

A full-stack mission voting system for the **Grim Reapers DCS World** Sunday Funday sessions. Players vote on their top 3 missions from a pool of 33, votes are tallied in real time via Google Sheets, and results are displayed on a live leaderboard.

**Live site:** [tinyurl.com/Sunday-Fun-Day-Vote](https://tinyurl.com/Sunday-Fun-Day-Vote)

---

## Features

- **33 missions** organized by category — Regular, Special Events, and Upcoming
- **Select up to 3 missions** per player with a one-vote-per-browser enforcement via localStorage
- **TSD-style mission brief panel** — slides in from the right with full mission description, theater, era restrictions, helicopter requirements, and rounds
- **Live leaderboard** powered by Google Sheets as a backend database via Apps Script
- **Timestamps** on every vote for session tracking
- **Admin panel** with PIN-protected archive and reset — previous week's votes are preserved in a dated archive tab, never deleted
- **HUD / MFD aesthetic** inspired by the F/A-18C Hornet TSD display

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript (vanilla) |
| Backend | Google Apps Script (Web App) |
| Database | Google Sheets |
| Hosting | GitHub Pages |
| URL | TinyURL |

---

## How It Works

1. Player opens the poll URL and selects up to 3 missions
2. On submission, the vote is sent via `fetch()` POST to a Google Apps Script Web App endpoint
3. The Apps Script increments vote counts and logs a timestamp in Google Sheets
4. The Live Results tab pulls the current tallies via GET request and renders the ranked leaderboard
5. Before each Sunday session, the admin archives the current results and resets the poll via the Admin tab

---

## File Structure

```
sunday-funday-poll.html   — Full application (single file)
Code.gs                   — Google Apps Script backend (deploy separately)
```

---

## Setup

### 1. Google Sheets Backend

- Create a new Google Sheet
- Go to **Extensions → Apps Script**
- Paste the contents of `Code.gs` and save
- Click **Deploy → New Deployment → Web App**
  - Execute as: Me
  - Who has access: Anyone
- Copy the Web App URL

### 2. Configure the HTML

Open `sunday-funday-poll.html` and replace the URL on this line:

```javascript
const APPS_SCRIPT_URL = "YOUR_APPS_SCRIPT_URL_HERE";
```

### 3. Deploy

Upload `sunday-funday-poll.html` to any static hosting provider. This project uses GitHub Pages.

### 4. Admin Reset PIN

The default PIN is set in `Code.gs` on the `RESET_PIN` line. Change it before deploying.

---

## Screenshots

> DCS World — Grim Reapers Sunday Funday | Built for the squad, by the squad.
