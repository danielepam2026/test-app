# quiz-cli

## Project Overview

`quiz-cli` is an interactive command-line quiz game for learning and reviewing JavaScript, Node.js, and general programming concepts. It is designed for developers and learners who want a lightweight terminal-based practice tool without external runtime dependencies.

The application is implemented as an ES module Node.js CLI and uses Node.js built-in modules for file loading and interactive input. Questions are stored in a JSON data file, while quiz execution, terminal formatting, and input handling are separated into focused modules.

## Features

- **Interactive category selection:** Choose JavaScript Basics, Node.js Fundamentals, or General Programming.
- **Configurable quiz length:** Answer all available questions or select three or five when the category contains enough questions.
- **Randomized questions:** Each quiz receives a shuffled copy of the selected questions using the Fisher–Yates algorithm.
- **Validated menu input:** Invalid menu numbers are rejected until a valid option is entered.
- **Immediate feedback:** Each answer is marked correct or incorrect, with the correct answer shown when needed.
- **Explanations:** Questions can display an educational explanation after the answer.
- **Progress display:** A terminal progress bar shows quiz completion percentage.
- **Results and review:** Final scores include a performance message and a review of incorrect answers.
- **Replay loop:** Players can start another quiz after viewing results.
- **ANSI terminal styling:** Output uses built-in ANSI escape codes with no external color dependency.

## File Structure

```text
quiz-cli/
├── package.json              # Project metadata, Node.js requirement, and npm scripts
├── index.js                  # CLI entry point, question loading, and application loop
├── data/
│   └── questions.json        # Categories and multiple-choice question data
└── src/
    ├── colors.js             # ANSI color and text-style helpers
    ├── input.js              # Readline prompts, selection, confirmation, and pause helpers
    └── quiz.js                # Quiz class, shuffling, scoring, progress, and results
```

## Setup Instructions

### Prerequisites

- Node.js 18.0.0 or later.
- A terminal capable of running an interactive Node.js process.

### Installation

Clone the repository, enter the project directory, and install the project metadata and dependencies:

```bash
git clone <REPOSITORY_URL>
cd test-app
npm install
```

The project does not declare external npm dependencies, so `npm install` does not need to download runtime packages.

### Configuration

No environment variables or configuration files are required. Edit `data/questions.json` to add or modify categories and questions.

## Usage Examples

### Start the quiz

```bash
npm start
```

This runs `node index.js` and opens the interactive quiz in the terminal.

### Typical session

1. Start the application with `npm start`.
2. Select a category by entering its displayed number, such as `1` for JavaScript Basics.
3. Select `All questions`, `3 questions`, or `5 questions` when available.
4. Press Enter to begin.
5. For each question, enter the number of the answer option.
6. Read the immediate correctness feedback and explanation, then press Enter to continue.
7. Review the score, percentage, performance message, and any incorrect answers.
8. Enter `y` to play again or any response not beginning with `y` to exit.

Invalid category, question-count, or answer selections produce a validation message and prompt again.

## Additional Details

### Available scripts

The scripts are defined in `package.json`:

```bash
npm start   # Run the CLI with Node.js
npm test    # Run Node.js's built-in test runner
```

No test files are included in the repository, so `npm test` currently starts the Node.js test runner without repository-defined test cases.

### Architecture and module interaction

- `index.js` resolves its own directory for ES modules, loads and parses `data/questions.json`, presents category and question-count menus, and controls the replay loop.
- `src/input.js` wraps Node.js `readline` in Promise-based helpers. Its `select` helper prints numbered options and validates numeric input.
- `src/quiz.js` owns quiz state. The `Quiz` class shuffles questions, tracks the current index and score, records answers, renders progress, asks questions, and prints results.
- `src/colors.js` provides ANSI escape-code formatting functions used by the entry point and quiz logic.

### Data format

`data/questions.json` contains a top-level `categories` object. Each category has a display `name` and a `questions` array. Every question contains a prompt, an ordered `options` array, a zero-based numeric `answer` index, and an optional `explanation`:

```json
{
  "categories": {
    "category-id": {
      "name": "Category name",
      "questions": [
        {
          "question": "Question text",
          "options": ["Option A", "Option B"],
          "answer": 0,
          "explanation": "Why the answer is correct."
        }
      ]
    }
  }
}
```

The answer index must correspond to an item in the options array. The current data contains three categories with five questions each.

### Error handling

The main application catches errors from question-file loading, JSON parsing, and the interactive flow. It prints the error message and stack trace, exits with status code `1`, and closes the readline interface in a `finally` block. Menu selection input is handled locally by repeatedly prompting until a valid number is supplied.

### License

The project is licensed under the MIT License, as declared in `package.json`.
