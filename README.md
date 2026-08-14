# Acquia Back End Specialist study track

A study track for the Acquia Certified Drupal 10/11 Back End Specialist exam. Static site, no build step, no dependencies.

**Live:** https://lucas-cunico.github.io/acquia-be-specialist/ (English version at [/en/](https://lucas-cunico.github.io/acquia-be-specialist/en/))

## Why this exists

Studying alone for this exam gets tiring. You read the blueprint, open a dozen tabs, lose track of what you already covered, and never really know whether you are ready or just familiar with the vocabulary.

This track answers three questions the scattered material does not:

1. What is worth studying, and in what proportion. The six modules are weighted the way the exam weights its domains. Cache and security is 27% of the exam, so it is the longest module. Render API is 10%, so it is a short one.
2. Whether the reading turned into retention. Every module ends with a timed mock exam in the exam format.
3. What is still weak. The dashboard tracks progress per module and names the weakest domain.

## What is in it

- 35 written lessons with real code, not bullet summaries
- 7 hands-on labs, each with a definition of done
- 69 questions across 7 mock exams, each answer explained, including why the wrong options are wrong
- A final mock exam with 20 real exam questions, kept word for word in English, plus six blocks that teach how to answer them
- Readiness dashboard: 60% study, 40% best mock exam score, weighted by domain

Progress lives in the browser `localStorage`. Nothing is sent anywhere, and the two language versions share the same progress.

## Coverage

| Module | Domains | Weight |
|---|---|---|
| 1. OO fundamentals and the request cycle | 1.0 | 16% |
| 2. Entity and Configuration API | 2.0 | 17% |
| 3. Plugins, events and Form API | 2.0 | 16% |
| 4. Render API, Twig and libraries | 4.0 | 10% |
| 5. Cache and security | 5.0, 6.0 | 27% |
| 6. Debugging, tests and community | 3.0, 7.0 | 14% |
| Final exam (extra) | real questions | outside the weighting |

Weights follow the [official Acquia blueprint](https://docs.acquia.com/acquia-academy/acquia-certified-drupal-backend-specialist). The final mock exam is deliberately excluded from the overall readiness figure, so the six module weights keep summing to 100%.

## Running it locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000/. Opening `index.html` straight from the filesystem also works.

## Editing

All content, styling and behaviour live in two files:

- `index.html` (Portuguese)
- `en/index.html` (English)

They are self contained: inline CSS, inline JS, zero external requests. Lessons are plain HTML sections. Mock exam questions are a `QUIZ` object at the bottom of the script, one array per module:

```js
{ q: 'Question text',
  o: ['option 1', 'option 2', 'option 3', 'option 4'],
  a: 1,                  // index of the correct option
  e: 'Why this is the answer, and why the others are not.' }
```

For multiple answer questions, add `m: true` and pass `a` as an array of indexes.

When you change one language version, mirror the change in the other. The checkbox ids (`data-c`) and answer keys must stay identical, because progress is shared between them.

## Publishing

```
git push origin main            # source
git push origin main:gh-pages   # publish
```

GitHub Pages serves the `gh-pages` branch from the repository root.

## Accuracy

The answer key for the final exam was corrected against the official results. Two of its explanations flag where the expected answer disagrees with everyday Drupal practice, on the `_controller` syntax and on whether `set()` alone persists an entity. Read those notes before taking them as coding advice.

Content and weights were checked against the official blueprint in August 2026. Review the blueprint yourself before buying a voucher.
