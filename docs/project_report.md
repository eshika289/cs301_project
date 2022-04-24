# Project Report
The following is a suggested structure for your report, as well as the rubric that we will follow when evaluating reports.

## Title, Author(s)
Title: Natural Language Processing with Disaster Tweets : Decision Tree and Random Forest Approach

## Abstract
Briefly describe your problem, approach, and key results. Should be no more than 300 words.

The problem we are working with is a natural language processing (NLP) classification problem involving disaster tweets.  The task at hand is to classify a given tweet as one that is announcing a disaster or one that is not (2 classes). The approach we took to solve the classification problem was to extract features from each tweet and utilize decision trees in a random forest to predict if a given tweet is announcing a disaster or not.  The overall accuracy of the random forest on the Kaggle test data set (data set that our model has never seen) was around 75%.

## Introduction (10%)
Describe the problem you are working on, why it’s important, and an overview of your results

## Related Work (10%)
Discuss published work that relates to your project. How is your approach similar or different from others?

## Data (10%)
Describe the data you are working with for your project. What type of data is it? Where did it come from? How much data are you working with? Did you have to do any preprocessing, filtering, or other special treatment to use this data in your project?

test and train data sets on Kaggle

Kaggle train data -> keyword, location, text, target
- preprocess data to add more feature columns for the decision tree
- 

Kaggle test data -> keyword, location, text

## Methods (30%)
Discuss your approach for solving the problems that you set up in the introduction. Why is your approach the right thing to do? Did you consider alternative approaches? You should demonstrate that you have applied ideas and skills built up during the quarter to tackling your problem of choice. It may be helpful to include figures, diagrams, or tables to describe your method or compare it with other methods.

The approach we chose is to use decision trees in a random forest. Since this is a classification problem, we decided that decision trees were a good approach. Additionally, we decided that combining multiple decision trees in a random forest would help us ensure that we build a strong model from multiple weak learners.  Other approaches that we considered include gradient boosting and neural networks. 

Each decision tree first finds the feature with the lowest entropy as that is the split with that will provide us with the greatest information gain.  It then splits the data into subsets based on the value each tweet has for the specified feature.  The tree will then find the entropies for the remaining features for each subset of data that was created by the first split.  Once, it finds the feature with the smallest entropy, it will split the subset by that feature.  It will continue to do so until it has no more features left.  The subsets created after all the splits are the leaf nodes.  Each leaf node will classify the data set within it as belonging to one of the classes (disaster tweet or not disaster tweet).  If the leaf node contains a majority of valid tweets, it will classify all prediction tweets that reach it as belonging to the valid class. 

The random forest contains decision trees that were made using different sets of training data as well as different sets of features. Each decision tree in the random forest has overlapping training data with other trees, but the complete set of training data for each tree is distinct from the other trees.  The method we used to split the train and test data for each decision tree is bootstrap aggregation or bagging.  Additionally, each decision tree splits the data set using different sets of features. We found the most optimal groupings of one, two, and three features and used those sets to run our decision trees on.  The most optimal groupings of features were ones that maximized the test data accuracy. 

## Experiments (30%)
Discuss the experiments that you performed to demonstrate that your approach solves the problem. The exact experiments will vary depending on the project, but you might compare with previously published methods, perform an ablation study to determine the impact of various components of your system, experiment with different hyperparameters or architectural choices, use visualization techniques to gain insight into how your model works, discuss common failure modes of your model, etc. You should include graphs, tables, or other figures to illustrate your experimental results.

- split data into test and training sets
- compare the number of correct predictions vs incorrect predictions to get the accuracy of the tree for the test and training data sets
- kaggle test data set submission provides an accuracy
- entropy
- optimal feature selection
- number of leaves in tree analysis

## Conclusion (5%)
Summarize your key results - what have you learned? Suggest ideas for future extensions or new applications of your ideas.

- single decision tree accuracy 
- random forest accuracy

ideas for future extensions
- can use gradient boosting
- attempt to use a neural network instead of decision trees
- ensemble methods

## Grading Info
Is your paper clearly written and nicely formatted? Writing / Formatting (5%)

Supplementary Material, not counted toward your 6-8 page limit and submitted as a separate file.

Your supplementary material might include:
- Cool videos, interactive visualizations, demos, etc.

Examples of things to not put in your supplementary material:
- The entire PyTorch/TensorFlow Github source code.
- Any code that is larger than 10 MB.
- Model checkpoints.
