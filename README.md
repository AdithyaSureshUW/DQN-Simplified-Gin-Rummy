# DQN-Simplified-Gin-Rummy

## Project Description

### Background of Deep Q-Learning

### Abstract

Deep Q-Learning has been used to solve games such as Atari games, Go, Chess, etc., however, this project strives to understand if Deep Q-Learning would be able to apply equally well to environemnts that do not provide all the gamestate information to a player. Specifically looking at Gin Rummy, a player is unable to know their opponents hand and the order of the deck, making finding optimal plays more random compared to the games mentioned above. To understand how effective different implementations of Deep Q-Learning would be on environments that do not provide players with full knowledge of the gamestate, this project will run multiple implementations of Deep Q-Learning on a simplified Gin Rummy environment, which contains a significant amount of missing knowledge, and then evaluate how well each model performs compared to a random move agent.

### Problem Statement

The problem this project aims to solve to is to understand if a Deep Q-Learning model can be trained to play a simplified version of Gin Rummy, where players are not provided full gamestate information. 

## Related Work

### References

- https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf
- http://people.csail.mit.edu/hongzi/content/publications/DeepRM-HotNets16.pdf

### Pre-Existing Work

My work was influenced by Maxwell De Jong's DQN work, https://maxwelldejong.com/data_science/lost_cities/, as well as one of the major sources of the De Jong's work, Jaromir Janisch's DQN work, https://jaromiru.com/2016/10/21/lets-make-a-dqn-full-dqn/. 

Specifically, I took inspiration of the idea to apply a DQN to a card game with players not knowing all aspects of the gamestate. Then, I utilized Janisch's explaination alongside the article sources mentioned above to get a grasp on how Deep Q-Learning and Deep Q-Networks worked and were coded. I used Janisch's DQN and DDQN Model code as a basis for the work I did on this project.

### Modifications Made to Pre-Existing Work

The first major change I made to the pre-existing work was creating the entire simplified Gin Rummy environment from scratch. When creating this environment, I had to understand the rules I wanted to implement for the simplified version of Gin Rummy, how much a state should be scored, the possible moves from a specific gamestate, how to update the environment given an action to take, etc. Next, after developing and tested the Gin Rummy environment, I had to modify the Brain model to adapt to the environment I built. To do this, I made sure to perform a manual hyperparameter search to get good parameters for the model as well as try out various model architecture to verify which would work the best with the Gin Rummy environment. Furthermore, I had to make modifications to the basis code for the DQNs in order to match how the environment stored different variables. Also, I had to make sure to create a function that would properly represent player's state rather than the gamestate so the DQN could use the proper information when bring trained and evaluated.

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

### DQN Simulation Evaluation

| DQN Model Reward Plot | DQN Model Score Plot | DQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| ![](/plots/plots_DQN/dqn_run1_net_rewards.png) | ![](/plots/plots_DQN/dqn_run1_score.png) | ![](/plots/plots_DQN/dqn_run1_losses.png) | 52%  | 
| ![](/plots/plots_DQN/dqn_run2_net_rewards.png) | ![](/plots/plots_DQN/dqn_run2_score.png) | ![](/plots/plots_DQN/dqn_run2_losses.png) | 55%  | 
| ![](/plots/plots_DQN/dqn_run3_net_rewards.png) | ![](/plots/plots_DQN/dqn_run3_score.png) | ![](/plots/plots_DQN/dqn_run3_losses.png) | 62%  | 

### DDQN Simulation 2 Evaluation

| DDQN Model Reward Plot | DDQN Model Score Plot | DDQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| ![](/plots/plots_DDQN/ddqn_run1_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run1_score.png) | ![](/plots/plots_DDQN/ddqn_run1_losses.png) | 58%  | 
| ![](/plots/plots_DDQN/ddqn_run2_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run2_score.png) | ![](/plots/plots_DDQN/ddqn_run2_losses.png) | 53%  | 
| ![](/plots/plots_DDQN/ddqn_run3_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run3_score.png) | ![](/plots/plots_DDQN/ddqn_run3_losses.png) | 51%  | 

## Results

### DQN Model Results

The DQN Model results are hard to quantify as the learning done by the model was not seen in the evaluation, but the DQN Model did have winning record over the course of 100 episodes consistenly over the majority the simulations. Furthermore, the individual model score of the DQN Model sometimes showed an upward trend as more episodes passes, but also sometimes showed a downward trend. This makes it hard to infer if the model was really learning as intended. The DQN Model did consistently have very high winning percentages over the Random Move agent, but the lack of consistency of the model makes it hard to answer the problem statement.

### DDQN Model Results

Unlike the DQN Model, the DDQN Model showed both a trend in learning how to maximize the reward of the player and held a winning record in the majority of simulations. Commpared to the DQN Model, the DDQN tends to be more stable in the rewards it provides leading to lower win percentages peaks compared to the DQN Model. However, this stability allows the DDQN Model to learn in a conistent manner as seen through the Model Score trend line which showed a positive, upward trend. This consistent positive, upward trending can be inferred to represent that the DDQN Model is learning and becoming more optimized.

### Result Summary

After revewing the evaluation data, I believe that looking at the Model Score Trend Line was is the best evaluation metric to use to verify how well a model is training because a Model's Net Reward and Win Percentage are are influenced by the Random Move agent. Overall , I believe that as a DQN model would not work consistently for the simplified Gin Rummy environment, while the DDQN model would produce consistently better results given more training time.

Thus, the results show that some forms of Deep Q-Learning are able to be applied to environments where players do not possess knowledge of the entire gamestate.

## Future Improvements

### Environment Improvements

### Model Improvements


