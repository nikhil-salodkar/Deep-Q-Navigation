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
