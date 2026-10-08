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
