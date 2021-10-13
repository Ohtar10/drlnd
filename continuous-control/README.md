# RL - Continuous Control task with DDPG

<div style="width: 100%; display: table;">
    <div style="text-align:center; display: table-row;">
        <div style="display: table-cell; padding-right: 10px;"> <p>Random Agent</p>
		<img src="./media/random-agent.gif" alt="Trained"
			title="Continuous Control - Random Agent"/> 
		</div>
        <div style="display: table-cell;"> 
		<p>Trained Agent</p>
		<img src="./media/trained-agent.gif" alt="Trained"
			title="Continous Control - Trained Agent"/>		
		</div>
    </div>
</div>

## Instroduction
This repo contains my submission to the second project in the Udacity's [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893). Here you will find a Notebook with the implementation to solve the task and how to use it.

## Task description
The goal is to solve a continuous control task in which an agent (or several) in the form of a two joins arm, needs to keep track of a target object represented as a green sphere. In this case, the environment is the [Unity MLAgents](https://unity.com/products/machine-learning-agents) Reacher environment. The agent maintain tracking as long as possible to the designated target.

The agent receives a reward of `+0.1` for every step the agent hand is in the goal location.

## Environment description

The simulation contains a single or multiple agents (two joints arm). The action space is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm.

The task is episodic and it is considered solved once the agent is capable to get an average score of +30 over 100 consecutive episodes.

## Setup

### Unity Environment
Download the environment from one of the links below. You need only select the environment that matches your operating system:

Single Agent: 

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

Twenty Agents:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

Once downloaded, place the zip file at the same level of the `Continuous_Control.ipynb` notebook and extract the content there.

### Runtime Environment
Create a conda/python environment from the provided `environment.yaml` file
```bash
conda env create -f environment.yaml
# activate the environment
conda activate navigation
```
Install `mlagents==0.9.0` via pip
**Note:** This needs to be installed separately from the requirements as unityagents and this version of mlagents make conflict at the moment of creation of this repo.
```bash
pip install mlagents==0.9.0
```
Run jupyter-notebook or jupyter-lab
```bash
jupyter-notebook
# or
jupyter-lab
```
Open the notebook in this repo and explore.



