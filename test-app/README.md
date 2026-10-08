# Quiz CLI

An interactive command-line quiz game for practicing JavaScript, Node.js, and general programming concepts. The application uses only Node.js built-in modules and demonstrates modern ES modules, asynchronous input handling, classes, array methods, and terminal formatting.

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Setup](#setup)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Quiz Content](#quiz-content)
- [Project Structure](#project-structure)
- [Development](#development)
- [Technical Details](#technical-details)
- [License](#license)

## Features

- Interactive terminal-based category selection.
- Three quiz categories: JavaScript Basics, Node.js Fundamentals, and General Programming.
- Choice of all available questions or a shorter quiz where supported.
- Randomized question order using the Fisher-Yates shuffle algorithm.
- Input validation for menu selections.
- Immediate correct/incorrect feedback and explanations.
- Progress bar and final score percentage.
- Review list for incorrectly answered questions.
- ANSI terminal colors without external dependencies.
- Option to play multiple quizzes in one session.

## Requirements

- Node.js 18 or newer.
- A terminal that supports standard ANSI color escape codes.

## Setup

Clone or download the repository, then move into the application directory:

```bash
git clone <repository-url>
cd test-app
```

No third-party packages are required. The project uses Node.js built-in modules only, so `npm install` is optional and does not install dependencies.

## Usage

Start the quiz with:

```bash
npm start
```

Alternatively, run the entry point directly:

```bash
node index.js
```

The application will:

1. Display the welcome banner.
2. Ask you to choose a quiz category.
3. Ask how many questions to answer.
4. Present each question and its numbered options.
5. Display feedback and an explanation after every answer.
6. Show your score and any questions requiring review.
7. Ask whether you want to play again.

At each menu, enter the number corresponding to your choice. When prompted to continue, press Enter. To replay after the results screen, answer `y`; answer `n` to exit.

## How It Works

`index.js` loads `data/questions.json`, builds the category and question-count menus, and controls the main play-again loop. Each selected quiz is represented by a `Quiz` instance from `src/quiz.js`.

Questions are copied and shuffled when a quiz is created. For each question, the CLI records the selected option, compares its zero-based index with the stored answer index, displays the explanation, and advances the progress state. At the end, the score and incorrect answers are displayed for review.

## Quiz Content

The bundled question bank contains five questions in each category:

- **JavaScript Basics** — constants, array methods, strict equality, primitive types, and `typeof null`.
- **Node.js Fundamentals** — the file-system module, event loop, project initialization, `process.argv`, and ES module imports.
- **General Programming** — APIs, recursion, JSON, callbacks, and version control.

Questions are stored as JSON objects with the following shape:

```json
{
  "question": "Question text",
  "options": ["First option", "Second option"],
  "answer": 0,
  "explanation": "Why the answer is correct."
}
```

The `answer` value is a zero-based index into `options`. If you add questions, preserve this convention and place them under a category in `data/questions.json`.

## Project Structure

```text
test-app/
├── data/
│   └── questions.json   # Categories, questions, answers, and explanations
├── src/
│   ├── colors.js        # ANSI color and text-style helpers
│   ├── input.js         # Readline interface and validated prompts
│   └── quiz.js          # Quiz state, scoring, shuffling, and results
├── index.js             # Application entry point and main game loop
├── package.json         # Metadata, scripts, and Node.js engine requirement
└── README.md            # Project documentation
```

## Development

The package defines a test command:

```bash
npm test
```

At present, the repository does not include test files, so this command runs Node's test runner without a project-specific test suite. The application itself can be manually verified with `npm start`.

When changing the question bank, validate that every question has at least one option and that its `answer` index points to the intended option. When changing input behavior, retain the promise-based interface expected by `index.js` and `Quiz`.

## Technical Details

- **Module system:** Native ES modules (`"type": "module"` in `package.json`).
- **Runtime APIs:** `node:fs/promises`, `node:path`, `node:url`, and `node:readline`.
- **Input model:** Promises wrapped around `readline.question`, consumed with `async`/`await`.
- **Question randomization:** Fisher-Yates shuffle on a copied array, leaving the source data unchanged.
- **Scoring:** One point for each answer whose option index matches the question's `answer` index.
- **Progress:** A 30-character Unicode progress bar and a rounded percentage.
- **Error handling:** The top-level application catches errors, prints a message and stack trace, exits with status 1, and closes the readline interface in `finally`.
- **Dependencies:** None; all runtime functionality comes from Node.js.

## License

The project declares the [MIT License](https://opensource.org/licenses/MIT) in `package.json`.
