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

In total, I ran the each simulation 10 times, and I have shown a sample plot for each simulation.

### Simulation 1 Evaluation

| DQN Model Reward Plot | DQN Model Score Plot | DQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| img  | img  | img | 55%  | 

### Simulation 2 Evaluation

| DDQN Model Reward Plot | DDQN Model Score Plot | DDQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| img  | img  | img | 53%  | 

## Results

Overall, the DQN Model did show that it learned as it was trained on more scenarios and performed adequately. The DQN Model was able to have a winning record over the course of 100 episodes consistenly over all the simulations. Furthermore, the individual model score of the DQN Model did show an upward trend as more episodes passes, which could indicate that it was learning how to maximize the reward of the player, even without having full gamestate knowledge. Similar to the DQN Model, the DDQN Model also showed a trend in learning how to maximize the reward of the player and winning record. Commpared to the DQN Model, the DDQN tends to be more stable in the rewards it provides and has less peaks compared to the DQN Model. 

One key note to add onto the evaluation is that in other simulations, both models had cases where their Model Score trend line went down. Furthremore, in most cases the net reward gained for each model still fluxuated greatly and showed no real trend. Thus, I found it very interesting that, regardless of the lack of trend in Net Reward and not having a guarenteed positive Model Score trend, the models consistently showed having a winning record.

## Future Improvements

### Environment Improvements

### Model Improvements


