# RL - Navigation task with Deep Q-Learning (DQN)

<div style="text-align:center">
<img src="./media/trained-ddqn.gif" alt="Training..."
	title="A cute kitten" width="450" height="250" />
</div>

## Description
This repo contains my submission to the first project in the Udacity's [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893). Here you will find a Notebook with the implementation to solve the task and how to use it.

## Task description
The goal is to solve a navigation task in which an agent needs to collect an item type while avoiding another. In this case, the environment is the [Unity MLAgents](https://unity.com/products/machine-learning-agents) environment Banana Navigation. The agent needs to collect yellow bananas while avoiding blue bananas.

The agent receives a reward of `+1` for every yellow banana it collects, and a reward of `-1` for every blue one.

## Environment description

The simulation contains a single agent that navigates a large environment. At each time step, it has four actions at its disposal:

    0 - walk forward
    1 - walk backward
    2 - turn left
    3 - turn right

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.

The environment itself does not define a terminal state. However, for simplicity, we can define a fixed time step in which we wish to terminate the episode. Furthermore, we can define this task as solved when the agent achieves an average score of `13` points in the last `100`, where each episode is at least ot `1000` time steps. 

## Setup

### Unity Environment
Download the environment from one of the links below. You need only select the environment that matches your operating system:

Embeeded state: 

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

Visual Banana:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Windows_x86_64.zip)

Once downloaded, place the zip file at the same level of the `Navigation.ipynb` notebook and extract the content there.

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

### :robot: I'm still training... :muscle: 
<div style="text-align:center">
<img src="./media/training-dqn.gif" alt="Training..."
	title="A cute kitten" width="150" height="100" />
</div>


