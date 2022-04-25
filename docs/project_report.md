# Project Report

## Title, Author(s)
Title: Natural Language Processing with Disaster Tweets : Decision Tree and Random Forest Approach

Authors: Eshika Malgari, Raj Patel

## Abstract
Briefly describe your problem, approach, and key results. Should be no more than 300 words.

The problem we are working with is a natural language processing (NLP) classification problem involving disaster tweets.  The task at hand is to classify a given tweet as one that is announcing a disaster or one that is not (2 classes). The approach we took to solve the classification problem was to extract features from each tweet and utilize decision trees in a random forest to predict if a given tweet is announcing a disaster or not.  The overall accuracy of the random forest on the Kaggle test data set (data set that our model has never seen) was around 75%.

## Introduction (10%)
Describe the problem you are working on, why it’s important, and an overview of your results

The problem is how social media has become an important communication channel in times of disater in the world. However, with that it's also poses people posting fake news or using misleading words. So in our case our problem is using Natural Language Processing (NLP) involving disaster tweets to predict whether the tweets are about real disasters or not. This is important because on social media it's never clear if a person's words are actually mentioning a disaster so using NLP to predict a disaster would be beneficial. The results are we got an accurarcy of 75% with the dataset specific in our model. 

## Related Work (10%)
Discuss published work that relates to your project. How is your approach similar or different from others?

The approach we used was similar at some point due to the fact that alot of people used splitting test and validation. Also using stopwords, numbers and repeating characters. Others used Matplotlib as data visualization or creating a sequence-aware LSTM model with text embedding. Some even used Logistic Regression and basic text processing to predict real disaster from given tweets.

## Data (10%)
Describe the data you are working with for your project. What type of data is it? Where did it come from? How much data are you working with? Did you have to do any preprocessing, filtering, or other special treatment to use this data in your project?

We were provided with a test and train data set by Kaggle. The train dataset has 7,613 tweets and the test data set has 3,263 tweets. The columns/features of the train and test data sets include keyword, location, and text of each tweet. The train data set also includes a target column indicating the class to which the tweet belongs: valid or not valid. 

Before we could build our trees and forest using the data, we needed to preprocess it to add more feature columns to split the data set on.  For the sklearn random forest, we extracted features by using the TfidfVectorizer() function which transforms the text of each tweet into a usable vector to extract features from. For the hard-coded trees, we extracted additional features from the test including word count, character count, average characters per word, common words, bigrams, does it include a link, and the number of hashtags present. 

## Methods (30%)
Discuss your approach for solving the problems that you set up in the introduction. Why is your approach the right thing to do? Did you consider alternative approaches? You should demonstrate that you have applied ideas and skills built up during the quarter to tackling your problem of choice. It may be helpful to include figures, diagrams, or tables to describe your method or compare it with other methods.

The approach we chose is to use decision trees in a random forest. Since this is a classification problem, we decided that decision trees were a good approach. Additionally, we decided that combining multiple decision trees in a random forest would help us ensure that we build a strong model from multiple weak learners.  Other approaches that we considered include gradient boosting and neural networks. 

Each decision tree first finds the feature with the lowest entropy as that is the split with that will provide us with the greatest information gain.  It then splits the data into subsets based on the value each tweet has for the specified feature.  The tree will then find the entropies for the remaining features for each subset of data that was created by the first split.  Once, it finds the feature with the smallest entropy, it will split the subset by that feature.  It will continue to do so until it has no more features left.  The subsets created after all the splits are the leaf nodes.  Each leaf node will classify the data set within it as belonging to one of the classes (disaster tweet or not disaster tweet).  If the leaf node contains a majority of valid tweets, it will classify all prediction tweets that reach it as belonging to the valid class. Visit the tree_prediction_path.pdf in the docs folder to better visualize how a decision tree makes a prediction on a given tweet.

The random forest contains decision trees that were made using different sets of training data as well as different sets of features. Each decision tree in the random forest has overlapping training data with other trees, but the complete set of training data for each tree is distinct from the other trees.  The method we used to split the train and test data for each decision tree is bootstrap aggregation or bagging.  Additionally, each decision tree splits the data set using different sets of features. We found the most optimal groupings of one, two, and three features and used those sets to run our decision trees on.  The most optimal groupings of features were ones that maximized the test data accuracy. 

## Experiments (30%)
Discuss the experiments that you performed to demonstrate that your approach solves the problem. The exact experiments will vary depending on the project, but you might compare with previously published methods, perform an ablation study to determine the impact of various components of your system, experiment with different hyperparameters or architectural choices, use visualization techniques to gain insight into how your model works, discuss common failure modes of your model, etc. You should include graphs, tables, or other figures to illustrate your experimental results.

We split the train dataset given to us by Kaggle into test and train subsets.  This allowed us to get the accuracy, precision, and recall of our decision trees and random forest for the train set and the test set.  The test set metrics are particularly important as it is a set of data that our model has never seen before.  Thus, the accuracy, precision, and recall for the test data set are great metrics to evaluate the performance of our model. 

Another way, we evaluated the performance of our decision trees and random forest is by using the test data provided by Kaggle.  We are not giving the classification values for the Kaggle test data set.  Once our model makes a prediction for the Kaggle test data set, we can submit that information to the competition and receive an accuracy or score for our prediction.  This is another good performance metric as our models were not trained using this data set. 

Each individual decision tree has an accuracy of around 60-70% depending on its feature set and training data.  The random forest combination of decision trees has an accuracy of about 75%.  The sklearn RandomForestClassifier has an accuracy of around 77%. 

One experiment we conducted was to determine the number of leaves in each decision tree and the average number of tweets per leaf node. This experiment helped us better understand if the decision tree was overfitting the data set. For instance, a tree built using nine features had about 1-2 tweets per leaf node. This tree was overfitting the training data and had a training accuracy above 99% but a test accuracy of around 63%. However, when we limited the number of features per tree to less than 4 features, the decision trees had a higher number of tweets per leaf node. The train and test accuracies of these trees were more similar to each other. Visit tweets_per_leaf.png in the docs folder to see a graph representation of the information discussed.

Another experiment we performed was analyzing the test data accuracy of decision trees made with various combinations of 1-3 features to determine the most optimal set of features to build decision trees on. We chose feature combinations that maximize the test data accuracy. 

## Conclusion (5%)
Summarize your key results - what have you learned? Suggest ideas for future extensions or new applications of your ideas.

We learned that decision trees are flexible models used for classification problems.  They can support features that are categorical or a numerical.  We can also use regression trees for problems that are not classification based. Their main advantage is that they are they're easy to interpret and can be used for classification and regression. However the disadvantages are they're prone to over fitting to the training data.

Random forest classification consists of many decision trees, that uses bagging and feature randomness to each tree to create forest of trees whose prediction is more accurate than a single tree. Basically the trees protect each other from their own individual errors.

Some ideas for future extensions include using gradient boosting to minimize bias error of the model. It can be used to predict as a classifier with the log loss function and as a regressor with the Mean Square Error.  We could aslo attempt to use a neural network instead of decision trees. Neural networks have the ability to learn and model non-linear and complex relationships. It can generalize and predict on unseen data.  Finally the use of ensemble methods could allow us create multiple models and then combine them to produce improved results. It would produces more accurate solutions than a single model would.
