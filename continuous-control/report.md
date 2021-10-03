# DDPG - Continous Control - Project Report

This solution impleents a Deep Deterministic Policy Gradient (DDPG) algorithm [
 [Silver et al. 2014](https://proceedings.mlr.press/v32/silver14.pdf), [Lillicrap et al. 2016](https://arxiv.org/abs/1509.02971)] to solve a continpus control task in which a 2 joint arm is tasked to reach and follow a target. DDPG is a policy gradient algorithm, meaning, it's ultimate goal is to directly learn the behaviour policy (the actor), the actor is then represented as a neural network. This is the opposite to Q-Learning which instead learns the $Q_\pi(s,a)$ (Q-Values) of each state-action pair and then apply an $\epsilon$-greedy policy to select actions. However, in DDPG, we have an Actor-Critic process in which a second network is used to calculate the $V_\pi(s)$ state value (the critic), which is used to evaluate how good an action selected by the actor is. Both networks are trained at the same time, from training experiences collected from the agent.

 The gradient of the actor (the policy) is calculated by evaluating the selected actions from given states against the critic values from the same states. The gradient of the critic is a loss function between the Q-values of the critic in the current state-actions and the Q-values under the same states but the actions predicted by the actor. By decoupling the Q-values calculation and the action selection, we aim to create a stable learning process.

 Despite the Actor-Critic process, this algorithm resembles the classic Q-learning because of the use of a replay buffer to learn from past experiences and still calculating Q-values. However, as stated in the beginning, the main purpose of this algorithm is to learn the policy, the Q-values are calculated just during training and to evaluate the actions selected by the policy network, which provides better learning stability.

## Network definition

Both actor and critic follow a similar network architecture. The differences between them are 1) the critic network needs to account for the actions taken to obtain the Q-value'2) the actor uses 'tanh' in the last layer, whereas the critic is just the linear function. The general architecture is as follows.

* Two fully connected linear layers of '256' and '128' units each.
* Inner layers activation function is `ReLu`.
* Actor uses `tanh` for final activation layer.
* Critic do not use activation function in the last layer.
* The optimizer used was Adam with its default values except for the learning rate.
* Use MSE loss for the actor.

## Replay buffer definition
We need to use the experience replay buffer. Hence the class below defines the minimal logic for a experience replay buffer.

## DDPG Agent
The DDPG agent logic includes mixing both the actor and the critic network as well as the action selection logic, and the learning process.

## Hyperparameters

This project run one experiment with hyper-parameters as follow:

### Neural Network training hyperparameters
* actor learning rate: `5e-4`
* critic learning rate: `5e-4`
* $\tau$ (soft updates): `1e-3`
* weight decay: 0



### DDPG parameters
* Max number of episodes for training: `10000`
* Max number of steps per episode: `1500`
* $\gamma$: 0.99

### Other parameters
* random seed: 123
* batch size: `128`
* Replay buffer size: `1e6`
* noise $\sigma$: `0.1`
* noise $\theta$: `0.15`

## Results
### DDPG Training output
```bash
1%|          | 101/10000 [17:37<28:46:55, 10.47s/it, Avg. Score=30.35]
```
Using the 20x agents environment, the task is solved in 101 episodes. This takes a bit longer for x1 agent as it needs more steps to get more samples to learn from. To achieve this result I struggled for a while with different implementations of the algorithm and different hyper-parameters. 

In the end, I discovered, by trial & error, that setting the same learning rates for both the actor and the critic to `5-e4` yield the best results, notice this is in contrast to the example learning rates from the course which most of the time recommended smaller learning rates for the actor. 

Another significant hyper-parameter change was the $\sigma$ value for the noise, the default value was `0.2` which in this case provoked too erratic behaviour of the arm leading it to barely get meaningful samples to learn from.

<div style="text-align:center">
<img src="./media/rewards-training.png" alt="Vanilla DQN"
	title="A cute kitten" width="450" height="300" />
</div>


### Concluding remarks

DDPG is a powerful algorithm for continuous control tasks and tasks with continous action spaces in general. This task was hard to solve in the beginning. Several trial & error sessions were needed to find the best hyper-parameters and tweaks to the original algorithm in order to make it work. Nevertherless, it is really envigorating when you finally solve the task and watch the agent to some progress. It would be interesting to see how other policy gradient algorithms and techniques compare against this one just for learning purposes.

### Future work
- Implement other PG algorithms and compare against this solution.
- Run more experiments and perform statistical analysis over the results.

### Credits
This solution was inspired by both [Udacity's pendulum solution](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum) & [Juan Carlos K](https://github.com/jckuri/DeepRL-Continuous-Control) adaptation to the reacher environment

### References
- Udacity - Deep Reinforcement Learning - Nano Degree: https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893
- Deterministic Policy Gradient Algorithms, [Silver et al. 2014](https://proceedings.mlr.press/v32/silver14.pdf)
- Continuous Control With Deep Reinforcement Learning, [Lillicrap et al. 2016](https://arxiv.org/abs/1509.02971)