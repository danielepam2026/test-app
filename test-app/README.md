# Quiz CLI

## Project Description

Quiz CLI is an interactive command-line quiz game for learning and reviewing JavaScript, Node.js, and general programming concepts. It runs with Node.js, uses only built-in modules, and provides colored terminal output, randomized questions, progress tracking, explanations, scoring, and answer review.

## Key Features

- Choose from JavaScript Basics, Node.js Fundamentals, and General Programming categories.
- Select all available questions or a shorter three- or five-question quiz when supported.
- Randomize question order for each quiz session.
- Validate menu selections and provide interactive prompts through the terminal.
- Display a visual progress bar and current question number.
- Show immediate correct or incorrect feedback with explanations.
- Report scores, percentages, performance messages, and incorrect-answer review.
- Replay multiple quizzes in one session.
- Use native Node.js ES modules with no external runtime dependencies.

## Project Structure

```text
.
├── data/
│   └── questions.json   # Quiz categories, questions, options, answers, and explanations
├── src/
│   ├── colors.js        # ANSI terminal color utilities
│   ├── input.js         # Readline prompts, menus, confirmations, and pause handling
│   └── quiz.js          # Quiz state, question flow, scoring, and results
├── index.js             # Application entry point and main game loop
├── package.json         # Project metadata and npm scripts
└── README.md            # Project documentation
```

## Setup Instructions

### Prerequisites

- Node.js 18 or newer
- npm, included with Node.js
- A terminal that supports standard ANSI color escape codes

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/danielepam2026/test-app.git
   ```

2. Enter the project directory:

   ```bash
   cd test-app/test-app
   ```

3. Install the project dependencies:

   ```bash
   npm install
   ```

   The application currently has no external dependencies, but this command is safe to run and prepares the npm project.

## How to Run the Project

Start the quiz with:

```bash
npm start
```

Then follow the prompts to choose a category, select the number of questions, answer each question, and decide whether to play again.

You can also run the entry point directly:

```bash
node index.js
```

## Testing

Run the configured test command with:

```bash
npm test
```

The project currently defines the command using Node.js's built-in test runner. Add test files as the application grows.

## Content and Customization

Quiz content is stored in `data/questions.json`. To add or modify questions, preserve the existing structure:

- Each category has a display `name` and a `questions` array.
- Each question contains a `question` string, an `options` array, and a zero-based numeric `answer` index.
- The optional `explanation` is shown after the user answers.

## License

This project is licensed under the MIT License, as specified in `package.json`.
