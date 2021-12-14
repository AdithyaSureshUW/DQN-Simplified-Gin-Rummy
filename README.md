# DQN-Simplified-Gin-Rummy

## Project Description

### Background of Deep Q-Learning

### Abstract

Deep Q-Learning has been used to solve games such as Atari games, Go, Chess, etc., however, this project strives to understand if Deep Q-Learning would be able to apply equally well to environemnts that do not provide all the gamestate information to a player. Specifically looking at Gin Rummy, a player is unable to know their opponents hand and the order of the deck, making finding optimal plays more random compared to the games mentioned above. To understand how effective different implementations of Deep Q-Learning would be on environments that do not provide players with full knowledge of the gamestate, this project will run multiple implementations of Deep Q-Learning on a simplified Gin Rummy environment, which contains a significant amount of missing knowledge, and then evaluate how well each model performs compared to a random move agent.

### Problem Statement

The problem this project aims to solve to is to understand if a Deep Q-Learning model can be trained to play a simplified version of Gin Rummy, where players are not provided full gamestate information. 

## Related Work

### Pre-Existing Work

### Modifications Made to Pre-Existing Work

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

Due to the high amound of randomness that is inherent within the Gin Rummy Environment, I evaluated based on:

1. Model Reward Plot
2. Model Score Plot and Trend Line
3. Model Loss Plot
4. Percentage of Games Won by Model

In total, I ran the each simulation 15 times, and I have shown a sample plot for each simulation.

### Simulation 1 Evaluation

| DQN Model Reward Plot | DQN Model Score Plot | DQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| img  | img  | img | 55%  | 
| img  | img  | img | 62%  | 

### Simulation 2 Evaluation

| DDQN Model Reward Plot | DDQN Model Score Plot | DDQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| img  | img  | img | 53%  | 
| img  | img  | img | 51%  | 

## Results

### DQN Model Results

The DQN Model results are hard to quantify as the learning done by the model was not seen in the evaluation, but the DQN Model did have winning record over the course of 100 episodes consistenly over the majority the simulations. Furthermore, the individual model score of the DQN Model sometimes showed an upward trend as more episodes passes, but also sometimes showed a downward trend. This makes it hard to infer if the model was really learning as intended , which could indicate that it was learning how to maximize the reward of the player, even without having full gamestate knowledge.

### DDQN Model Results

Unlike the DQN Model, the DDQN Model showed both a trend in learning how to maximize the reward of the player and held a winning record in the majority of simulations. Commpared to the DQN Model, the DDQN tends to be more stable in the rewards it provides leading to lower win percentages peaks compared to the DQN Model. However, this stability allows the DDQN Model to learn in a conistent manner as seen through the Model Score trend line which showed a positive, upward trend that can be inferred to represent the optimization of the DDQN Model.

### Result Summary

After revewing the evaluation data, I believe that looking at the Model Score Trend Line was is the best evaluation metric to use to verify how well a model is training because a Model's Net Reward and Win Percentage are are influenced by the Random Move agent. Thus, I believe that as a DQN model would not work consistently for the simplified Gin Rummy environment, while the DDQN model shows that it could produce consistently better results given more training time.

## Future Improvements

### Environment Improvements

### Model Improvements


