# collaboration_and_competition_maddpg

As part of the Deep reinforcement learning nano degree with Udacity, this is an implementation of the DQN algorithm to train an agent how to optimally maximize yellow banana collection. 

## environment details
For any reinforcement learning implementation, the agent has to interact with their environment. In this case, the environment is represented as a large square floor with blue and yellow bananas scattered throughout. 

### rewards
Per the agent's action, the agent is rewarded according to banana collection; -1 for a blue banana collected and +1 for a yellow banana collected.

### state space
The state space has to total of 37 dimensions and keeps information on the velocity of the agent, as well a ray based perception of objects in front of the agent.

### action space
Within the environment, there is a discrete action space of 4. At any point in time, the agent is able 1. move forward, 2. move right, 3. move backwards, or 4. move left.

### task success
In order to successfully complete our episodic task, the agent is required to obtain an average score of at least 13 bananas over 100 episodes.

## Dependencies & requirements to get started

1. To get up and running, you'll want to download the defined Udacity dependencies [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)

2. You'll need to grab the following:
    - Unity ML agents: [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md)
    - NumPy: [here](http://www.numpy.org/) 
    - PyTorch: [here](https://pytorch.org/) 

3. Next you'll need the navigation simulation. Download the environment that corresponds to your operating system. 
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.
    
4. Move the downloaded file to the `p1_navigation/` folder in the DRLND repository. Decompress the file and you'll be ready to go. 

5. Navigate to the `Navigation.ipynb` and load the file using the drlnd kernel. 

Credit to Udacity for collating the above resources
