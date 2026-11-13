# Веселе множення! 🤪🤩😎

A fun, kid-friendly **multiplication table learning app** for the 1–10 range, built as a single self-contained HTML file. Everything (markup, styles, logic) lives in **`index.html`** — there are no dependencies, no build step, and no external requests. Just open the file in a browser and play.

The interface is in **Ukrainian**. On desktop it looks like a **16:9 presentation** (a fixed 1280×720 "stage" that scales to fit the screen); on tablets and phones it becomes a fluid, full-height, scrollable layout with large touch targets. Everything is operated with the **mouse or touch — no keyboard needed**.

## Features

Four tabs (views), switchable from the top bar:

| # | Tab | What it does |
|---|-----|--------------|
| 1 | **📚 Класична** | The main page. All 10 multiplication tables (1 × 1 … 10 × 10) shown at once in a **2 rows × 5 columns** grid. Each table is a small card listing `n × 1` … `n × 10` in one column. Rows highlight on hover. |
| 2 | **🔢 Піфагора** | The big interactive 11×11 **color grid** (the "Pythagorean table"). Hover a number and its whole row + column light up; cell color shows how large the answer is. |
| 3 | **🎯 Тренування** | **Practice one number.** Pick a number 1–10 and a question count (3 / 5 / 10 / 15 / 20, default 10), then answer one question at a time: each shows **5 answer buttons** and only one is correct — tap it for instant right/wrong feedback. An optional **cheat sheet** (that number's table) can be toggled on/off. |
| 4 | **🎲 Тестування** | **Quick quiz.** Pick a question count (default 10) and get a random set of examples from the whole table (factors 2–9), answered the same tap-a-button way. |

Each round ends with a **score summary**: stars, a score circle (`right / total`), a friendly message, and a review list of the examples to repeat. Sound effects (WebAudio) can be muted with the speaker button.

## Getting started

There is nothing to install or build.

```bash
# Option 1: just open the file
open index.html            # macOS
xdg-open index.html        # Linux
# ... or double-click index.html in your file manager

# Option 2 (optional): serve it locally
python3 -m http.server 8000
# then visit http://localhost:8000
```

That's it. The app works fully offline.

## Using the app

1. **Класична** — browse all tables; hover (or tap) any row to see it highlight.
2. **Піфагора** — hover (or tap) any cell to light up its row and column and read the answer.
3. **Тренування** — pick a number, pick how many questions (default 10), press **🚀**, then **tap the correct answer** from the 5 options on each question. Tap **Наступне →** to continue. Toggle **👀 Шпаргалка** to reveal/hide the cheat sheet.
4. **Тестування** — pick a question count (default 10) and press **🚀** for a random mixed round, answering the same way.

After a round you can **Повторити** (play again), change the number/count, or stop.

## Editing the text

All Ukrainian strings are gathered in **one place** — the `const T = { … }` block near the top of the `<script>` section in `index.html`, marked:

```
/* ================= УКРАЇНСЬКІ ФРАЗИ — EDIT ALL THE TEXT HERE ================= */
```

To change any phrase, edit the matching line, save, and reload the page. Placeholders available in some strings:

| Placeholder | Meaning |
|-------------|---------|
| `{n}` | a number (1…10) |
| `{a}`, `{b}` | the two numbers in a question |
| `{ans}` | the correct answer |
| `{k}` | current question number |
| `{total}` | total questions in the round |
| `{r}`, `{c}` | row / column (used in the big table) |

The strings are pushed into the page by `applyStrings()`, and dynamic ones are filled by `fill(str, {…})`.

## Technical notes

- **Single file** — `index.html` is the entire app.
- **Responsive layout** — a fixed 1280×720 stage scaled with `transform: scale()` on wide screens; below 900px it switches to a fluid, full-height, scrollable layout (3→2-column table grid, wrapping answer buttons, stacked cheat sheet) for tablets and phones.
- **Pointer only** — answers are picked by tapping one of 5 buttons, so no keyboard is required (Enter still works as a shortcut to advance).
- **No dependencies** — no frameworks, fonts, or network calls.
- **Sounds** are generated with the Web Audio API; toggle with the speaker icon.

## Project structure

```
.
├── index.html   # the whole app (markup + CSS + JS)
└── README.md    # this file
```
