# Reinforcement Learning - CartPole – Tabular Q-Learning (Discretized State Space)

This project implements **tabular Q-learning** to solve the **CartPole-v1** environment by converting the continuous observation space into a finite discrete state space.
---
## Environment
**CartPole-v1** provides a continuous 4-dimensional observation:
- Cart position  
- Cart velocity  
- Pole angle  
- Pole angular velocity  

Tabular Q-learning requires a finite number of states, so observations are discretized before learning.
---

## State Discretization

Each observation dimension is scaled and floored to create discrete bins:

```python
state[0] *= 2   # cart position
state[1] *= 2   # cart velocity
state[2] *= 5   # pole angle
state[3] *= 5   # pole angular velocity

obs = tuple(np.floor(state))

This version is structured specifically for a GitHub-style `README.md`, including a table of contents and a clear hierarchy.

---

# Q-Learning Algorithm

Q-Learning is a model-free, value-based Reinforcement Learning (RL) algorithm used to find the optimal action-selection policy for any given finite Markov Decision Process (MDP).

## Table of Contents

1. [Overview](https://www.google.com/search?q=%23overview)
2. [The Update Rule](https://www.google.com/search?q=%23the-update-rule)
3. [Action Selection](https://www.google.com/search?q=%23action-selection)
4. [Training vs. Evaluation](https://www.google.com/search?q=%23training-vs-evaluation)

---

## Overview

The algorithm learns an **action-value function** . This function represents the expected future rewards the agent will receive by taking action  in state  and following the optimal policy thereafter.

The goal of the agent is to populate a **Q-Table** where rows represent states and columns represent actions.

---

## The Update Rule

At every step, the agent updates its knowledge using the **Bellman Equation**. The update rule is defined as:

### Parameter Breakdown

| Parameter | Description | Purpose |
| --- | --- | --- |
|  | **Learning Rate** | Controls how much new rewards influence the existing Q-value. |
|  | **Discount Factor** | Represents the importance of future rewards (0 = short-sighted, 1 = long-term). |
|  | **Reward** | The immediate feedback received from the environment. |
|  | **Next State** | The state resulting from action . |
|  | **Max Future Reward** | The highest Q-value available in the next state. |

---

## Action Selection

To solve the **exploration-exploitation trade-off**, Q-learning uses an **-greedy policy**:

1. **Exploration (with probability ):** The agent selects a random action to discover new strategies and state transitions.
2. **Exploitation (with probability ):** The agent selects the action with the highest current Q-value to maximize its reward.

---

## Training vs. Evaluation

### Training Phase

* **Goal:** Populate the Q-table accurately.
* **Updates:** The Q-values are updated at every time step using the update rule above.
* **Policy:**  is usually high at the start and decays over time to transition from exploration to exploitation.

### Evaluation Phase

* **Goal:** Test the performance of the learned policy.
* **Updates:** No updates are made to the Q-table.
* **Policy:** The agent acts purely **greedily** ():



---

Would you like me to add a section with a Python implementation of this algorithm?
