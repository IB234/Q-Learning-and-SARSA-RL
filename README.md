# 🧗‍♂️ Reinforcement Learning: Q-Learning vs. SARSA on CliffWalking

This repository provides a complete Jupyter Notebook implementation comparing two foundational Reinforcement Learning (RL) algorithms: **Q-Learning** (off-policy) and **SARSA** (on-policy). The algorithms are evaluated using the `CliffWalking-v1` environment from the `gymnasium` library.

## 📋 Project Features

* **Algorithm Implementations:** Custom, from-scratch functions for both SARSA (`run_sarsa`) and Q-Learning (`run_q_learning`) using an $\epsilon$-greedy action selection strategy.


* **Performance Visualization:** Tracks the sum of rewards per episode and smooths the learning curves using a Pandas rolling mean (window size of 50) for clear performance comparison.


* **Policy Mapping:** Includes a `visualize_policy` function that maps the Q-table to a 4x12 grid, displaying the chosen path with directional arrows (↑, →, ↓, ←), the Start (S), Goal (G), and Cliff (C) states.


* **Hyperparameter Exploration:** Conducts a grid search to compare how both algorithms respond to different hyperparameter combinations, specifically testing exploration rates ($\epsilon = 0.01, 0.35$) and learning rates ($\alpha = 0.05, 0.5$).



## 🛠️ Dependencies

Ensure you have Python 3 installed along with the following required libraries:

```bash
pip install gymnasium numpy matplotlib pandas

```

## 🚀 Usage

Run the Jupyter Notebook sequentially. Upon execution, the code automatically generates a directory named `RL_hw3_data/` in the working directory to store all generated data and visualizations.

## 📊 Generated Outputs

The notebook outputs the following files into the `RL_hw3_data/` directory:

* **`standard_training_returns.csv`**: A CSV file containing the raw episode-by-episode total returns for both algorithms over 500 episodes.


* **`sarsa_learning_curve.png`**: The smoothed learning curve for the SARSA agent.


* **`qlearning_curve.png`**: The smoothed learning curve for the Q-Learning agent.


* **`learning_curves_comparison.png`**: An overlaid plot comparing the smoothed and raw returns of both SARSA and Q-Learning.


* **`sarsa_policy.png` & `qlearning_policy.png**`: Grid visualizations showing the final deterministic path chosen by each algorithm's Q-table.


* **`hyperparameter_exploration.png`**: A 2x2 subplot matrix illustrating the algorithms' performance across the tested $\epsilon$ and $\alpha$ hyperparameter variations.



## 🧠 Algorithm Behavior

* **Q-Learning (Off-Policy):** Learns the absolute optimal path (right along the cliff's edge). Due to $\epsilon$-greedy exploration, this risky path often leads to the agent falling off the cliff during training, resulting in lower online rewards but a strictly optimal theoretical policy.
* **SARSA (On-Policy):** Learns the value of the policy it is currently following, meaning it accounts for its own exploration rate. This causes the agent to learn a safer, longer path away from the cliff to avoid the massive penalty of falling during the exploration phase.
