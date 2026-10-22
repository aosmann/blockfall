# Blockfall

Educational block puzzle for the EduGames portal. An 8×8 board, a question card above it with three answers, and a tray of pieces below. Every tray of three pieces is earned with a question.

- Right answer: +1 point, the streak grows, and you **choose** your next tray from two trays of 3 pieces
- Wrong answer: the right answer shows, the streak resets, and you get **one random tray** that leans towards awkward shapes (long bars, big L's, 3×3 squares)
- Drag the pieces onto the board. A ghost shows where the piece lands and which rows and columns it would clear. When all 3 are placed, the next question appears
- Lines: 1 line = 10 points; several at once pay more (2 → 30, 3 → 60, 4 → 100); clears on back-to-back placements add 50% per link (combo)
- Streaks: 3 right in a row = ×2 line points, 5 = ×3. Every 5th right answer in a row also earns a **bomb**: drop it on any cell to blast a 3×3 area
- The run ends when no piece left in the tray fits anywhere (the pieces are marked), when the timer ends, or when you end it from pause
- Easy / Medium / Hard: harder levels put more awkward pieces in random trays. On Easy a random tray always has at least one piece that fits; offered trays always do
- Time: no limit (the clock counts up), 2 min or 5 min. Record kept per topic, difficulty and time

## Controls
- Touch or mouse: drag a piece from the tray onto the board. On touch the piece is lifted above your finger so you can see where it goes. Let go over a highlighted spot to place it; anywhere else it flies back
- Tap a tray to pick it after a right answer
- Keyboard: 1 / 2 / 3 answers the question (1 / 2 also picks a tray). Esc or P pauses

Plain canvas 2D, no build step, works offline after the first visit, installs to the home screen. Portrait first (question card, board and tray fit a 390×844 phone without scrolling); iPad and laptop too, with the board beside the card on wide screens. Fills the visible screen with 100dvh.

## Files
- `index.html`: the game (board, pieces, trays, drag, scoring, menus, audio, PORTAL EMBED block)
- `questions.js` and `flags/`: the shared EduQ question bank (v3), byte-identical to Hoopfall's copy. Do not edit here
- `game.json`: portal metadata and teacher settings (level, time)
- `sw.js`, `manifest.webmanifest`, `icon-*.png`: offline support (including every flag) and install

## Portal
Follows the EduGames game contract v1: `?topic=<id>&level=1-3&time=0|120|300&regions=eu,as&lock=1` starts a run at once; posts `edu-ready`, `edu-progress` after every answer and `edu-result` at the end (also kept in `localStorage['edu-results']`). The result adds `lines`, `timeUsed` (seconds played), `cause` (`stuck` / `time` / `quit`), `time`, `pieces`, `bestCombo` and `bombs` (bombs used).

`?debug=1` exposes a `window.BF` hook used by the automated tests.

## Credits

Country, capital and continent data: [mledoze/countries](https://github.com/mledoze/countries), Open Database License (ODbL 1.0).  
Flags: [flag-icons](https://github.com/lipis/flag-icons), MIT licence, compressed into `flags/`.
