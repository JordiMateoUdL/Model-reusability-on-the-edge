# Model reusability on the edge

In the context of edge computing, model reusability can be defined as the ability of two nodes to exchange and reuse other work. Thus, we need to know which nodes in the network are similar and what is the direction of reusability.

## Methodology

### Maximum Mean Discrepancy (MMD)

* [Github snippet](https://github.com/jindongwang/transferlearning/blob/master/code/distance/mmd_numpy_sklearn.py


## Datasets

* **GNFUV Unmanned Surface Vehicles Sensor Data**: These datasets contains data of mobile sensor readings (humidity, temperature) corresponding to a swarm of four Unmanned Surface Vehicles (USVs) in a test-bed, Athens, Greece.

  * [GNFUV Unmanned Surface Vehicles Sensor Data Data Set 1](https://archive.ics.uci.edu/ml/datasets/GNFUV+Unmanned+Surface+Vehicles+Sensor+Data)
  * [GNFUV Unmanned Surface Vehicles Sensor Data Data Set 2](https://archive.ics.uci.edu/ml/datasets/GNFUV+Unmanned+Surface+Vehicles+Sensor+Data+Set+2)

## Implementation

### Generating synthetic datasets

In data science, synthetic data plays a significant role. It allows us to test a new algorithm under controlled conditions. In other words, we can generate data that pushes our algorithm's particular property or behaviour.

We have worked until now with the GNFUV datasets. These datasets represent regression distributions. This way,  we look at the ```sklearn—datasets``` package, which generates synthetic datasets for regression. 

The ```make_regression()``` function returns a set of input data points (regressors) along with their output (target). This function can be adjusted with the following parameters:

* **n_features**: number of dimensions/features of the generated data.
* **noise**: standard deviation of Gaussian noise
* **n_samples**: number of samples

The response variable is a linear combination of the generated input set.

We use a simple trick to generate synthetic data similar to the original one. We develop from different random_states, and we add or subtract this linear combination generated from the original dataset.

Check the code in this [Jupyter notebook](https://github.com/JordiMateoUdL/Model-reusability-on-the-edge/blob/master/notebooks/Generating%20synthethic%20data%20%3F.ipynb).

