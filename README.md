# A3C-GoogleDeepMind-OpenAIGym-KungFuMaster
![1](https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/ba6753bc-a481-4bc9-9d20-6005792620e5)

## Environment :

This environment is part of the [Atari environments](https://gymnasium.farama.org/environments/atari/). Please read that page first for general information.
| Action Space | ``` Discrete(14) ``` |
| :---   | :--- | 
| Observation Space |  ``` Box(0, 255, (250, 160, 3), uint8) ``` | 
| Import | ``` gymnasium.make("version") ``` |

## Description
You are a Kung-Fu Master fighting your way through the Evil Wizard’s temple. Your goal is to rescue Princess Victoria, defeating various enemies along the way.

For a more detailed documentation, see the [AtariAge page](https://atariage.com/manual_html_page.php?SoftwareLabelID=268)

## Actions
KungFuMaster has the action space of ```Discrete(5)``` with the table below listing the meaning of each action’s meanings. To enable all 18 possible actions that can be performed on an Atari 2600, specify ```full_action_space=True``` during initialization or by passing ```full_action_space=True``` if less computational power set ```full_action_space=False``` to ```gymnasium.make```.

| Value | Meaning | Value | Meaning | Value | Meaning |
| :---   | :--- | :--- | :--- | :--- | :--- | 
| ```0``` | ```NOOP``` | ```1``` | ```UP``` | ```2``` | ```RIGHT``` |
| ```3``` | ```LEFT``` | ```4``` | ```DOWN``` |```5```|```DOWNRIGHT```|
|```6```|```DOWNLEFT```|```7```|```RIGHTFIRE```|```8```|```LEFTFIRE```|
|```9```|```DOWNFIRE```|```10```|```UPRIGHTFIRE```|```11```|```UPLEFTFIRE```|
|```12```|```DOWNRIGHTFIRE```|```13```|```DOWNLEFTFIRE```|

## Observations

Atari environments have three possible observation types: ```"rgb"```, ```"grayscale"``` and ```"ram"```.

* ```obs_type="rgb" -> observation_space=Box(0, 255, (210, 160, 3), np.uint8)```

* ```obs_type="ram" -> observation_space=Box(0, 255, (128,), np.uint8)```

* ```obs_type="grayscale" -> Box(0, 255, (210, 160), np.uint8)```, a grayscale version of the “rgb” type

See variants section for the type of observation used by each environment id by default.

## Variant
KungFuMaster has different variants of the environment id which have differences in observation, the number of frame-skips and the repeat action probability. The variant used :

| Env-id | obs_type= | frameskip= | repeat_action_probability= |
| :---   | :--- | :--- | :--- | 
| KungFuMasterDeterministic-v0 | ```"rgb"``` | ```4``` | ```0.25``` |

## Version History
A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.
 * v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the “ALE” namespace.
 * v4: Stickiness of actions was removed
 * v0: Initial versions release

<p align="center">
  <img src="https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/3732af5d-2792-42e0-97b5-9bc08ab47556"/>
</p>

## A3C ( Asynchronous Advantage Actor Critic ) with LSTM
### Prerequisites : In-Depth Knowledge of  CNN, Q-Learning and  Deep-Q-Learning.

### Actor - Critic
Actor-Critic combines the benefits of both approaches Q-learning, or policy-iteration methods such as Policy Gradient. In the case of A3C, our network will estimate both a value function V(s) (how good a certain state is to be in) and a policy π(s) (The Q values) (a set of action probability outputs). These will each be separate fully-connected layers sitting at the top of the network. Critically, the agent uses the value estimate (the critic) to update the policy (the actor) more intelligently than traditional policy gradient methods.
* The “Critic” estimates the value function. This could be the action-value (the Q value) or state-value (the V value).
* The “Actor” updates the policy distribution in the direction suggested by the Critic (such as with policy gradients).

Working : The actor decided which action should be taken and critic inform the actor how good was the action and how it should adjust. The learning of the actor is based on policy gradient approach. In comparison, critics evaluate the action produced by the actor by computing the value function.

![Screenshot 2024-01-23 185105](https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/7fed6dbd-c576-4df7-b9ff-420ca55cd44c)

### Asynchronous
Asynchronous stands for the principal difference of this algorithm from DQN, where a single neural network interacts with a single environment. On the contrary, in this case, we’ve got a global network with multiple agents having their own set of parameters. It creates every agent’s situation interacting with its environment and harvesting the different and unique learning experience for overall training. That also deals partially with RL sample correlation, a big problem for neural networks, which are optimized under the assumption that input samples are independent of each other.

![Screenshot 2024-01-23 220751](https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/14e07a99-46a2-4b77-b8cb-7fa248193e7e)

Note : In this project we have used 10 agents who will explore the environment from different starting points and who are sharing the same Critic so they can compare the rewards they are getting and the actions they will choose to maximize the reward updating the Neural Network 

### Advantage
### LSTM
### Comparision - Performance of A3C LSTM 

![Screenshot 2024-01-23 190318](https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/1c8e371e-1878-45e9-866f-6968abc218c8)

Mean and median human-normalized scores on 57 Atari games using the human starts evaluation metric.


![Screenshot 2024-01-23 190831](https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/0acc07d2-aaaf-429f-9552-5374586681cd)

Training speed comparison of different numbers of actor-learners on five Atari games. The x-axis shows training time in
hours while the y-axis shows the average score. Each curve shows the average over the three best learning rates. All asynchronous methods show significant speedups from using greater numbers of parallel actor-learners.

