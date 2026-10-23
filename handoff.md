# Word Hunt — Handoff

_Last updated: Friday, October 23, 2026_

An endless, GamePigeon-style Word Hunt that runs in any browser and is meant to become a Telegram Mini App.

## Done

- **Game built and playable.** Swipe or type to find words; 80 s, 2 min and Zen rounds on 4×4 or 5×5; end-of-round word list with paths; "Play specific letters"; best scores saved per device.
- **Startup bug fixed (Oct 23).** The "Play specific letters" box showed on load and swallowed typing. Pop-ups now stay hidden until opened, and typing in a textbox goes into the textbox.
- **Published.** Repo: https://github.com/elmopaciencia-tech/word-hunt (public, branch `main`). Live: https://elmopaciencia-tech.github.io/word-hunt/ via GitHub Pages. `index.html` includes the ENABLE dictionary and Telegram's Mini App script.

- **Redesign (Oct 23).** White, Duolingo-style look; tiles turn blue/green/yellow while dragging (no red until release); chime/beep sounds; Sound and Vibration switches; clearer end-screen word lists; bigger score/time.
- **Challenge links (Oct 23).** Every board has a short code that produces the same letters on every device. After a round, "Challenge a friend" shares a link with the board, timer and your score. Whoever opens it sees a face-down board, presses Start, gets a 3-2-1 countdown, then a You-vs-them result and can send their score back. Works in groups (everyone gets the same board). No server: scores travel inside the link, so they're on the honour system.

## Left to do

| # | Task | Who | Notes |
|---|------|-----|-------|
| 1 | Check the live page on your phone | You | Open the live URL and play a round. |
| 2 | Create the Telegram bot | **You** | In @BotFather send `/newbot`. Keep the token private; this setup doesn't use it. |
| 3 | Attach the game as a Mini App | You | In @BotFather send `/newapp`, choose the bot, and paste the live URL. You get a link like `t.me/<yourbot>/wordhunt`. |
| 4 | Optional: add a Play button in the bot chat | You | `/setmenubutton`, then paste the same URL. |
| 5 | Point challenge links at the Mini App | Claude | Once you have the `t.me/<bot>/<app>` link, Claude sets `TG_APP` in `index.html` so shared challenges open inside Telegram instead of the browser. |

Tasks 2–4 are yours because creating the bot makes a new Telegram account and issues a secret token, which Claude shouldn't create or handle.

## Known gaps

- **Dictionary mismatch.** GamePigeon's word list isn't public. ENABLE will accept some words GamePigeon rejects, and the reverse.
- **Scoring past 8 letters is assumed** to be +400 per extra letter. Up to 8 letters it matches GamePigeon: 100 / 400 / 800 / 1400 / 1800 / 2200.
- **Letter distribution is approximate.** Boards come from Boggle dice, and any board with fewer than 50 words (120 on 5×5) is re-dealt. A Q tile is a plain Q, not "Qu".
- **No shared leaderboards.** Scores stay on each device. Telegram group leaderboards would need a small always-on bot server that calls `setGameScore`.

## Ideas for later

- Swap in a word list closer to GamePigeon's, or let players report "GamePigeon rejected this"
- Daily board (easy now: use the date as the board code)
- Live rooms with a lobby and synced start (needs a small server, e.g. Supabase)
- Telegram leaderboards (needs a hosted bot)
- Shrink the page by gzipping the dictionary (about 1.7 MB down to roughly 500 KB)

## Where things are

- **Local folder:** `/Users/elmo/Desktop/AI/apps/word-hunt` (git repo, tracks `origin/main`)
- **GitHub repo:** https://github.com/elmopaciencia-tech/word-hunt
- **Live URL:** https://elmopaciencia-tech.github.io/word-hunt/
- **Dictionary source:** ENABLE word list ([dolph/dictionary](https://github.com/dolph/dictionary))
