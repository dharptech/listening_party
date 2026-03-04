# 🎵 Listening Party

A real-time multiplayer music game where players compete to control what plays next.

Built by [Duane Harper](https://www.linkedin.com/in/duaneharper/)

---

## What is it?

Listening Party is a browser-based party game for groups. One person hosts a room on a device with good speakers — everyone else joins from their phones. Players submit YouTube links, and when enough people vote with their own submission, the current song gets cut and the earliest pick wins. Points are awarded based on how long your song survived, and strategy emerges around when to submit, what to play, and whether to risk skipping your own song.

No accounts. No installs. Just open a link.

---

## How to play

### Setup
1. The host opens the app and clicks **Host a room**
2. Share the room code or copy the invite link — friends open it on their phones and enter their name to join
3. Anyone can submit a YouTube link to start the first song — first submission plays immediately

### Scoring

| Situation | Cutter | DJ (current song owner) |
|-----------|--------|------------------------|
| Cut at 0–66% | +3 pts | +0 pts |
| Cut at 66–90% | +2 pts | +1 pt |
| Cut at 90–100% | +1 pt | +2 pts |
| Song plays all the way through | — | +3 pts |
| Consecutive songs (same player goes again) | — | +6 pts instead of 3 |
| You cut your own song | -3 pts | — |
| Your song gets self-cut | — | Everyone else with a pick queued gets +3 |

### Cut rules
- A cut triggers when **majority of non-DJ players** have submitted a next song
- In a 2-player game: 1 submission cuts immediately
- In a 3-player game: 2 submissions needed
- The **earliest** submission wins — timing matters
- The DJ can queue their next song but it doesn't count toward the cut threshold

---

## Host Only mode

Toggle **Host Only** on the host screen to run the game on a dedicated speaker device (TV, laptop, PC). In this mode:

- The host is not added as a player
- No submission UI — the host just plays audio
- Full-screen Now Playing with the leaderboard below
- Everyone plays from their own phones

---

## Features

- 🎬 YouTube playback with real-time progress sync
- 🔗 Join by link — share a URL, no code typing required
- 🌙 Dark mode by default, toggleable
- 💾 Persistent sessions — switching tabs to grab a link won't drop you from the game
- 📱 Mobile-friendly
- ♥ YouTube Music button to save songs you hear

---

## Tech stack

- Vanilla HTML/CSS/JS — single file, no build step
- [Firebase Realtime Database](https://firebase.google.com/products/realtime-database) for multiplayer sync
- [YouTube IFrame API](https://developers.google.com/youtube/iframe_api_reference) for playback
- Hosted on [GitHub Pages](https://pages.github.com/)

---

## Running locally

Because YouTube embeds require an HTTP origin (not `file://`), you need a local server:

```bash
# Python 3
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

---

## Firebase setup

If you're forking this and want your own backend:

1. Create a project at [firebase.google.com](https://firebase.google.com)
2. Add a Realtime Database (start in test mode)
3. Replace the `firebaseConfig` object near the top of `index.html` with your own config
4. Set your database rules to allow read/write:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

---

## License

MIT — do whatever you want with it.
