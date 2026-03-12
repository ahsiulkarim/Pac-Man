# Pac3man: Python3 port of Berkeley Pacman
A comprehensive suite of AI projects covering Search, Multi-Agent Systems, Reinforcement Learning, and Probabilistic Classification.
📂 Project Structure
The repository is organized into five main modules:
search/: Pathfinding and state-space search in Pacman.
multiagent/: Adversarial search (Minimax, Alpha-Beta Pruning, Expectimax).
reinforcement/: Value Iteration and Q-Learning for Pacman, Gridworld, and a Crawling Robot.
markov/: A Markov Babbler for generating text based on training data.
spam/: A Naive Bayesian classifier for filtering spam emails.
🚀 Getting Started
Prerequisites
Python 3.6+
tkinter (usually included with Python for the graphical interface)
Installation
Clone the repository:
code
Bash
git clone https://github.com/your-username/Pacman-main.git
cd Pacman-main
🎮 Project 1: Search
Implement classic search algorithms to help Pacman find food in a maze.
Algorithms: DFS, BFS, UCS, and A*.
Key Files: search.py, searchAgents.py.
Example Usage:
code
Bash
python search/pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python search/pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic
👻 Project 2: Multi-Agent Search
Design agents for the classic version of Pacman, including ghosts.
Concepts: Minimax, Alpha-Beta Pruning, and Expectimax.
Key Files: multiAgents.py.
Example Usage:
code
Bash
python multiagent/pacman.py -p MinimaxAgent -l minimaxClassic -a depth=4
python multiagent/pacman.py -p AlphaBetaAgent -a depth=3 -l smallClassic
🤖 Project 3: Reinforcement Learning
Implement model-based and model-free reinforcement learning.
Concepts: Value Iteration, Q-Learning, Epsilon-Greedy, and Approximate Q-Learning.
Environments: Pacman, Gridworld, and the Crawler Robot.
Key Files: valueIterationAgents.py, qlearningAgents.py.
Example Usage:
code
Bash
# Run Gridworld with Value Iteration
python reinforcement/gridworld.py -a value -i 100 -k 10
# Run Q-Learning Crawler
python reinforcement/crawler.py
✍️ Project 4: Markov Babbler
A text generation tool that uses N-gram Markov Chains to produce text that mimics a specific author's style.
Key Files: babbler.py.
Features: Sentence starters/stoppers tracking and probabilistic state transitions.
📧 Project 5: Spam Classifier
A Naive Bayesian classifier trained on the Enron email dataset to distinguish between "Ham" and "Spam".
Key Files: spamclassifier.py.
Concepts: Laplace smoothing, log-sum-exp for underflow prevention, and word frequency analysis.
🧪 Running Tests
Each project folder contains an autograder.py script to verify your implementations.
code
Bash
# Example: Testing Search algorithms
cd search
python autograder.py
📜 Credits
The Pacman AI projects were originally developed at UC Berkeley by John DeNero and Dan Klein. This repository utilizes a Python 3 port of those materials, combined with original Machine Learning assignments.

