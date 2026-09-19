# Problems this template solves

## The short version

**Pure active recall is the gold standard for long-term retention — and the wrong tool
for a multiple-choice board exam.**

Anki's default workflow is blank-page retrieval: see the prompt, produce the answer from
nothing. That is the hardest, most durable form of learning. It is also expensive, and
its cost only pays off if the thing you're being tested on *requires* production.

The Philippine pharmacy board exam — like most professional licensure exams — is
**100% multiple choice**. Every item hands you the answer among four or five options and
asks you to recognise the right one. So the exam is measuring **recognition**, not
production. Drilling full recall:

- spends the same study minute on a strictly harder task,
- adds retrieval failure modes the exam will never test, and
- produces **less exam-relevant yield per minute** than practising the format itself.

Familiarity with the actual question format has a **higher yield** for this target than
picture-perfect recall. That is not an argument against active recall in general — it is
an argument against using the most expensive tool for a cheaper job.

## What this template does instead

It trains recognition under exam-like conditions:

| Problem with a plain Anki deck for MCQ prep | What this template does |
|---|---|
| A basic card shows the answer immediately, so you never actually *choose* | You click a choice; nothing is revealed until you commit |
| You memorise "the third option is right" by position | Choices are **randomised on every rep**, so position carries no signal |
| Single-answer cards train a format that doesn't exist on multi-select items | Supports **multiple correct answers**; on the back each choice is marked `Correct`, `Wrong`, or `Missed` |
| Nothing stops you from guessing wildly to reach the answer | A **dynamic selection limit** disables further choices once you've hit the number of correct answers — a hint that doesn't reveal which ones |
| Getting it wrong tells you "wrong" and nothing else | The back distinguishes a *wrong* pick from a *missed* correct answer, which are different study signals |
| Re-reading a wall of options on a phone | Mobile-first layout that works on Anki Desktop, AnkiWeb and AnkiMobile |

## Who this is for

- **Licensure / board exam candidates** — any exam where the item format is multiple
  choice and the goal is a passing score, not mastery for its own sake.
- **Anyone converting a question bank** into spaced repetition without losing the
  answer-selection step that the real exam requires.
- **Students who over-study** for recognition tests and would rather spend the same
  minutes on the format they'll actually face.

## What it deliberately does not do

- It does not attempt to teach production recall. If your target requires generating an
  answer from nothing — diagnostics, dosing calculations, counselling scripts — use a
  cloze or basic card for that, not this template.
- It does not hide the answer for long. Recognition practice is a *familiarity* loop;
  the value comes from repetition at volume, not from struggle.

## Companion project

[**Anki-MCQ-Importer-AI-Batch-Generator**](https://github.com/anki-boi/Anki-MCQ-Importer-AI-Batch-Generator)
solves the step before this one: turning folders of lecture-slide images into structured
MCQ cards for this note type, in batches, via the Gemini API.
