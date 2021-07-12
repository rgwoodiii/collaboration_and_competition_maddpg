# Report

## implementation

### environment details
For any reinforcement learning implementation, the agent has to interact with their environment. In this case, the environment is represented as a large square floor with blue and yellow bananas scattered throughout. 

### rewards
Per the agent's action, the agent is rewarded according to banana collection; -1 for a blue banana collected and +1 for a yellow banana collected.

### action space
Within the environment, there is a discrete action space of 4. At any point in time, the agent is able 1. move forward, 2. move right, 3. move backwards, or 4. move left.

## algorithm

### DQN
To train this agent, I utilized the DQN algorithm. The agent will perform an action on the current state according to epsilon-greedy valies. The algorithm performs episodic training until the pre-specified number of episodes has been satisfied or  the agent has solved the environment. (The environment is solved when the average reward over 100 episodes reaches at least 13.) This algorithm utilizes a replay buffer.

Episodes run until the maximum time steps parameter (max_t) has been reached.

Per the udacity deep reinforcement learning course, the dqn algorithm at first was made for solving video game environments. The DQN approximates the state-value function through the use of a neural network. There are a couple of key processes that are standard for DQNs. DQNs makes use of experienced replay and fixed Q targets. 

Experienced replay is the act of sampling 'observed experience' from our environment. After being saved in replay memory, experiences are subsequently randomly sampled from our replay memory and incorporated in our learning.

Fixed Q targets means that we optimize our network towards a static target network. 

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
