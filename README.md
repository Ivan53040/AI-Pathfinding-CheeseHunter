Search Assignment – Cheese Hunter

📌 About

This repository contains the support code and starter templates for Cheese Hunter. The project focuses on implementing search algorithms (such as UCS, A* etc.) to solve a grid‑based puzzle where an agent must find cheese while avoiding traps and leveraging levers.

The codebase includes utility modules for representing the environment and game state, starter solution files, test cases, and scripts to run and evaluate your solution. The included documentation explains the problem specification, design considerations, and expected behaviour.

📁 Repository Structure

Path	Description
- game_env.py	Simulates the Cheese Hunter environment and transitions
  
- game_state.py	Encapsulates game state (agent position, lever/trap status)
  
- play_game.py	Script to run an interactive game session

- solution.py	Starter file for your search solution

- tester.py	Test harness to evaluate your implementation

- testcases/	Input files for testing solver correctness

- gui.py	Optional graphical interface for play/testing

- gui_assets/	Supporting assets for GUI display

- control/	Control logic used by tests or GUI

- Report.pdf	Assignment report explaining design and approach

- Spec.pdf	Official problem specification and requirements

- README.md	(This file) project overview and instructions

🛠 Getting Started

Running Your Solution

1. Clone the repository:

git clone https://github.com/Ivan53040/Search.git
cd Search

2. Inspect test cases:

The testcases/ directory contains level definitions for evaluating your solution.

3. Implement your solver:

Write your search logic inside solution.py (e.g., implement UCS and A*).

4. Run the tester script:

python tester.py

This will run your implementation against provided test cases and report performance indicators.

📖 Play the Game

You can interactively play Cheese Hunter using the play_game.py script:

python play_game.py testcases/level_1.txt

Follow on‑screen prompts to move the agent manually or test your search outcomes.

🧠 Solver Template

The file solution.py includes stubs for the search functions you need to implement. It’s designed so you can focus on algorithm logic (e.g., Uniform Cost Search, A*) while the supporting code handles environment transitions and state representation.

📚 Documentation

- Spec.pdf – Full problem description, input/level format, scoring rules.

- Report.pdf – Your report summarising approach, design decisions, and test results.

These files help assess correctness as well as design clarity.

🔹 Heuristic and A* Search

For the A* implementation, a custom heuristic was designed to efficiently solve the CheeseHunter environment. Key points:

1. Directed Movement Cost – Accounts for asymmetric action costs: walking, sprinting, climbing, and dropping all have different costs, so the heuristic reflects movement efficiency.

2. Lever–Goal Ordering via MST – Since all levers must be activated before reaching the goal, a Minimum Spanning Tree (MST) over remaining levers + goal provides a tight lower bound.

3. Lever Activation Cost – Each lever requires a discrete activation action; this cost is included in the heuristic to avoid underestimation.

✅ Admissibility

The heuristic is admissible, meaning it never overestimates the true cost:

- Movement cost uses minimum per-cell cost, so cheaper options are always assumed available.

- MST lower bound ensures the cost of visiting remaining levers + goal is underestimated rather than overestimated.

- Activation cost counts exactly one action per lever.

This combination reduces node expansions significantly compared to UCS, especially on large maps, while keeping runtime overhead manageable via precomputation and caching.

📊 Testing

The repository includes test scripts and cases to verify your implementation:

- tester.py runs solver functions and prints metrics.

- Additional test files are provided in testcases/.

This helps ensure your algorithms satisfy all assignment criteria.

📈 Learning Outcomes

This assignment demonstrates:

- Implementation of search strategies for AI problem solving

- Handling of state spaces and transitions

- Use of test automation for algorithm validation

- Integration of logic with a game environment simulator

It is a solid showcase of classical AI search methods in practice.
