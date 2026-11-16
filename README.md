# 🏸 Badminton Social — 3 Courts

A single-file web app for running a **large social badminton session** (12–18 players) across **3 courts** at once. Enter everyone with a skill level, and the app keeps all courts busy — balancing teams by skill, rotating partners, and sharing play/rest fairly. Works on any phone; nothing to install.

> Separate app from the 6-player tournament. Different codebase, host it on its own GitHub repo (and its own Firebase project if you use online mode).

---

## How it works

**Setup.** Enter 8–18 players, each with a **skill level: Beginner, Intermediate, or Advanced**. The app uses **1 court per 4 players, up to 3** — so 12–18 players fill 3 courts, 8–11 fill 2. The roster remembers each name *and* its level, so next time you just tap them from the dropdown (level auto-fills).

**The engine.** Each court shows its current 2-vs-2 game with names and levels. When a game ends you enter the score; the app forms the next game with **skill-balanced teams** (strongest + weakest vs the two middles, avoiding repeat partners) and **fair play/rest** (fewest-games-played go on next). It runs in two modes automatically:

- **Continuous (when some players are resting, i.e. 13–18 on 3 courts):** when a court finishes it immediately pulls the next four from the waiting pool — courts never wait for each other, and the rested players rotate on. Everyone mixes well.
- **Round-based (when every court is full with nobody resting, e.g. exactly 12):** a finished court waits until all courts finish, then **everyone reshuffles** into fresh balanced games. This is the only way to mix when there's no rest pool, and it mixes fully. (This is the "Court 1 waits for the others, then re-mix" behaviour.)

**Scoring.** Win = **2 points** per player. Each player keeps their own points (partners rotate). The live standings rank by points, then point differential, then wins.

**End.** A ~90-minute clock runs as a guide. Tap **End session** for the final standings. Highest points wins — no final match.

**Fairness note.** Everyone plays within one game of each other, teams stay competitive, and partners mix well at every count (continuous for 13–18, round-based for 12/8). The only trade-off: in round-based mode a court sits idle between finishing and the round's slowest game ending — that's the cost of full mixing when nobody's resting.

---

## Features

- **3 live courts** with independent scoring and per-game timers.
- **Skill-balanced teams** (Beginner / Intermediate / Advanced) and **fair play/rest** rotation.
- **Add players mid-session** — someone shows up late? Add them in **👥 Players**; they drop into the rotation fairly and a new court opens if the count warrants it.
- **Rest / drop a player** — pause anyone who needs to sit out or leaves; resume them later. Their earlier games still count.
- **Substitutions** — swap a waiting player onto any court before recording; the record credits who actually played.
- **Daily report + all-time leaderboard** — see each day's standings and winner, plus the overall ranking across all sessions.
- **Activity log (tamper record)** — every recorded result, substitution, add/rest/resume is timestamped and logged. You can correct a past score from the history (✎), but the edit is logged and **flagged in red**, so nothing can be quietly changed. The log appears on each session and its daily report.
- Each player shows as **Name (Level)** throughout.
- **Match history**, **live standings**, and an **all-time leaderboard** (total wins across sessions).
- **Player roster** with autocomplete + levels, duplicate-merge, and remove.
- **Online mode (optional)** — Firebase sync so any phone can score from a shared link. Off until you add config; until then it runs offline on one device.
- **Auto-dated** sessions.

---

## Host it (GitHub Pages)

1. Create a **new, public** repo (e.g. `badminton-social`).
2. Upload `index.html` (keep that filename) and optionally these docs.
3. **Settings → Pages → Deploy from a branch → `main` / `/ (root)` → Save.**
4. Live at `https://<your-username>.github.io/badminton-social/`. Open on any phone; **Add to Home Screen** for full-screen.

Works offline out of the box. For live multi-phone scoring, follow `FIREBASE-SETUP.md`.

---

## How to run a session

1. **New Session** → enter names + levels (tap from the dropdown if they've played before) → **Start**.
2. Play the three games shown. When one finishes, enter its score and **Record** — the next four appear on that court automatically.
3. **🔗 Share** (online mode) to let others score from their phones. **Standings** shows the live leaderboard. The **Waiting** panel shows who's up next.
4. Need a swap? **Substitute** on that court before recording.
5. **End session** when the clock's up (or whenever) for final standings.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole app. |
| `README.md` | This file. |
| `FIREBASE-SETUP.md` | Optional online-mode setup. |
