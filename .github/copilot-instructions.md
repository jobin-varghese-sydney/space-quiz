# Copilot instructions

## Project structure and behavior

- This is a dependency-free, single-file web app. `index.html` contains the markup, CSS, question data, and quiz logic; open it directly in a browser to run it.
- The `questions` array is the source of truth for quiz content. Each entry has an `icon`, `text`, four `choices`, a zero-based `answer` index, and an `explanation`.
- Quiz state is held in `currentQuestion`, `score`, and `answered`. `renderQuestion` updates the question and progress, `selectAnswer` locks choices and provides feedback, `showResults` replaces the question view at completion, and `restartQuiz` resets the state.
- The styles and script target stable element IDs in the page markup. Keep those IDs in sync when changing the UI or its behavior.

## UI and accessibility conventions

- Keep the app self-contained: use browser-native HTML, CSS, and JavaScript without a build step or runtime dependency.
- Theme colors are CSS custom properties in `:root`, with dark-theme overrides under `prefers-color-scheme: dark`. Keep new colors theme-aware; do not hard-code a color that makes controls or feedback unreadable in either theme.
- The quiz card uses a mission-control visual style. Preserve its instrument-panel treatment while keeping correct answers green and incorrect answers red.
- Use native buttons for choices and actions. Preserve visible `:focus-visible` styling, logical focus movement between questions, the live feedback region, and the progress bar's accessible value.
- Respect `prefers-reduced-motion` when adding animations. Keep the narrow responsive layout working at mobile widths.

## Build, test, and lint

- No build, test, or lint commands are configured. There is no package manifest or test runner.
- To run the app, open `index.html` directly in a browser. For a browser smoke check, answer through all 10 questions and verify choice locking, score changes only for correct answers, correct/incorrect feedback, progress updates, the results screen, and replay reset.
