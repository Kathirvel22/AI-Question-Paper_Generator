# AI Question Paper Generator

An AI-powered web application that automatically generates customised question papers based on **syllabus topics, subject, total marks, and difficulty level** — built entirely with **HTML, CSS, and JavaScript**.

No backend, no installation, no dependencies. Open one file in a browser and it works.

---

## Overview

Setting a question paper manually is repetitive: balancing marks across sections, matching questions to the syllabus, and adjusting difficulty every time. This project automates that process.

You enter:
- Subject name
- Syllabus topics
- Total marks
- Exam duration
- Difficulty level (Easy / Medium / Hard)
- Which question types to include (MCQ, Short Answer, Long Answer)

The app then generates a fully formatted question paper — with sections, mark allocation, multiple-choice options, and an optional answer key — instantly, in the browser.

---

## Features

- **Syllabus-driven generation** — every question is built from the topics you provide, so the paper always matches what was actually taught.
- **Automatic mark distribution** — total marks are intelligently split across MCQ (1 mark), Short Answer (2–3 marks), and Long Answer (5–10 marks) sections so the paper always adds up correctly.
- **Difficulty scaling** — question phrasing changes with difficulty: *"Define X"* for Easy, *"Explain X with an example"* for Medium, *"Critically analyse X"* for Hard.
- **Multiple choice generation** — MCQs are generated with plausible distractor options, with the correct answer tracked internally.
- **Answer key toggle** — instantly reveal/hide the MCQ answer key for teacher use.
- **Print / Save as PDF** — one click to print the paper in a clean, exam-ready layout (controls are automatically hidden in print view).
- **Variation seed** — regenerate a fresh shuffle of questions from the same topics by changing the seed value.
- **100% client-side** — no server, no API keys, no data leaves the browser.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, responsive grid layout, print stylesheet) |
| Logic | Vanilla JavaScript (ES6) |
| Fonts | Google Fonts — Source Serif 4, Inter |

No frameworks, no build tools, no npm install required.

---

## Project Structure

```
AI-Question-Paper-Generator/
│
└── AI_Question_Paper_Generator.html   # Single self-contained file (HTML + CSS + JS)
```

Everything — markup, styling, and generation logic — is bundled into one `.html` file for easy submission and deployment. A modular three-file version (`index.html`, `style.css`, `script.js`) is also available on request / in the `source/` branch if you'd prefer to split it out for development.

---

## How It Works

1. **Input parsing** — syllabus topics are split into a list (comma or newline separated).
2. **Mark distribution algorithm** — `distributeMarks()` calculates how many questions of each type are needed so the marks sum to the exact total entered, reserving ~15–20% for MCQs and splitting the remainder between Short and Long answers.
3. **Question generation** — for each question slot, a topic is pulled from the syllabus list and combined with a difficulty-appropriate verb/template (e.g. `"{verb} {topic} {suffix}."`), so no two generated papers read identically even for the same topic list.
4. **MCQ construction** — the correct answer (an actual syllabus topic) is mixed with three distractor options drawn from a generic distractor pool, then shuffled so the correct option's position varies.
5. **Rendering** — the generated question set is rendered into a formatted exam-paper layout with sections, instructions, and per-question mark labels.
6. **Seeded randomness** — a lightweight seedable PRNG (`makeRng()`) ensures the shuffle is reproducible when the same seed is reused, but varies freely otherwise.

---

## Getting Started

### Run it locally
1. Download `AI_Question_Paper_Generator.html`.
2. Double-click it (or open it in any modern browser — Chrome, Firefox, Edge, Safari).
3. Fill in the form on the left and click **Generate question paper**.

### Deploy it
Since it's a single static HTML file, you can host it anywhere with zero configuration:
- **GitHub Pages** — push the file to a repo and enable Pages.
- **Netlify / Vercel** — drag and drop the file.
- **Any static file host** — just upload it.

---

## Usage Example

**Input:**
- Subject: `Data Structures`
- Topics: `Arrays, Linked Lists, Stacks, Queues, Recursion`
- Total Marks: `50`
- Difficulty: `Medium`

**Output:** A formatted paper with:
- Section A — 8 MCQs (1 mark each)
- Section B — Short answer questions (2–3 marks each)
- Section C — Long answer questions (5–10 marks each)
- Total marks summing exactly to 50

---

## Possible Extensions

- Connect to a real LLM API (e.g. Claude) for richer, subject-aware question phrasing instead of template-based generation.
- Export directly to PDF/DOCX without relying on the browser's print dialog.
- Support question banks uploaded from a CSV/spreadsheet.
- Add Bloom's Taxonomy tagging per question.
- Multi-language support for regional syllabi.

---

## License

This project is open for academic and educational use. Feel free to fork, modify, and build on it.

---

## Author

Submitted as a mini-project: **AI Question Paper Generator using HTML, CSS, JavaScript**.
