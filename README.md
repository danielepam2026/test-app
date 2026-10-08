# quiz-cli

## Project Description

`quiz-cli` is an interactive command-line quiz game for learning JavaScript and general programming concepts. It runs in Node.js, presents questions through a terminal interface, evaluates answers, and displays scores with explanations and performance feedback.

The project uses JavaScript ES Modules and Node.js built-in APIs, including `readline` for user input and the file system module for loading quiz data. No external runtime dependencies are required.

## Key Features

- **Interactive terminal interface** – Select quiz categories and answers using numbered prompts.
- **Multiple quiz categories** – Includes JavaScript Basics, Node.js Fundamentals, and General Programming.
- **Configurable quiz length** – Answer all available questions or choose three or five questions when enough questions exist.
- **Randomized questions** – Questions are shuffled using the Fisher-Yates algorithm for each quiz.
- **Progress tracking** – Displays a progress bar and the current question number.
- **Immediate feedback** – Shows whether each answer is correct and provides an explanation when available.
- **Score reporting** – Displays the final score, percentage, category, and performance message.
- **Incorrect answer review** – Lists incorrect answers with the selected and correct responses.
- **Replay support** – Start another quiz after reviewing the results.
- **Colorized output** – Uses ANSI escape codes to improve terminal readability without external packages.
- **Error handling** – Reports loading and runtime errors before exiting with a failure status.

## Project Structure

```text
test-app/
├── data/
│   └── questions.json  # Quiz categories, questions, answers, and explanations
├── index.js            # Application entry point and main quiz loop
├── package.json        # Project metadata, scripts, and Node.js requirement
└── src/
    ├── colors.js       # ANSI color and text-style utilities
    ├── input.js        # Readline-based input and selection helpers
    └── quiz.js         # Quiz class, scoring, progress, and result handling
```

- `index.js` loads the question data, displays the main menu, creates quiz instances, and controls the replay loop.
- `src/input.js` provides reusable asynchronous prompts, list selection, confirmations, and pause functionality.
- `src/quiz.js` contains the quiz logic, including question shuffling, answer evaluation, scoring, progress rendering, and results.
- `src/colors.js` provides terminal styling helpers using ANSI escape codes.
- `data/questions.json` stores the quiz content in a category-based JSON structure.

## Setup Instructions

### Prerequisites

- Node.js 18.0.0 or later
- npm, included with Node.js

### Installation

```bash
git clone https://github.com/danielepam2026/test-app.git
cd test-app
npm install
```

The project has no external package dependencies, but running `npm install` is safe and initializes the standard npm project workflow.

### Configuration

No environment variables or additional configuration files are required. Quiz content is loaded from:

```text
data/questions.json
```

Each category contains a display name and a list of questions. Each question provides a prompt, answer options, a zero-based correct-answer index, and an optional explanation.

## How to Run the Project

Start the quiz with:

```bash
npm start
```

Alternatively, run the entry point directly:

```bash
node index.js
```

During a typical session:

1. Choose a quiz category by entering its number.
2. Choose to answer all questions, three questions, or five questions when available.
3. Press Enter to begin.
4. Select an answer for each question by entering its number.
5. Review immediate correctness feedback and explanations.
6. View the final score and incorrect-answer review.
7. Choose whether to play again.

### Running Tests

The project defines the following test command:

```bash
npm test
```

This runs Node.js's built-in test runner:

```bash
node --test
```

No test files are currently included in the repository.

## Additional Details

### Available Scripts

| Command | Description |
|---|---|
| `npm start` | Starts the interactive quiz with `node index.js`. |
| `npm test` | Runs Node.js's built-in test runner. |

### Application Architecture

The application is divided into three main concerns:

- **Application flow** – `index.js` manages loading data, menus, quiz sessions, and replay.
- **Quiz domain logic** – `src/quiz.js` manages questions, answers, scoring, progress, and results.
- **Terminal interaction** – `src/input.js` handles user input, while `src/colors.js` formats terminal output.

The project uses ES Modules, enabled by `"type": "module"` in `package.json`.

### Data Format

Quiz data is organized under a top-level `categories` object. Each category includes:

- `name` – The category label shown to the user.
- `questions` – An array of question objects.

Each question includes:

- `question` – The question text.
- `options` – An array of possible answers.
- `answer` – The zero-based index of the correct option.
- `explanation` – An explanation displayed after answering.

### License

This project is licensed under the MIT License.
