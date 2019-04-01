# Deep Q Navigation

## Introduction

In this project we will train an agent to navigate and collect as many good bananas as possible in an episode in a large square world.
The environment and a trained agent looks like this:

![Alt Text](https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif)


The simulated environment is Unity based wherein the agent has to collect as many yellow bananas as possible avoiding blue bananas.
**A reward of +1 is received for collecting one yellow banana and a reward of -1 is received for collecting a blue banana.** Thus, the goal is to receive the highest cumulative reward in an episode.

The simulated environment provides a simplified **state space having 37 dimensions** containing the agent's velocity, along with ray-based perception of objects around agent's forward direction. Given this information the agent will learn how to best selection actions to try to achieve maximum cumulative reward. **There are four discrete actions available :**
  - 0 move forward
  - 1 move backward
  - 2 turn left
  - 3 turn right

We will assume the environment solved when the agent is able to achieve more than 13 score on average over more than 100 episodes.

## Installation Instructions

1. Download the appropriate Unity environment according to the operating system:
    - Linux: [Click Here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX : [Click Here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit) : [Click Here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit) : [Click Here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    You can use the above downloaded environment to see view how a trained agent behaves in the given envrionment setup.

2. Since the project is developed using Python and Pytorch some necessary packages need to be installed. Install the necessary libraries and packages mentioned in **requirements.txt**. To install the necessary packages either use pip or create a new conda environment and install the minimum required packages as mentioned in the requirements file. To set up a python environment to run code using conda, you may follow the instructions below:

    Create and activate a new environment with Python 3.6 and install dependencies
    
    - Linux or Mac:
      ```
      conda create --name env-name python=3.6
      source activate env-name
      ```
    
    - Windows:
      ```
      conda create --name env-name python=3.6
      activate env-name
      ```
  
    - Then install the dependecies using 
      ```
      pip install -r requirements.txt
      ```
3. To use unity agent Unity environment will have to be installed. Follow the instructions in this [link](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md)

4. Run the cells in Jupyter notebook to train a new agent on this environment. Pretrained agent's weights are also present in weights folder.
