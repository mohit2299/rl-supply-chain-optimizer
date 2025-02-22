# Resilient Supply Chain Optimization with Reinforcement Learning

## Overview
This repository contains an end-to-end project that simulates a supply chain environment and uses a Deep Q-Network (DQN) agent implemented in PyTorch to optimize production decisions. The agent learns to minimize overall costs—including production, inventory holding, and shortage penalties—while handling random disruptions and seasonal demand variations.

## Project Description
In this project, we simulate a simplified supply chain comprising:
- **A Factory:** Produces goods with a chance of disruption (i.e., production may occasionally drop to zero).
- **A Warehouse:** Stores produced inventory.
- **Customer Demand:** Generated at each time step with seasonal fluctuations.

At each time step, the agent selects a production multiplier (0, 1, or 2) which directly affects the number of units produced. The environment calculates the cost incurred based on:
- **Production Cost:** Cost per unit produced.
- **Holding Cost:** Cost for keeping inventory.
- **Shortage Penalty:** Extra cost if available inventory is insufficient to meet demand.

The agent's goal is to learn a policy that minimizes these costs by maximizing the negative cost (i.e., the reward).

## Environment and Agent
- **Supply Chain Environment (`SupplyChainEnv`):**  
  A custom Gym environment that simulates the dynamics of the supply chain, including random production disruptions and seasonal demand changes.
  
- **Deep Q-Network (DQN) Agent:**  
  - Implements a neural network to estimate Q-values for each action based on the current state (inventory and seasonal factor).
  - Uses an epsilon-greedy strategy to balance exploration and exploitation.
  - Stores past experiences in a replay buffer to stabilize training.
  - Periodically updates a target network to further stabilize learning.

## Features
- **Simulation of Realistic Scenarios:**  
  The environment models random production disruptions and seasonal variations in demand.
- **Reinforcement Learning:**  
  Utilizes a DQN agent to learn optimal production strategies that minimize costs.
- **Comprehensive Cost Metrics:**  
  Incorporates production, holding, and shortage costs into the reward function.
- **Training Summary:**  
  At the end of training, the script outputs the final average reward (negative cost) over the last 50 episodes and the final epsilon value.

## Requirements
- Python 3.x
- [Gym](https://gym.openai.com/)
- [PyTorch](https://pytorch.org/)
- [NumPy](https://numpy.org/)

You can install the required packages via pip:
```bash
pip install gym torch numpy

