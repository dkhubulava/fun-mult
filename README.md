# Веселе множення! 🤪🤩😎

A fun, kid-friendly **multiplication table learning app** for the 1–10 range, built as a single self-contained HTML file. Everything (markup, styles, logic) lives in **`index.html`** — there are no dependencies, no build step, and no external requests. Just open the file in a browser and play.

The interface is in **Ukrainian** and the app is styled as a **16:9 presentation** (a fixed 1280×720 "stage" that scales to fit the screen), designed for **desktop** use.

## Features

Four tabs (views), switchable from the top bar:

| # | Tab | What it does |
|---|-----|--------------|
| 1 | **📚 Класична** | The main page. All 10 multiplication tables (1 × 1 … 10 × 10) shown at once in a **2 rows × 5 columns** grid. Each table is a small card listing `n × 1` … `n × 10` in one column. Rows highlight on hover. |
| 2 | **🔢 Піфагора** | The big interactive 11×11 **color grid** (the "Pythagorean table"). Hover a number and its whole row + column light up; cell color shows how large the answer is. |
| 3 | **🎯 Тренування** | **Practice one number.** Pick a number 1–10 and a question count (3 / 5 / 10 / 15 / 20), then answer one question at a time with instant right/wrong feedback. An optional **cheat sheet** (that number's table) can be toggled on/off. |
| 4 | **🎲 Тестування** | **Quick quiz.** Pick a question count and get a random set of examples from the whole table (factors 2–9), checked one by one. |

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

1. **Класична** — browse all tables, or hover any row to see it highlight.
2. **Піфагора** — hover any cell to light up its row and column and read the answer.
3. **Тренування** — pick a number, pick how many questions, press **Почнемо / 🚀**, then type each answer and press **Перевірити! ✔** (or hit **Enter**). Toggle **👀 Шпаргалка** to reveal/hide the cheat sheet.
4. **Тестування** — pick a question count and press **Почнемо! 🚀** for a random mixed round.

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
- **Presentation layout** — a fixed 1280×720 stage scaled with `transform: scale()` to fit the window; desktop-only by design.
- **No dependencies** — no frameworks, fonts, or network calls.
- **Sounds** are generated with the Web Audio API; toggle with the speaker icon.
- **Keyboard**: **Enter** submits the current answer.

## Project structure

```
.
├── index.html   # the whole app (markup + CSS + JS)
└── README.md    # this file
```
