# Pac3man: Python3 port of Berkeley Pacman
# 🟡 Pac3man — Python 3 Port of Berkeley Pacman AI

> A complete Python 3 port of the [UC Berkeley Pacman AI Projects](http://ai.berkeley.edu), extended with a Markov Text Babbler and a Naïve Bayesian Spam Classifier.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Modules](#modules)
  - [Project 1 — Search](#project-1--search)
  - [Project 2 — Multi-Agent Search](#project-2--multi-agent-search)
  - [Project 3 — Reinforcement Learning](#project-3--reinforcement-learning)
  - [Project 0 — Markov Babbler](#project-0--markov-babbler)
  - [Spam Classifier](#spam-classifier)
- [Getting Started](#getting-started)
- [Running the Autograder](#running-the-autograder)
- [Requirements](#requirements)
- [Attribution](#attribution)

---

## Overview

**Pac3man** ports all three classic Berkeley AI Pacman projects from Python 2 to Python 3. It covers core AI topics — informed and uninformed search, adversarial game-tree search, and model-based reinforcement learning — all through the lens of guiding a Pacman agent through a maze.

In addition to the three Pacman projects, this repository includes:
- A **Markov Chain text generator** (Babbler) trained on literary texts.
- A **Naïve Bayesian Spam Classifier** that distinguishes spam from ham email.

> 💡 Solution code is maintained on a **private branch** to prevent academic dishonesty. This repository contains only the assignment scaffolding.

---

## Project Structure

```
Pacman-main/
├── search/               # Project 1: Search algorithms
├── multiagent/           # Project 2: Adversarial multi-agent search
├── reinforcement/        # Project 3: Reinforcement learning
├── markov/               # Project 0: Markov babbler
├── spam/                 # Naïve Bayesian spam classifier
└── util/                 # Shared utility scripts
```

---

## Modules

---

### Project 1 — Search

📁 `search/`

Pacman navigates mazes using classical graph search algorithms. The goal is to implement general-purpose search strategies and apply them to increasingly complex Pacman problems.

**Algorithms implemented:**

| # | Problem | Algorithm |
|---|---------|-----------|
| Q1 | Depth First Search | DFS |
| Q2 | Breadth First Search | BFS |
| Q3 | Uniform Cost Search | UCS |
| Q4 | A\* Search | A\* with heuristics |
| Q5 | Corners Problem | State-space representation |
| Q6 | Corners Problem | Admissible heuristic design |
| Q7 | Eating All The Dots | Food heuristic (A\*) |
| Q8 | Suboptimal Search | Greedy closest-dot agent |

**Key files:**

| File | Description |
|------|-------------|
| `search.py` | **Edit this** — implement DFS, BFS, UCS, A\* |
| `searchAgents.py` | **Edit this** — implement search-based Pacman agents |
| `pacman.py` | Main game driver |
| `game.py` | Core game logic |
| `util.py` | Data structures (Stack, Queue, PriorityQueue) |
| `run.py` | Helper for running commands without the CLI |

**Example commands:**

```bash
cd search

# Run Pacman with DFS on a tiny maze
python pacman.py -l tinyMaze -p SearchAgent

# Run A* with Manhattan heuristic
python pacman.py -l mediumMaze -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic

# Run the autograder
python autograder.py
```

---

### Project 2 — Multi-Agent Search

📁 `multiagent/`

Pacman now faces adversarial ghosts. This project introduces game-tree search algorithms for multi-agent environments.

**Algorithms implemented:**

| # | Problem | Algorithm |
|---|---------|-----------|
| Q1 | Reflex Agent | State evaluation function |
| Q2 | Minimax | Minimax search |
| Q3 | Alpha-Beta Pruning | Minimax with pruning |
| Q4 | Expectimax | Probabilistic ghost behavior |
| Q5 | Evaluation Function | Custom state scoring |

**Key files:**

| File | Description |
|------|-------------|
| `multiAgents.py` | **Edit this** — implement all agents |
| `pacman.py` | Main game driver |
| `ghostAgents.py` | Ghost behavior (RandomGhost, DirectionalGhost) |
| `game.py` | Game state and mechanics |

**Example commands:**

```bash
cd multiagent

# Run minimax agent (depth 2) on classic layout
python pacman.py -p MinimaxAgent -l minimaxClassic -a depth=2

# Run alpha-beta with depth 3
python pacman.py -p AlphaBetaAgent -a depth=3 -l smallClassic

# Run expectimax
python pacman.py -p ExpectimaxAgent -l trappedClassic -a depth=3

# Autograder for question 2 only
python autograder.py -q q2
```

**Available layouts:** `minimaxClassic`, `smallClassic`, `trappedClassic`, `mediumClassic`, `openClassic`, and more in `layouts/`.

---

### Project 3 — Reinforcement Learning

📁 `reinforcement/`

Pacman learns to play using value-based and model-free reinforcement learning methods. Agents are first tested in a Gridworld environment, then on a simulated robot crawler, and finally on Pacman itself.

**Algorithms implemented:**

| # | Problem | Algorithm |
|---|---------|-----------|
| Q1 | Value Iteration | Synchronous Bellman updates |
| Q2 | Bridge Crossing Analysis | Policy analysis |
| Q3 | Policies | Discount / noise parameter tuning |
| Q4 | Q-Learning | Tabular Q-learning |
| Q5 | Epsilon Greedy | Exploration vs. exploitation |
| Q6 | Bridge Crossing (Revisited) | Q-learning policy analysis |
| Q7 | Q-Learning and Pacman | Apply Q-learning to Pacman |
| Q8 | Approximate Q-Learning | Feature-based Q-learning |

**Key files:**

| File | Description |
|------|-------------|
| `valueIterationAgents.py` | **Edit this** — value iteration agent |
| `qlearningAgents.py` | **Edit this** — Q-learning and approximate Q-learning |
| `analysis.py` | **Edit this** — policy analysis answers |
| `mdp.py` | Markov Decision Process interface |
| `learningAgents.py` | Base classes for learning agents |
| `featureExtractors.py` | Feature functions for approximate Q-learning |
| `gridworld.py` | Gridworld environment |
| `crawler.py` | Simulated robot crawler environment |

**Example commands:**

```bash
cd reinforcement

# Run value iteration on Gridworld
python gridworld.py -a value -i 100 -k 10

# Run Q-learning on Gridworld
python gridworld.py -a q -k 5

# Run Pacman with Q-learning (training + testing)
python pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid

# Run Pacman with approximate Q-learning
python pacman.py -p ApproximateQAgent -a extractor=SimpleExtractor -x 50 -n 60 -l mediumGrid

# Run the autograder
python autograder.py
```

---

### Project 0 — Markov Babbler

📁 `markov/`

A Markov Chain text generator that trains on literary texts (e.g., Lewis Carroll's _Alice in Wonderland_) and produces novel sentences that imitate the author's style.

**How it works:**

Given a training corpus, the babbler builds an n-gram state machine. Each state (n-gram) stores transition probabilities to the following words. When generating text, it performs a random walk through the state machine until reaching a sentence terminator.

**Key files:**

| File | Description |
|------|-------------|
| `babbler.py` | **Edit this** — core Markov chain and babbler logic |
| `test_markov.py` | Unit tests for babbler |
| `graphit.py` | Visualise the Markov chain as a graph |
| `maketest.py` | Utility to generate test fixtures |
| `tests/` | Sample test sentences (`test1.txt`, `test2.txt`, `test3.txt`) |
| `img/` | Markov chain diagram images (unigram & bigram) |

**Example usage:**

```python
from babbler import Babbler

b = Babbler(n=2)            # bigram model
b.add_file("alice.txt")     # train on a book
print(b.babble())           # generate a sentence
```

**Run unit tests:**

```bash
cd markov
python test_markov.py
```

**Markov Chain diagrams:**

Unigram model for a toy corpus:

![Unigram Markov Chain](markov/img/test1.png)

Bigram model for the same corpus:

![Bigram Markov Chain](markov/img/test2.png)

---

### Spam Classifier

📁 `spam/`

A Naïve Bayesian classifier that labels emails as **spam** or **ham** (legitimate). It uses bag-of-words features with word frequency counts from labelled training data.

**Key files:**

| File | Description |
|------|-------------|
| `spamclassifier.py` | **Edit this** — Naïve Bayes classifier |
| `stopwords.txt` | Common English stop words to filter out |

**How it works:**

1. Train on labelled spam and ham email corpora.
2. Compute per-class word probabilities with Laplace smoothing.
3. Classify new emails by comparing log-likelihoods under each class.

---

## Getting Started

### Prerequisites

- Python 3.8 or higher
- `tkinter` (for graphical display — usually included with Python)

### Clone and run

```bash
git clone https://github.com/<your-username>/Pacman.git
cd Pacman

# No extra dependencies required for the core game.
# Optionally activate the bundled virtual environment (Windows):
.env\Scripts\activate

# Or create your own:
python -m venv venv
source venv/bin/activate    # macOS/Linux
venv\Scripts\activate       # Windows
```

### Quick start — play Pacman yourself

```bash
cd search
python pacman.py
```

Use the **arrow keys** to move. Close the window or press `q` to quit.

---

## Running the Autograder

Each project has a built-in autograder that verifies correctness against a suite of test cases.

```bash
# Grade all questions
python autograder.py

# Grade a single question
python autograder.py -q q1

# Grade a specific test case (with graphics)
python autograder.py -t test_cases/q2/0-small-tree

# Run without graphics
python autograder.py --no-graphics
```

---

## Requirements

| Requirement | Version |
|-------------|---------|
| Python | ≥ 3.8 |
| tkinter | Bundled with CPython |
| pip | ≥ 24 (included in `.env`) |

No third-party packages are required for the game engine or algorithms. The bundled `.env/` directory contains a pre-configured virtual environment on Windows with Python 3.12.

---

## Attribution

The Pacman AI projects were originally developed at **UC Berkeley** for the CS 188 course.

- Core projects and autograders: **John DeNero** & **Dan Klein**
- Student-side autograding: **Brad Miller**, **Nick Hay**, and **Pieter Abbeel**
- Original source: [http://ai.berkeley.edu](http://ai.berkeley.edu)

This repository is a **Python 3 port** of those original Python 2 projects, with additional assignments (Markov Babbler, Spam Classifier) added for educational use.

> ⚠️ **Academic integrity notice:** Do not distribute solution code. Solution implementations are kept on a private branch. This repository contains only the assignment scaffolding as intended.

---

<p align="center">
  Made with 🟡 and Python 3
</p>
