# DQN-Simplified-Gin-Rummy

## Project Description

### Background of Deep Q-Learning

### Abstract

Deep Q-Learning has been used to solve games such as Atari games, Go, Chess, etc., however, this project strives to understand if Deep Q-Learning would be able to apply equally well to environemnts that do not provide all the gamestate information to a player. Specifically looking at Gin Rummy, a player is unable to know their opponents hand and the order of the deck, making finding optimal plays more random compared to the games mentioned above. To understand how effective different implementations of Deep Q-Learning would be on environments that do not provide players with full knowledge of the gamestate, this project will run multiple implementations of Deep Q-Learning on a simplified Gin Rummy environment, which contains a significant amount of missing knowledge, and then evaluate how well each model performs compared to a random move agent.

### Problem Statement

The problem this project aims to solve to is to understand if a Deep Q-Learning model can be trained to play a simplified version of Gin Rummy, where players are not provided full gamestate information. 

## Methodology

### Definitions

- Model Score: Reward of the Model
- Model Net Reward: (Model Score - Random Move Agent Score)

### Initial Approachs

### Finalized Approach

## Evaluation

To evalute how well a model performed, I used simulations to understand how well a model was learning.

- Simulation 1: DQN Model vs Random Move 
- Simulation 2: DDQN Model vs Random Move

Due to the high amound of randomness that is inherent within the Gin Rummy Environment, I evalutaioned based on:

1. Model Reward Plot
2. Model Score Plot and Trend Line
3. Model Loss Plot
4. Percentage of Games Won by Model

## Results

### Simulation 1 Results

| DQN Model | DQN Model Reward Plot | DQN Model Score Plot | DQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- | --- |
| Sample Run 1 | img  | img  | img | %  | 
| Sample Run 2  | img | img  | img | %  | 

### Simulation 2 Results

| DDQN Model | DDQN Model Reward Plot | DDQN Model Score Plot | DDQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- | --- |
| Sample Run 1 | img  | img  | img | %  | 
| Sample Run 2  | img | img  | img | %  | 

### Key Observations

In total, I ran the each simulation 10 times. 

The key observations I understood were that:
- The average reward of the DQN Model was very variable, <br/> However, regardless of the average reward, the DQN won the majority of games playing against Random Moves.
- The DDQN Model, which accounts for the next state action, performs worse than a normal DQN Model consistently when looking at Model Reward and winning percentage.

### Understanding Observations


