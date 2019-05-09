
[//]: # (Image References)
[image1]:cont_control.gif  "Trained Agent"

# Project 2: Continuous Control

### Introduction

For this project, we work with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. The environment for this project involves controlling     
a **double-jointed arm**, to reach target locations.  A reward of +0.1 is provided for each step that the agent's hand         
is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many     
time steps as possible.  The accompanying research paper can be found [here](https://arxiv.org/pdf/1803.07067.pdf). For demonstrating the collective robot    
reinforcement learning see the [Googl AI Blog paper](https://ai.googleblog.com/2016/10/how-robots-can-acquire-new-skills-from.html).

![Trained Agent][image1]

The observation space (i.e., state space) has 33 dimensions corresponding to position, rotation, velocity, 
and angular velocities of the arm. The action space has 4 dimensions corresponding to torque applicable to two joints. 
Every entry in the action vector should be a number between -1 and 1.


### Environment

The environment is simulated by Unity application _Reacher_ lying in the subdirectory _Reacher_Windows_x86_64_.
We start the environment as follows:

      env = UnityEnvironment(file_name='Reacher_Windows_x86_64/Reacher.exe')

We consider for solving the version of the environment with 20 agents. In particular, our agents must get an average score       
of +30 (over 100 consecutive episodes, and over all agents). After each episode, we add up the rewards received by each    
agent, to get a score for each agent. This yields 20 (potentially different) scores. We then take the **average score**          
over all 20 agents. The environment is considered solved, when the average (over 100 episodes) of those average scores   
is at least +30. 

### Prepare environment on the local machine

You need at least the following three packages:

1. **deep-reinforcement-learning  (DRLND)**        
   The instructions to set up the DRLND repository can be found [here](https://github.com/udacity/deep-reinforcement-learning#dependencies). This repository contains material related to Udacity's [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) program.

2. **ml-agents  (ML-Agents Toolkit)**
   To set up the ML-Agents Toolkit for Windows you need to do following steps:
    
    2.1  Creating a new Conda environment:
    
       conda create -n ml-agents python=3.6
       
    2.2 Activating ml-agents by the following command:
    
       activate ml-agents
       
    2.3 Latest versions of TensorFlow won't work, so you will need to make sure that you install version 1.7.1:
    
       pip install tensorflow==1.7.1
       
    For details on installing the ML-Agents Toolkit, see the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation-Windows.md).     
    
3. **Unity environment _Reacher_**

    For this project, we not need to install Unity because the environment already built. For 20 agents, the environment     
    can be downloaded as follows:

   Windows (64-bit), [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)    
   Windows (32-bit), [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)     

   Download this environment zip into  **p2_continuous-control/** folder, and unzip the file.

### Train the Agent

   Run the notebook _Continuous_Control.ipynb_
   
   [1] import UnityEnvironment    
   [2] env = UnityEnvironment(file_name='Reacher_Windows_x86_64/Reacher.exe')   # create environment      
   [3] Environments contain _brains_ which are responsible for deciding the actions of their associated agents. 
       We check for the first brain available.      
   [4] Examine the State and Action Spaces. We get the information frame as follows:   
       
     Number of agents: 20   
     Size of each action: 4    
     There are 20 agents. Each observes a state with length: 33   
     The state for the first agent looks like: [ 0.00000000e+00 -4.00000000e+00  0.00000000e+00  1.00000000e+00    
        -0.00000000e+00 -0.00000000e+00 -4.37113883e-08  0.00000000e+00    
         0.00000000e+00  0.00000000e+00  0.00000000e+00  0.00000000e+00    
         0.00000000e+00  0.00000000e+00 -1.00000000e+01  0.00000000e+00    
         1.00000000e+00 -0.00000000e+00 -0.00000000e+00 -4.37113883e-08    
         0.00000000e+00  0.00000000e+00  0.00000000e+00  0.00000000e+00    
         0.00000000e+00  0.00000000e+00  5.75471878e+00 -1.00000000e+00    
         5.55726624e+00  0.00000000e+00  1.00000000e+00  0.00000000e+00   
        -1.68164849e-01]    
   
   [5]  Create _env_info_ and _agent_:

     env_info = env.reset(train_mode=True)[brain_name]      
     agent = Agent(state_size=state_size, action_size=action_size, random_seed=15)     


