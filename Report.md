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
At the end of each episode, each agent's rewards are added up to get two different scores. For each episode we take the maximum score. We solve the environment when the 100 episode average is at least +0.5.

## algorithm
### MADDPG
To train this agent, I utilized the MADDPG algorithm. MADDPG is an actor-critic method. Derivative of DDPG, MADDPG is known as an off-policy algorithm, but varies in its capability to solve environments with multiple agents. 

Different from the DQN, and similar to their predecessor the DDPG, the MADDPG are able to solve tasks in a continuous action space.

MADDPG also uses four different neural networks; rather than just an actor and a critic, this algorithm uses what is called a local actor as well as a target actor, and similarly for the agent; a local agent and a target agent.

The experience is stored at each training step. Each subsequent training step learns from a random sample of the stored experience. 
Per actor-crotic methods, the actor attempts to identify the optimal policy by estimating the state-action function from the critic and the critic estimate the optimal q-value function.

### hyper-parameters
The following hyperparameters were used:
- replay buffer size: 1e5
- max timesteps: 10000 (all episodes get shutdown after 10000 timesteps)
- minibatch size: 128
- discount factor: 0.99
- tau (soft update for target networks factor): 1e-3
- learning rate: 1e-4 (actor) and 1e-3 (critic)
- update interval (how often to learn): 1
- beta start (factor for the noise added to the actions selected by the actor): 1.0
- beta decay factor: 0.995
- min beta: 0.01

### model architecture
#### actor
- feed forward network
- Batch normalization
- Input layer: 24 (input) neurons (the state size)
- 1st hidden layer: 128 neurons (leaky relu)
- 2nd hidden layer: 128 neurons (leaky relu)
- output layer: 2 neurons (1 for each action) (tanh)

#### critic
- Batch normalization
- Input layer: 24 (input) neurons (the state size)
- 1st hidden layer: 132 neurons (action with 2 * action_size 2 added) (leaky relu)
- 2nd hidden layer: 128 neurons (leaky relu)
- output layer: 1 neuron

## Results
The agent was able to solve the environment after 467 episodes achieving an average maximum score of 0.51 over the last 100 episodes
of the training process.











### hyper-parameters

- n_episodes: maximum number of training episodes (1000)
- max_t: maximum number of timesteps per episode  (500)
- eps_start: starting value of epsilon, for epsilon-greedy action selection (0.5)
- eps_end: minimum value of epsilon  (0.01)
- eps_decay: multiplicative factor (per episode) for decreasing epsilon (.97)

- BUFFER_SIZE: the size of the replay buffer (1e5)
- BATCH_SIZE: size of the mini batch (64)
- GAMMA: our discount factor (.99)
- TAU: target parameters soft update (1e-3)
- Learning Rate: the learning rate  we use (5e-4)
- UPDATE_EVERY: network update frequecy (4)

I tuned the above parameters manually and randomly. It didn't take too long before I was successfully solving the environment in about 300 episodes. I was super excited in my last run to solve it in 108 episodes.

### model architecture
Because of the state space, my neural network takes a 37 by 1 vector from the environment. My output layer includes 4 outputs, 1 corresponding to each action in the action space. There are also 64 nodes in each of the two hidden layers.

## plot & performance
![image](https://user-images.githubusercontent.com/13371867/123744365-e5985c80-d86b-11eb-9c00-0676df93dc08.png)
- Episode 100	Average Score: 12.19
- Episode 108	Average Score: 13.02
- Environment solved in 108 episodes!	Average Score: 13.02

## improvements

- My hyper-parameter was largely a manual implementation of random search. Random can be ok, if somewhat controlled in a systematic fashion. I would have preferred to implement grid search or random search to determine hyper parameters in the end.

- To mitigate action value over-estimation; I would like to implement Double Q-Learning.

- Rather than uniform sampling from experience, I could use prioritized experience replay to increase the frequency of higher importance experience. 
