# Report

## implementation

## environment details
For any reinforcement learning implementation, the agent has to interact with their environment. In this case, the environment is represented as a as a ping pong table with each agent controlling a paddle on either side.

### rewards
If the agent successfully hits the ball over the net, then it receives a reward of +0.1. In the event the agent hits the ball out of bounds or lets the ball hit the ground, then it receives a reward of -0.01.

### state space
The state space has to total of 8 variables that correspond to racket and ball position and velocity. Said observations are recieved by each agent separately.

### action space
Within the environment, the agent has two continuous actions available. The actions are represented as movement toward or away from the net and jumping.

### task success
In order to successfully complete this episodic task, the agents are required to obtain an average score of at least .5 over 100 consecutive episodes.

#### calculation explanation
At the end of each episode, each agent's rewards are added up to get two different scores. For each episode we take the maximum score. We solve the environment when the 100 episode average is at least 0.5.

## algorithm
### MADDPG
To train this agent, I utilized the MADDPG algorithm. MADDPG is an actor-critic method. Derivative of DDPG, MADDPG is known as an off-policy algorithm, but varies in its capability to solve environments with multiple agents. 

Different from the DQN, and similar to their predecessor the DDPG, the MADDPG are able to solve tasks in a continuous action space.

MADDPG also uses four different neural networks; rather than just an actor and a critic, this algorithm uses what is called a local actor as well as a target actor, and similarly for the agent; a local agent and a target agent.

The experience is stored at each training step. Each subsequent training step learns from a random sample of the stored experience. 
Per actor-cr-tic methods, the actor attempts to identify the optimal policy by estimating the state-action function from the critic and the critic estimate the optimal q-value function.

### hyper-parameters
- BUFFER_SIZE = int(1e6)  # replay buffer size
- BATCH_SIZE = 256        # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR_ACTOR = 1e-3         # learning rate of the actor 
- LR_CRITIC = 1e-3        # learning rate of the critic
- WEIGHT_DECAY = 0        # L2 weight decay
- LEARN_EVERY = 1         # update the networks 3 times after every timestep
- LEARN_NUMBER = 3        # update the networks 3 times after every timestep
- EPSILON = 1.0           # noise factor
- EPSILON_DECAY = 0.99    # noise factor decay
- CLIPGRAD = .1           # clip gradient parameter

### model architecture
#### actor
- input layer = 24
- fully connected hidden layer = 450 nodes, relu activation
- fully connected hidden layer = 350 nodes, relu activation
- ouput layer = 2 nodes, tanh activation

#### critic
- input layer = 24
- fully connected hidden layer = 256+2 nodes, relu activation
- fully connected hidden layer = 128 nodes, relu activation
- ouput layer = 1 node

## results
The agent was able to solve the environment after 331 episodes achieving an average maximum score of 0.5 over the last 100 episodes
of the training process.

I tuned the above parameters manually and randomly. 

## plot & performance
![image](https://user-images.githubusercontent.com/13371867/125478203-3087ce77-75fe-4809-89bc-bc29960efa09.png)
- Episode 0  Average_Score: 0.00
- Episode 50  Average_Score: 0.01
- Episode 100  Average_Score: 0.04
- Episode 150  Average_Score: 0.08
- Episode 200  Average_Score: 0.10
- Episode 250  Average_Score: 0.13
- Episode 300  Average_Score: 0.31
- Environment solved in 331 episodes!	Average_Score: 0.51

## improvements

- I've mentioned this before, but my hyper-parameter was largely a manual implementation of random search. Random can be ok, if somewhat controlled in a systematic fashion. I would have preferred to implement grid search or random search to determine hyper parameters in the end. The obvious challenge with something like that is that within the grid you would be testing and recording results for many training sessions which could easily take over a day given how long things currently take to run.
- After I wrap up this section, I hope to go back to the various lessons and reattempt the solutions with different algorithms. In this case, TD3 & SAC 

