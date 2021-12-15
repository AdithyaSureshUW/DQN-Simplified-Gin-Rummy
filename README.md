# DQN-Simplified-Gin-Rummy

## Project Description

### Abstract

Deep Q-Learning has been used to solve games such as Atari games, Go, Chess, etc.; however, this project strives to understand if Deep Q-Learning would be able to apply equally well to environments that do not provide all the game state information to a player. Specifically looking at Gin Rummy, a player is unable to know their opponent's hand and the order of the deck, making finding optimal plays more random compared to the games mentioned above. To understand how effective different implementations of Deep Q-Learning would be on environments that do not provide players with full knowledge of the game state, this project will run multiple implementations of Deep Q-Learning on a simplified Gin Rummy environment, which contains a significant amount of missing knowledge, and then evaluate how well each model performs compared to a random move agent.

### Problem Statement

This project aims to understand if a Deep Q-Learning model can be trained to play a simplified version of Gin Rummy, where players are not provided complete game state information.

### Definitions

- DQN: Deep Q-Network
- DDQN: Double Deep Q-Network

## Related Work

### References

- https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf
- http://people.csail.mit.edu/hongzi/content/publications/DeepRM-HotNets16.pdf

### Pre-Existing Work

My work was influenced by Maxwell De Jong's DQN work, https://maxwelldejong.com/data_science/lost_cities/, and one of the major sources of De Jong's work, Jaromir Janisch's DQN work, https://jaromiru.com/2016/10/21/lets-make-a-dqn-full-dqn/. 

Specifically, I took inspiration from the idea to apply a DQN to a card game with players not knowing all aspects of the game state. Then, I utilized Janisch's explanation alongside the article sources mentioned above to get a grasp on how Deep Q-Learning and Deep Q-Networks worked and were coded. I used Janisch's DQN and DDQN Model code as a basis for my work on this project.

### Modifications Made to Pre-Existing Work

The first significant change I made to the pre-existing work was creating the entire simplified Gin Rummy environment from scratch. When creating this environment, I had to understand the rules I wanted to implement for the simplified version of Gin Rummy, how much a state should be scored, the possible moves from a specific game state, how to update the environment given an action taken, etc. Next, after developing and testing the Gin Rummy environment, I had to modify the Brain model to adapt to my built environment. To do this, I made sure to perform a manual hyperparameter search to get suitable parameters for the model and try out various model architectures to verify which would work the best with the Gin Rummy environment. Furthermore, I had to modify the basic code for the DQNs to match how the environment stored different variables. Also, I had to create a function that would adequately represent the player's state rather than the game state so the DQN could use the correct information when trained and evaluated.

## Methodology

### Simplified Gin Rummy

To simplify the game of Gin Rummy, I decided to make the game a best of 1 and have it so a player can only win by obtaining Gin. This would mean a player would need 3 melds (sets or runs) and 1 meld having 4 cards to win. Furthermore, I scaled the reward of a state exponentially when more melds are contained within a hand as it increases the likelihood of winning by a lot. Then, I also emphasized having a meld of 4 cards because, from personal experience playing Gin Rummy, it is crucial to obtain a meld of 4. Finally, I made sure the reward of winning would definitely surpass the reward of any hand, so a trained agent should try any possible path to a victory state. Importantly, to train the model in a reasonable amount of time, I limited the number of game moves to 100. If the max number of moves has been played, the player with the highest score wins.

### Definitions

- Model Score: Reward of the Model
- Model Net Reward: (Model Score - Random Move Agent Score)

### Model Approach

For the Deep Learning model, I used a Sequential model that contained multiple Dense layers, each activated by the ReLU activation function. Initially, I used two Dense layers in my DQN Model. Then, looking at the training results with multiple hyperparameters, it seemed that a single layer would not be able to best find the features needed. Thus, I continued testing until I ended up using a total of 4 Dense layers within my Sequential Model for DQN. After performing a manual hyperparameter search for the DQN Model, I found hyperparameters that would let the DQN Model consistently have a winning record against a random move agent. 

Importantly, when making the DQN and following DDQN Models, I created a separate target network to set the targets for Gradient Descent for more stability in the results and updated that separate target network every 5 episodes. Another critical aspect in both the DQN and DDQN Models is the Lambda, or the Epsilon decay factor, which balances Model move exploration vs. acting in a greedy manner. For a model to perform well, it needs to explore many different states and then act in a greedy manner which is why I chose a very small Lambda. However, this means that likely most actions will be random, with the majority of greedy actions occurring later. Finally, I also used experience replay to better fine tune the network, and used a subset of experiences of size batch_size to update the DQN. Doing so allows the network to train and update based on a set of action data compared to updating the model for each action, improving the models stability.  

#### DQN vs DDQN Approach

Since the DQN Model was performing well when looking at win percentage but not showing consistent improvements in Model Score or Net Reward, I decided to implement a DDQN Model to verify if Deep Q-Learning can be applied to environments similar to the simplified Gin Rummy environment. To make a fair comparison, the only code I changed between the two models is the replay function, where I changed how to calculate the target Q values.

## Evaluation

To evaluate how well a model performed, I used simulations to understand how well a model was learning.

- Simulation 1: DQN Model vs. Random Move 
- Simulation 2: DDQN Model vs. Random Move

Due to the high amount of randomness that is inherent within the Gin Rummy Environment, I evaluated based on:

1. Model Reward Plot
2. Model Score Plot and Trend Line
3. Model Loss Plot
4. Percentage of Games Won by Model

In total, I ran each simulation 15 times, and I have shown sample plots for each simulation.

### DQN Simulation Evaluation

| DQN Model Reward Plot | DQN Model Score Plot | DQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| ![](/plots/plots_DQN/dqn_run1_net_rewards.png) | ![](/plots/plots_DQN/dqn_run1_score.png) | ![](/plots/plots_DQN/dqn_run1_losses.png) | 52%  | 
| ![](/plots/plots_DQN/dqn_run2_net_rewards.png) | ![](/plots/plots_DQN/dqn_run2_score.png) | ![](/plots/plots_DQN/dqn_run2_losses.png) | 55%  | 
| ![](/plots/plots_DQN/dqn_run3_net_rewards.png) | ![](/plots/plots_DQN/dqn_run3_score.png) | ![](/plots/plots_DQN/dqn_run3_losses.png) | 62%  | 

### DDQN Simulation Evaluation

| DDQN Model Reward Plot | DDQN Model Score Plot | DDQN Model Loss Plot | Percentage of Games Won |
| --- | --- | --- | --- |
| ![](/plots/plots_DDQN/ddqn_run1_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run1_score.png) | ![](/plots/plots_DDQN/ddqn_run1_losses.png) | 58%  | 
| ![](/plots/plots_DDQN/ddqn_run2_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run2_score.png) | ![](/plots/plots_DDQN/ddqn_run2_losses.png) | 53%  | 
| ![](/plots/plots_DDQN/ddqn_run3_net_rewards.png) | ![](/plots/plots_DDQN/ddqn_run3_score.png) | ![](/plots/plots_DDQN/ddqn_run3_losses.png) | 51%  | 

## Results

### DQN Model Results

The DQN Model results are hard to quantify as the learning done by the model was not seen in the evaluation. However, the DQN Model did have a winning record over the course of 100 episodes consistently over most of the simulations. Furthermore, the individual model score of the DQN Model sometimes showed an upward trend as more episodes passed but sometimes showed a downward trend. This makes it hard to infer if the model was really learning as intended. The DQN Model consistently had very high winning percentages over the Random Move agent. However, the lack of consistency of the model makes it hard to answer the problem statement.

### DDQN Model Results

Unlike the DQN Model, the DDQN Model showed both a trend in learning how to maximize the player's reward and held a winning record in the majority of simulations. The DDQN tends to be more stable in its rewards, leading to lower win percentages peaks than the DQN Model. However, this stability allows the DDQN Model to learn consistently, seen through the Model Score trend line, which showed a positive, upward trend. This consistent positive, upward-trending of the Model Score can be inferred to represent that the DDQN Model is learning and becoming more optimized.

### Result Summary

After reviewing the evaluation data, I believe that looking at the Model Score Trend Line is the best evaluation metric to verify how well a model is training because a Model's Net Reward and Win Percentage are influenced by the Random Move agent. Even though many actions during the training process are done for exploration, due to the large Lambda, looking at the trend line still shows how well the DQN / DDQN Model itself is training. Overall, I believe that a DQN model would not work consistently for the simplified Gin Rummy environment. In contrast, I believe that the DDQN model would produce consistently better results given more training time.

It is important to note that most of the actions done by both models are likely random, so even minor improvements appearing over 100 episodes show that the model is learning how to play the game more optimally. The consistent score improvements alongside a solid win percentage indicate a positive result for the DDQN model's training results.

Thus, the results show that some forms of Deep Q-Learning can be applied to environments where players do not possess knowledge of the entire game state.

## Future Possibilities

### Environment Improvements

The major update to the environment would be to finish the environment when the game truly ends, rather than a set number of moves. While this would cause the model to take much more time to train, it would allow the model to be able to better understand how to act in different scenarios and likely lead to better results. Also, more features could be added to the simplified Gin Rummy environment, such as being able to Knock, to make the game more complex. Then, one could see if DQN models could still perform in more complex environments where players do not have full game state knowledge.

### Model Improvements

Currently, the agent's Lambda value is very small, making it so that most of the actions are being done randomly, as Epsilon decreases slowly, with few of the moves being done in a greedy manner. This made it so that the agent explored many different possible states for a while, and only near the end of training did the model start acting in a more greedy manner. However, due to the limitations on the number of episodes that could be run as well as how long the training process took, I could not feasibly increase the Lambda or increase the number of episodes to a point where the model would be able to explore many possibilities while also acting greedily. Thus, training the agent for a much more extended period and continuously acting more greedily could produce better and more consistent results.
