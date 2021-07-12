# collaboration_and_competition_maddpg

As part of the Deep reinforcement learning nano degree with Udacity, this is an implementation of the MADDPG algorithm to train two agents to successfully hit a ping pong ball over the net and return the opposing agent's hit without letting the ball hit the ground. Contrary to typical ping pong, the goal in this case is to keep the ball in play.

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

## Dependencies & requirements to get started

1. To get up and running clone [this repository](https://github.com/0Zeta/Udacity-Collaboration-and-Competition) 
2. Download the defined Udacity dependencies [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)
3. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
4. You'll need to grab the following:
    - Unity ML agents: [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md)
    - NumPy: [here](http://www.numpy.org/) 
    - PyTorch: [here](https://pytorch.org/) 
5. Place the file in this GitHub repository and unzip (or decompress) the file
4. Move the downloaded file to the `p3_collab-compet/` folder in the DRLND repository. Decompress the file and you'll be ready to go. 
5. Navigate to the `Tennis.ipynb` and load the file using the drlnd kernel. 

Credit to Udacity for collating the above resources
