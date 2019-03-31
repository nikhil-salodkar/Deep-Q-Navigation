# Report

## Introduction

In this project our goal is to train an agent which would be able to explore a large square world consisting of yellow
and blue bananas and learn to collect as much cumulative reward as possible in an episode.

According to the environment each **yellow banana gives a reward of +1 and each blue banana gives a reward of -1**. Thus, the
agent will have to learn to collect as many yellow bananas as possible simultaneously avoiding as many blue bananas as possible
to get as high as possible cummulative reward in a fixed timed episode.

The environment provides a simplified state space having 37 dimensions containing the agent's velocity, along with ray-based
perception of objects around agent's forward direction.

**There are four actions** available which could be taken by the agent:
  - 0 Move forward
  - 1 Move backward
  - 2 Turn lef
  - 3 Turn right
  
The goal is to train the agent so that it would be able to achieve at least 13 score as reward on average over more than 100 episodes.

## Learning Techniques

Since, **we have small number of discrete set of actions that the agent can take, Q learning seems to be a great fit to train our agent**.
Also, since the state space has got continuous values, traditional tabular based method such as tabular monte carlo does not fit well.
Thus, Deep Q Learning will help in approximating the table well.

### Deep Q Learning

This is a type of Model free, Value based reinforcement learning technique in which we use a Neural Network to approximate a
function which would be able to estimate value of a state-action pair. Given a state as input the Neural Network outputs the
estimated value of each of the action. Our goal in training is thus to adjust the neural network weights in such a manner that
for each state the network is able to output high values for actions that would result in better cumulative future rewards compared
to actions that would result in poor cumulative future rewards. To train the network, we thus use Temporal Difference Error and try
to minimize the same.

Some improvements which are necessary for applying Q Learning technique on Neural Networks to make the training stable include the technique of using Experience Replay and Fixed targets.

  1. **Experience Replay**: In this technique instead of taking experince samples of agent as an agent is interacting with envrionment in a consecurive manner, we store the agent's experience at each time step in a tuple of four values (S<sub>t</sub>, A<sub>t</sub>, R<sub>t</sub>, S<sub>t+1</sub>) in a Dataset D pooled over many episodes into a replay memory. Then during training a batch of tuples are randomly selected to be used as candidates for training. This approach has several advantages over standard Q-learning. First, each step of experience is potentially used in many weight updates, which allows for greater data efficiency. Second, learning directly from consecutive samples is inefficient, owing to the strong correlations between the samples; randomizing the samples breaks this correlations and therefore reduces the varience of the updates.
  
  2. **Fixed Targets/ Soft Update**: In this improvement, we use a seperate network for generating the targets in the Q-learning update. Every few updates we clone the network Q to obtain a target network Q' and use Q' for generating the Q-learning targets. This modification makes the algorithm more stable compared to standard online Q-learning and reduces oscillations or divergence of policy. In this project we have used a varient of fixed target method instead which is called soft update of target network, where instead of copying the Q Network parameters into target network in every C steps, the target network is softly updated means slowly updated at each interval.
  
  3. **Double DQN**: **This method handles the problem of the overestimation of Q-values**. To calculate TD target, we face a problem: how are we sure that the best action for the next state is the action with the highest Q-value? We know that the accuracy of Q value depends on what action we tried and what neighboring states we explored. As a consequence, at the beginning of the training we don't have enough information about the best action to take. Thus, we decouple action selection from the target Q value generation. To calculate TD target, we use DQN network to select what is best action to take for the next state (the action with hightest Q value). And use our target network to calculate the target Q value of taking that action at next state. We have used this technique in this project to help hasten the agent's learning.
 
### Neural Network Architecture

In this project, to train the model, the neural network architecture is very simple. **Input layer consist of 37 input neurons** to get 37 dimensional input state. Then, **there are two hidden layers each of 32 neurons which are fully connected** in a feed forward manner. Then, **the output layer consist of 4 neurons** each one represending an action which the agent can take. Both of the hidden layers have ReLu as their output activation functions. The output layer since emits regression values does not need any activation function at its output.

### Hyperparameters

The important hyperparameter values which we have used are:
  - BUFFER_SIZE : 100000 Size of the replay buffer size
  - BATCH_SIZE : 64 Batch of experiences which are used for updating network weights
  - GAMMA : 0.99 Discount factor
  - TAU : 0.001 For soft update of target parameters. Used in place of fixed target technique.
  - LR : 0.0001 Learning rate
  
### Results

The agent was trained first using Deep Q Learning with experienced replay and soft update technique only. Then, adding Double DQN technique to existing techniques. The comparision results of both these approaches can be seen in the below graphs:
  
  
