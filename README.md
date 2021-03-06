# Deep Trading Agent
*(Implementation in Progress)*<br>
Deep Reinforcement Learning based Trading Agent for Bitcoin using [DeepSense](https://arxiv.org/abs/1611.01942) Network for Q function approximation. <br>

## Trading Model
is inspired by [Deep Q-Trading](http://cslt.riit.tsinghua.edu.cn/mediawiki/images/5/5f/Dtq.pdf) where they solve a simplified trading problem for a single asset. <br>
For each trading unit, only one of the three actions: neutral(1), long(2) and short(3) are allowed and a reward is obtained depending upon the current position of agent. Deep Q-Learning agent is trained to maximize the total accumulated rewards. <br>
Current Deep Q-Trading model is modified by using the *Deep Sense* architecture for *Q function* approximation.

## Dataset
Per minute price for Bitcoin in USD (*Bitstamp*) from 2012-1-1 to 2017-5-31 is available on Kaggle at this [link](https://www.kaggle.com/mczielinski/bitcoin-historical-data/data). However, this dataset has many missing values.<br>
A more cleaner (but less in volume) dataset in USD (*Coinbase*) is available on the same link from 20114-12-1 to 2017-10-20. <br>
*Dates for which data is available get updated frequently. These are the values at the time of writing.*

### Preprocessing
**Basic Preprocessing**<br>
Completely ignore missing values and remove them from the dataset and accumulate blocks of continuous values using the timestamps of the prices.<br>
All the accumulated blocks with number of timestamps lesser than the combined *history length* of the state and *horizon* of the agent are then filtered out since they cannot be used for training of the agent.<br>

**Advanced Preprocessing**<br>
Process missing values and concatenate smaller blocks to increase the sizes of continuous price blocks<br>
*(To be implemented)*

## Implementation
Tensorflow "1.1.0" version is used for the implementation of the **Deep Sense** network.<br>
For exact details of the implementation and the network architecture, refer to the Wiki of this repository.
### Deep Sense
Implementation is adapted from [this](https://github.com/yscacaca/DeepSense) Github repository with a few simplifications in the network architecture to incorporate learning over a single time series of the Bitcoin data.

### Deep Q Trading
Implementation and preprocessing is inspired from this [Medium post](https://hackernoon.com/the-self-learning-quant-d3329fcc9915). The actual implementation of the Deep Q Network is adapted from [DQN-tensorflow](https://github.com/devsisters/DQN-tensorflow).
