# Identity Lab

A student-oriented practice platform for **Identities and Factorization** (Junior Secondary Mathematics in Action, Book 2A — Additional Revision Exercise 2).

Built for a maths class: students read short summary notes, practise the workbook questions, and when they get one wrong they are offered a **fresh, similar question** to try — plus progressive hints and step-by-step solutions whenever they ask.

## Features

- **Summary notes** — 6 units: what an identity is, the two product identities, common factors & grouping, square patterns, the Level-2 toolkit, and exam technique with the common traps.
- **All 84 source questions** — 70 workbook questions (Level 1 & Level 2, incl. 5 multi-part challenges) and 14 Multiple Choice questions, grouped into 13 practice sets.
- **Similar questions on wrong answers** — 21 generator families (backed by a small fraction + multivariate polynomial engine) produce a new question of the same type, with its own answer, hints and worked solution.
- **Hints on demand** — 2–3 progressive hints per question, never forced.
- **Step-by-step solutions** — revealed one step at a time, following the textbook method.
- **Smart Practice** — a queue that prioritises questions the student got wrong or hasn't seen.
- **Progress tracking** — XP, streaks, per-skill mastery bars, "questions to revisit". Saved in the browser (localStorage).
- **Dark / light theme** toggle (dark by default).

## Running it

No build step, no server required:

```
open index.html
```

Maths is typeset with [KaTeX](https://katex.org) loaded from a CDN; offline it falls back to plain-text notation.

To serve it locally instead:

```
python3 -m http.server 8000   # then open http://localhost:8000
```

## Repository layout

```
index.html          single-page app shell
styles.css          theme + layout
js/engine.js        fraction & multivariate polynomial engine, answer normalisation
js/gens.js          the 21 similar-question generators
js/data.js          question bank (84 questions) + practice sets
js/learn.js         summary-notes content
js/app.js           router, UI, answer checking, hint/solution flow
js/test*.js         verification harness (see below)
```

## Verification

The question bank and generators are covered by automated checks (Node ≥ 18):

```
cd js
node test.js           # fuzz every generator (300 runs each): structure, answers, hints, steps
node test-accept.js    # all accepted answer variants are mathematically equivalent
node test-answers.js   # every stored answer matches its question (48 expand/factorise,
                       #   8 identity verdicts, 12 constants questions, all MCQ options)
```

All three suites currently pass. They caught several transcription errors during development, so re-run them after editing the bank.

## Notes

Questions were transcribed from the Pearson *Junior Secondary Mathematics in Action* additional revision exercise and its solutions for classroom use.
