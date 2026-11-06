# SDA2 Workshop: Architectural Styles

Hands-on exercises for the SDA2 Software Architecture workshop. You implement small systems in three architectural styles (monolith, layered, event-driven) and compare the resulting structures. Each exercise is a single Python file with a built-in test suite: the tests define the required behaviour, and your task is to make them pass (test-driven development).

## Learning objectives

After the workshop you can

- describe the characteristics and trade-offs of monolithic, layered and event-driven architectures,
- explain how an architectural style shapes code organisation, coupling and testability,
- use failing tests as an executable specification,
- argue which style fits which part of a given system.

## Repository structure

```
├── 01-monolith/
│   ├── todo_manager.py           # starter code + 15 tests
│   └── guide.md                  # background and instructions
├── 02-layered/
│   ├── library_management.py     # starter code + 18 tests
│   └── guide.md
├── 03-event-driven/
│   ├── library_notification.py   # starter code + 17 tests
│   └── guide.md
└── README.md
```

## Getting started

Requirements: Python 3.8 or newer. No external packages are needed.

```bash
git clone https://github.com/bfh-teaching/sda2-workshop-architectural-styles
cd sda2-workshop-architectural-styles
```

Alternatively, download the repository as a ZIP file from GitHub.

### Running the tests

Each file runs its own tests when executed:

```bash
cd 01-monolith
python3 todo_manager.py        # on Windows: python todo_manager.py
```

At the start, all tests fail. Implement the functions marked with `TODO`, run the file again and repeat until the summary shows `OK`.

## Workshop flow

Work in groups of two or three. Record your test results and answers for each part on the Miro board (one row per group).

### Part 1: Monolith (`01-monolith/todo_manager.py`)

A to-do manager with global state and direct function calls.

- Shared global state, direct coupling between functions
- Simple to develop and deploy
- Question: where does the shared state make the code fragile, and how could a monolith still be modular?

### Part 2: Layered (`02-layered/library_management.py`)

A library management system split into data access, business logic and presentation layers.

- Each layer only calls the layer directly below it
- Changes stay local to one layer
- Question: which call would have violated the layer rule, and which change would affect only one layer?

### Part 3: Event-driven (`03-event-driven/library_notification.py`)

A library notification system in which services communicate through an event broker.

- Producers publish events without knowing their consumers
- New consumers can be added without changing the producer
- Question: which consumer could you add without changing the producer, and what became harder to trace?

### Part 4: Comparison

Compare the three implementations and relate them to your Assignment 1 case.

| | Monolith | Layered | Event-driven |
|---|---|---|---|
| Coupling | tight, shared state | controlled, top-down | loose, via events |
| Change impact | anywhere | mostly one layer | mostly one service |
| Traceability | direct calls | direct calls | indirect, via broker |
| Scaling | as a whole | as a whole or per tier | per service |

## Working method

1. Read the `guide.md` of the exercise.
2. Read the failing tests: test names and assertions are the requirements.
3. Implement one function at a time and rerun the tests after each step (red, green, refactor).
4. When all tests pass, check whether your code still follows the architectural style, not only the tests.

You may use AI assistants. Make sure you can explain every line of your solution in the group discussion.

## License

MIT License, see [LICENSE](LICENSE).

## Questions

Ask during the workshop or in the SDA2 Moodle forum.
