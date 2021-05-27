# Experiment Design

## Overview
This is portfolio exercise completed as part of the Udacity Data Science Nanodegree. Being a _portfolio_ activity was not subject to actual rating.  

The dataset provided was originally used as a take-home assignment provided by Starbucks for their job candidates. The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. 

In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. 
Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.

The final goal is to provide a strategy to predict whether or not a Starbucks customer would react fovorably to a promotion, based on the 7 defining feature, and measure the overall effect in terms of specific metrics.

## Requirements
In order to facilitate the execution of the Notebooks and of the scripts I have prepared an [`environment.yml`](./environment.yml) file to be used to install an environment with [Anaconda](https://www.continuum.io/downloads):

```sh
conda env create -f environment.yml
```

After the installation the environment should be visible via `conda info --envs`:

```sh
# conda environments:
#
dsnd-proj4        /usr/local/anaconda3/envs/dsnd-proj4
...

```

Further documentation on working with Anaconda environments can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html). 

## Results
The exercise is completed as a Jupyter notebook available [here](./Starbucks.ipynb). Inside that, some functions from the [`test_results.py`](./test_results.py) script are loaded.

### Training Data Analysis
In the first part of the notebook we load the [training data](./training.csv) and evaluate them from a statistical perspective, considering two evaluation metrics:

* IRR
* NRR

Moreover, as an invariant metric we analyse the proportions of Treatment/Control groups with respect to the total population. This allows us to conclude that the randomization of participants was conducted properly.

### Definition of a Classifier
After having looked at the training data, we can move forward and use them to train a classifier to identify whether or not a customer would react positively to the promotion.
For the sake of this analysis I compared 4 differnt types of classifier:

* [Random Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
* [K-Nearest Neighbor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)
* [Support Vector](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html)
* [Naive Bayes](https://scikit-learn.org/stable/modules/naive_bayes.html)

They are compared in terms of accuracy and confusion matrix against the [test data](./Test.csv) provided.  
As a note on this, the data included very few cases in which customers receiving the promotion ended up actually completing a purchase; this affected the overall performances of the classifier.

### Evaluation of a Promotion Strategy
Once selected a classifier from the above list, we can compare its predictions with the results of the actual solution deloyed at Starbucs, in terms of the 2 evaluation metrics.

I opted for the Random Forest classifier, and this led to a better IRR but a worse NRR than the reference.



## License
 <a rel="license" href="https://opensource.org/licenses/MIT"><img alt="MIT License" style="border-width:0" src="https://img.shields.io/badge/License-MIT-yellow.svg" /></a><br />This work is licensed under an <a rel="license" href="https://opensource.org/licenses/MIT">MIT License</a>.
