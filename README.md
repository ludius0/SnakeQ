# SnakeQ

![gif](https://user-images.githubusercontent.com/57571014/95682411-5b2ca180-0be5-11eb-926f-ed95a5b26f85.gif)

## VIDEO: https://youtu.be/7Vh77YytDgg

# SNAKE AI LEARNING TO PLAY IT SELF WITH DEEP Q LEARNING (DQN)

## Requirements to install:
- numpy
- pytorch
- pygame

made in python 3.7+

## ABOUT:
Using DQN for teaching snake to play its own game. If you want to try it self you just type *python appGUI.py*. It will load existing model in *model* directory. If you want play with settings of Neural Network and train own, than go to *parameters.py*. To train own model you need to in *parameters.py* change LOAD to False (bear in mind if you stop code and than you want use last saved model, you need to change it back to True).

If you want understand more of structure of code: *environment.py* is whole snake game. Code is handling logic and rules of snake (with *snake_sensors.py*). You will be probably interested in *def step(action)* and *def compute_state()*. Code is structured to be similiar as **gym** from OpenAI. The *def step(action)* take action (from 0 to 3) and compute game and return (*state, reward, is_game_finished, info*), which is handled with *q_learning.py*. In the *def compute_state()* you can play with, what will go into Neural Network.

Code is under MIT license, so you can use it as you want.

### Structure:
Neural Network is linear and use ReLU activation function and Adam optimizer. Computing loss function is handled in DQN class and if you want change some parameters in DQN, you can change them in *parameters.py*. Only thing I don't recommend to change is BATCH. I tried 32 size of batch and event after 1000000 generations, there weren't any improvements.

Neural Network:
- 28 to 64 neurons
- ReLU
- 64 to 32 neurons
- ReLU
- 32 to 4 neurons

State? Neural network is feed by 28 long vector tensor: 
- First four are distance to wall (range from 0 to 1). 
- Eight are True or False (in form 1 and 0) if it see apple. 
- Another eight are distance to own snake body (range from 1 to 0). 
- Four are direction of head and last four are direction of tail both as True and False (1 or 0).

Rewards?: 
- Hitting self or border: -100. 
- Eating an apple: 30. 
- Every step: -1. 
- A lot of steps: -100. 
- Winning the game: 1000.

### Note:
So far this was my most complicated project, because I was still learning reinforcement learning and I wanted to do this project to test my understanding. I learned DQN from Maxim Lapan book on reinforcement learning. He there used DQN for game FrozenLake in gym module and on Atari pong. I wanted for long time make snake game with AI learning on its own and here it is. After 95000+ generations any further training didn't yield betetr result or I didn't give it enough computation time. Best mean result was around 370 reward.
