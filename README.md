# DQN-Simplified-Gin-Rummy

## Methodology

### Definitions

Model Score: Reward of the Model
Model Reward: (Model Score - Random Move Score)

## Evaluation

To evalute how well a model performed, I used simulations to understand how well a model was learning.

- Simulation 1: DQN Model vs Random Move 
- Simulation 2: DDQN Model vs Random Move

Due to the high amound of randomness that is inherent within the Gin Rummy Environment, I based my evalutaions on:

1. Model Reward Plot
2. Model Score Plot and Trend Line
3. Percentage of Games Won by Model

## Results

### Simulation 1 Results

| DQN Model Runs | DQN Model Reward Plot | DQN Model Score Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| Run 1 | img  | img  | 55%  | 
| Run 2  | img | img  | 60%  | 

### Simulation 2 Results

| DDQN Model Runs | DDQN Model Reward Plot | DDQN Model Score Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| Run 1 | img  | img  | %  | 
| Run 2  | img | img  | %  | 

### Key Observations

In total, I ran the each simulation around 10 times. 

The key observations I understood were that:
- The average reward of the DQN Model was very variable, however, regardless of the average reward the DQN did win the majority of games against a player making Random Moves.
