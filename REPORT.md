# Collaboration and Competition Project Report

## Learning Algorithm

I've used MADDPG (Multi Agent Deep Deterministic Policy Gradient). .Multi-Agent Deep Deterministic Policy Gradient (MADDPG) algorithm is a new population DRL algorithm. It can find the global optimization solution and can easily defeat various DRL methods, including DQN (Deep Q-Network), TRPO (Trust region policy optimization) and DDPG (Deep Deterministic Policy Gradient). MADDPG is a kind of "Actor-Critic" method. Unlike DDPG algorithm which trains each agent independantly, MADDPG trains actors and critics using all agents information (actions and states). However, the trained agent model (actor) can make an inference independentaly using its own state.

## Architecture

The architecture of the model has two networks, one for the actor and the other for the critic.

Two hidden units for each of the actor and critic networks. Added batchnorm after the first hidden layer of both the networks. For actor:

* Fully connected layer - input size is 24(state size) and output is 256 activation used is RELU
* Fully connected layer - input size is 256 and output is also 128 activation used is RELU
* Fully connected layer - input size is 128 and output is 2(action size) activation used is tanh

For critic:

* Fully connected layer - input size is 24(state size) and output is 256 activation used is RELU
* Fully connected layer - input size is 258 and output is also 128 activation used is RELU
* Fully connected layer - input size is 128 and output is 1

## Hyperparameters

```
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 256        # minibatch size
UPDATE_FREQ = 1

GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR_ACTOR = 1e-4         # learning rate of the actor 
LR_CRITIC = 3e-4        # learning rate of the critic
WEIGHT_DECAY = 0        # L2 weight decay

NOISE_REDUCTION_RATE = 0.99
EPISODES_BEFORE_TRAINING = 500
NOISE_START=1.0
NOISE_END=0.1
```

## Training Plot
![](https://github.com/gouthamcm/Tennis/blob/main/plot_tennis.png)

## Training Results

```

0 episode	avg score 0.10000	max score 0.10000
500 episode	avg score 0.10260	max score 0.10000
866 episode	avg score 0.50450	max score 2.10000
Environment solved after 866 episodes with the average score 0.5045000075735152
```

## Future Scopes

I would like to fine tune the hyperparameters to bring a stable learning for the agent. Also, try out other algorithms such as PPO on this task.  
