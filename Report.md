# Report

## Introduction

In this project our goal is to train an agent which would be able to explore a large square world consisting of yellow
and blue bananas and learn to collect as much cumulative reward as possible in an episode.

According to the environment each **yellow banana gives a reward of +1 and each blue banana gives a reward of -1**. Thus, the
agent will have to learn to collect as many yellow bananas as possible simultaneously avoiding as many blue bananas as possible
to get as high as possible cummulative reward in a fixed timed episode.

**There are four actions** available which could be taken by the agent:
  - 0 Move forward
  - 1 Move backward
  - 2 Turn lef
  - 3 Turn right
  
The goal is to train the agent so that it would be able to achieve at least 13 score as reward on average over more than 100 episodes.

## Learning Techniques

Since, we have small number of discrete set of actions that the agent can take 
