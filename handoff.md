# Word Hunt — Handoff

_Last updated: Friday, October 23, 2026_

An endless, GamePigeon-style Word Hunt that runs in any browser and is meant to become a Telegram Mini App.

## Done

- **Game built and playable**, as a private Claude artifact ("Word Hunt Unlimited").
  - Swipe input with live green/yellow feedback, plus keyboard typing on desktop
  - 80 s, 2 min, and untimed Zen rounds on 4×4 or 5×5 boards
  - End-of-round screen lists every possible word and draws the path for any word you tap
  - "Play specific letters" loads any board, such as one copied from GamePigeon
  - Best score saved per board size and round length, in the browser
- **Standalone `index.html` prepared** for GitHub Pages. It has the ENABLE dictionary embedded (about 1.7 MB, 172k words) and Telegram's Mini App script added (full-screen, haptics, no swipe-to-close).
- **Local git repo committed** with `index.html`, `README.md` and `.nojekyll` (commit `a128266`, branch `main`). It hasn't been pushed yet.

## Left to do

| # | Task | Who | Notes |
|---|------|-----|-------|
| 1 | Create an empty public repo `elmopaciencia-tech/word-hunt` | **You** | Go to [github.com/new](https://github.com/new). Leave README, .gitignore and license unticked. Claude was blocked from creating public repos. |
| 2 | Push the committed game to the new repo | Claude | Say "repo's created" and Claude attaches it and pushes. |
| 3 | Turn on GitHub Pages | **You** (if Claude is blocked) | Settings → Pages → Deploy from a branch → `main` / root → Save. Live in about a minute at `https://elmopaciencia-tech.github.io/word-hunt/`. |
| 4 | Check the live page on your phone | You | Open the Pages URL and play a round. |
| 5 | Create the Telegram bot | **You** | In @BotFather send `/newbot`. Keep the token private; this setup doesn't use it. |
| 6 | Attach the game as a Mini App | You | In @BotFather send `/newapp`, choose the bot, and paste the Pages URL. You get a link like `t.me/<yourbot>/wordhunt`. |
| 7 | Optional: add a Play button in the bot chat | You | `/setmenubutton`, then paste the same URL. |

Tasks 5–7 are yours because creating the bot makes a new Telegram account and issues a secret token, which Claude shouldn't create or handle.

## Known gaps

- **Dictionary mismatch.** GamePigeon's word list isn't public. ENABLE will accept some words GamePigeon rejects, and the reverse.
- **Scoring past 8 letters is assumed** to be +400 per extra letter. Up to 8 letters it matches GamePigeon: 100 / 400 / 800 / 1400 / 1800 / 2200.
- **Letter distribution is approximate.** Boards come from Boggle dice, and any board with fewer than 50 words (120 on 5×5) is re-dealt. A Q tile is a plain Q, not "Qu".
- **No shared leaderboards.** Scores stay on each device. Telegram group leaderboards would need a small always-on bot server that calls `setGameScore`.

## Ideas for later

- Swap in a word list closer to GamePigeon's, or let players report "GamePigeon rejected this"
- Daily seeded board so friends can compare on the same letters
- Telegram leaderboards (needs a hosted bot)
- Shrink the page by gzipping the dictionary (about 1.7 MB down to roughly 500 KB)

## Where things are

- **Repo (local, not yet pushed):** `/home/claude/word-hunt` in Claude's workspace
- **Planned GitHub repo:** `elmopaciencia-tech/word-hunt`
- **Planned live URL:** `https://elmopaciencia-tech.github.io/word-hunt/`
- **Dictionary source:** ENABLE word list ([dolph/dictionary](https://github.com/dolph/dictionary))
