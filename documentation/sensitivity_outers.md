# Experiment: Outers sensitivity analysis


## Goal

Evaluate the impact and accuracy of adding outer points to the nodes dataset for predicting future queries.

## Methodology

### Sensitivity Analysis

A **sensitivity analysis** determines how different values of an independent variable affect a particular dependent variable under a given set of assumptions. In other words, sensitivity analyses study how various sources of uncertainty in a mathematical model contribute to the model's overall uncertainty.

### KMeans

**K-means** clustering is a simple unsupervised learning algorithm used to solve clustering problems. It follows a simple procedure of classifying a given data set into some clusters, defined by the letter "k," fixed beforehand. The clusters are then positioned as points, and all observations or data points are associated with the nearest cluster, computed, adjusted. Then the process starts overusing the new adjustments until the desired result is reached.

### Mean Square Error
In statistics, the mean squared error (MSE) or mean squared deviation (MSD) of an estimator (of a procedure for estimating an unobserved quantity) measures the average of the squares of the errors—that is, the average squared difference between the estimated values and the actual value. MSE is a risk function, corresponding to the expected value of the squared error loss.

The MSE is a measure of the quality of an estimator. As it is derived from the square of Euclidean distance, it is always a positive value that decreases as the error approaches zero.

## Experimental Setup

In this experiment we deal with a real dataset $D_s$ collected by four Unmanned Surface Vehicles to produce our edge architecture. Each node $n \in N$ in the edge will contain a subset of ponts. Therefore, $D_{n}\subset D_s \;|\; \forall n \in N\;,D_m\not\subset D_n\; | \; m \neq n \;, \; \forall m \in N$.


## Procedure

1. Classify the data into different clusters using KMeans. *For this experiment, we use $K=5$*.
2. Generate the datasets for each node using the centroids information. $D_k\forall k\in K$ and store it in a dictionary ```datasets={}```.
3. Split the datasets in *train* and *test*. *For this experiment, we use $80\%$ train and $20\% test*.
4. Generate the outsiders $\tilde{D}_{k_1}|\;\forall k_1\neq k\;|\;k,k_1\in K$ from node $k\in K$.  $  and add to each dataset: $\hat{D}_k\;=\;D_k+\sum^{k_1\in K}_{k\neq k1}\tilde{D}_{k_1}|\;\forall k\in K$.
5. Train the models:
   * Full: Train the model with the entire dataset without splitting into nodes.
   * Percentile: Train the model using the dataset with outers generated using percentile strategy. $\hat{DP}_k\;=\;D_k+\sum^{k_1\in K}_{k\neq k1}\tilde{DP}_{k_1}|\;\forall k\in K$
   * Random: Train the model using the dataset with outers generated using percentile strategy. $\hat{DR}_k\;=\;D_k+\sum^{k_1\in K}_{k\neq k1}\tilde{DR}_{k_1}|\;\forall k\in K$
    * Nodes Train the model using only their dataset. $D_k\forall k\in K$
6. Evaluate the results using the test set (separated in the beginning) generated and test accuracy using the MSE (Mean Square Error).

## Results

