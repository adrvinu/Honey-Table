# 🍯 Honey Table

> A secret puzzle game for lovers — hide a word inside a honeycomb grid that only the right birthday can open.

Honey Table is a single-file, offline web app. One partner hides a short message inside a grid that looks like a jumble of letters and numbers (a honeycomb); the other, knowing the shared **date of birth**, lifts the message back out. To anyone else it's just noise. No server, no accounts, no tracking — everything runs in the browser.

**Short description (for the repo "About" field):**
`Secret honeycomb cipher for lovers — hide messages in a grid unlocked by a date of birth. Single HTML file, runs offline.`

---

## ✨ Features

- **Two inputs, one comb** — a *Honey Key* (date of birth) and a *Honey Word* (your message).
- **Hand-readable rule** — each letter hides at `row = its column's key digit`.
- **Print & download** — export the grid as PNG or print it to share on paper.
- **Hive Code** — copy a compact code for digital sharing and decoding.
- **Solution view** — colour-coded cells (direction / key digits / version / word) for learning.
- **100% offline** — one `.html` file, no dependencies, no network calls.

---

## 🚀 Usage

1. Open `honey-table.html` in any modern browser.
2. **Hide a Secret** — enter the date of birth and the secret word, then *Build the Honeycomb*. Print, download a PNG, or copy the Hive Code.
3. **Reveal a Secret** — paste a Hive Code and enter the matching birthday to read the message.

No build step. No install. Just open the file.

---

## 🧩 How it works

The grid is always **10 rows** (0–9). Columns = `length(word) + 1`.

**Column 0 — the structure column** (read top to bottom):

| Cell | Colour | Holds |
|------|--------|-------|
| Row 0 | 🔵 blue | direction marker |
| Rows 1–8 | 🔴 red | the 8 key digits (date as `DDMMYYYY`) |
| Row 9 | 🟢 green | version number (currently `0`) |

`1 (direction) + 8 (key digits) + 1 (version) = 10` — which is exactly why the comb has 10 rows.

**Placement rule:** every letter gets its own column. The column is labelled with the matching key digit, and the letter sits at the **row equal to that digit**. Words longer than 8 letters reuse the key digits in a cycle.

### Example — key `15-08-1947`, word `HAPPY`

| Letter | Column | Key digit | Lands at |
|:------:|:------:|:---------:|:--------:|
| H | 1 | 1 | row 1 |
| A | 2 | 5 | row 5 |
| P | 3 | 0 | row 0 |
| P | 4 | 8 | row 8 |
| Y | 5 | 1 | row 1 |

**Reading it back:** walk column by column, jumping to the row named by each key digit, and collect the letters. A wrong birthday jumps to the wrong rows and pulls out decoys.

---

## 🔐 Security note

Honey Table is an **obfuscation puzzle, not strong cryptography** — the key digits appear in the comb itself, so its safety rests on a partner knowing the method. For a genuinely private channel, pair it with real encryption (e.g. AES).

---

## 📁 Files

| File | What it is |
|------|------------|
| `honey-table.html` | The complete app (open this) |
| `Honey-Table-Algorithm.pdf` | Illustrated explainer of the algorithm |
| `README.md` | This file |

---

## 📜 License

Free to use and share. 🐝
