# Blockfall

Educational falling-blocks game for the EduGames portal. The questions drive the game: a block falls from the top of an 8×12 board while the question shows just above the answers, and your answer decides where the block lands. You never move the blocks yourself.

- Right answer: +1 point and the block glides into the best spot on the board and snaps in. Answer within the first part of its fall for +1 more (Quick)
- Wrong answer: the block lands somewhere random (on Hard it leans towards the worse spots) and the right answer shows
- No answer before it lands: it lands wherever it was falling, counted as a miss ("too slow"). The higher the stack, the less time you have
- Full rows clear: 1 row = 10 points, 2 at once = 30, 3 = 60, 4 = 100; clears on back-to-back blocks add 50% per link (combo)
- Streaks: 3 right in a row = ×2 line points, 5 = ×3. Every 5th right answer in a row also sweeps away the bottom row
- Chess clock (as in Slicefall): start with 10 s. The clock only runs while a block is falling with its question open. Right answers add time, wrong or unanswered ones take it away: Quick +1 s / −1 s, Normal +2 / −2, Relaxed +3 / −2. The clock holds at most 15 s, and the bonus shrinks by 0.5 s every 8 right answers (never below 0.5 s)
- The run ends when the clock hits zero, when the stack reaches the top, or when you end it from pause
- Easy / Medium / Hard: blocks fall the whole board in about 15 / 11 / 8 seconds, a little faster every 10 lines
- Record kept per topic, difficulty and clock

## Controls
- Tap or click one of the three answer buttons under the board
- Keyboard: 1 / 2 / 3 answers. Esc or P pauses

Plain canvas 2D, no build step, works offline after the first visit, installs to the home screen. Portrait first (board, question card and answers fit a 390×844 phone without scrolling); iPad and laptop too, with the board beside the card on wide screens. Fills the visible screen with 100dvh.

## Files
- `index.html`: the game (board, falling pieces, placement, scoring, menus, audio, PORTAL EMBED block)
- `questions.js` and `flags/`: the shared EduQ question bank (v3), byte-identical to Hoopfall's copy. Do not edit here
- `game.json`: portal metadata and teacher settings (level, clock)
- `sw.js`, `manifest.webmanifest`, `icon-*.png`: offline support (including every flag) and install

## Portal
Follows the EduGames game contract v1: `?topic=<id>&level=1-3&clock=quick|normal|relaxed&regions=eu,as&lock=1` starts a run at once; posts `edu-ready`, `edu-progress` after every answer and `edu-result` at the end (also kept in `localStorage['edu-results']`). The result adds `lines`, `timeUsed` (seconds played), `cause` (`time` / `topout` / `quit`), `clock`, `pieces`, `slow` (blocks that landed unanswered, also counted in `asked` and `missed` with `picked: "(no answer)"`), `quick`, `bestCombo` and `sweeps`.

`?debug=1` exposes a `window.BF` hook used by the automated tests.

## Credits

Country, capital and continent data: [mledoze/countries](https://github.com/mledoze/countries), Open Database License (ODbL 1.0).  
Flags: [flag-icons](https://github.com/lipis/flag-icons), MIT licence, compressed into `flags/`.
