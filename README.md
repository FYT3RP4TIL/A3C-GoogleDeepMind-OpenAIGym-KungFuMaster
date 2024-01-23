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
  <img src="https://github.com/FYT3RP4TIL/A3C-GoogleDeepMind-OpenAIGym-KungFuMaster/assets/113416452/ee470725-111b-4cb4-b745-e81465cfa62e"/>
</p>

## A3C ( Asynchronous Advantage Actor Critic ) with LSTM

