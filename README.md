# Implementing Gaussian Naive Bayes in C++

[//]: # (Image References)

[image1]: ./images/vehicle-maneuvers.png "Vehicle Maneuvers"
[image2]: ./images/Conditional-probabilities-for-each-feature.png "Conditional Probabilities for each feature"
[image3]: ./images/Conditional-probabilities-Naive-Bayes-classifier.png "Conditional Probabilities Naive Bayes Classifier"


This is an exercise present in Udacity's Self-Driving Cars Engineer Nanodegree Program - Lesson 8: Prediction.

In this exercise I will implement a Gaussian Naive Bayes classifier to predict the behavior of vehicles on a highway. In the image below you can see the behaviors I'll be looking for on a 3 lane highway (with lanes of 4 meter width). The dots represent the d (y axis) and s (x axis) coordinates of vehicles as they either...

   1. Change lanes left (shown in blue)
   2. Keep lane (shown in black)
   3. Or change lanes right (shown in red)

![Vehicle Maneuvers][image1]

In this exercise, my job will be to write a classifier that can predict which of these three maneuvers a vehicle is engaged in given a single coordinate (sampled from the trajectories shown below).

Each coordinate contains 4 features:

* s
* d
* ṡ
* ḋ


It is known that the lane width is 4 meters (this might be helpful in engineering additional features for my algorithm).

## Instructions

### 1. Implement the <mark>train(data, labels)</mark> method in the class <mark>GNB</mark> in <mark>classifier.cpp</mark>. 

Training a Gaussian Naive Bayes classifier consists of computing and storing the mean and standard deviation from the data for each label/feature pair. For example, given the label "change lanes left” and the feature ṡ, it would be necessary to compute and store the mean and standard deviation of ṡ over all data points with the "change lanes left” label.

Additionally, it will be convenient in this step to compute and store the prior probability p(C_k) for each label C_k. This can be done by keeping track of the number of times each label appears in the training data.

### 2. Implement the <mark>predict (observation)</mark> method in <mark>classifier.cpp</mark>.

Given a new point, prediction requires two steps:

#### 1. Compute the conditional probabilities for each feature/label combination.

For a feature xxx and label C with mean μ and standard deviation σ (computed in training), the conditional probability can be computed using the formula [here](https://en.wikipedia.org/wiki/Naive_Bayes_classifier#Gaussian_naive_Bayes): 

![][image2]

Here v is the value of feature x in the new data point.

#### 2. Use the conditional probabilities in a Naive Bayes classifier.

This can be done using the formula [here](https://en.wikipedia.org/wiki/Naive_Bayes_classifier#Constructing_a_classifier_from_the_probability_model):

![][image3]

In this formula, the argmax is taken over all possible labels Ck and the product is taken over all features xi with values vi​.

---

### Helpful Resources

* [sklearn documentation on GaussianNB](http://scikit-learn.org/stable/modules/naive_bayes.html#gaussian-naive-bayes)
* [Wikipedia article on Naive Bayes / GNB](https://en.wikipedia.org/wiki/Naive_Bayes_classifier#Gaussian_naive_Bayes)

