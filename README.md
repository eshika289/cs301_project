# cs301_project

# Project Proposal

What is the problem that you will be investigating? Why is it interesting?

We will be investigating weather or not a person's tweet is actually announcing a disaster. Many times people spread false information about disasters to gain influence on social media. This problem is interesting because social media is a power tool in today's times, and major events and information travel faster through social media compared to traditional news.  It's important to verify if the information on social media is actually true and valid.
https://www.kaggle.com/competitions/nlp-getting-started/overview

What reading will you examine to provide context and background?

We will examine news articles that show how social media spreads information about current events and disasters.

The article below describes how social media is being used to spread information quickly about the war in Ukraine.
https://www.nytimes.com/2022/03/25/world/europe/ukraine-war-social-media.html

This article examines how social media and Twitter specifically is being used to gain information about disasters.
https://www.scientificamerican.com/article/how-social-media-is-changing-disaster-response/

What data will you use? If you are collecting new data, how will you do it?

The Kaggle competition provides us with a set of training and test data.  It has recorded information about individual tweets and the key words and locations they reference.  The test and train data both have about 10.9k tweets in the data set.

What method or algorithm are you proposing? If there are existing implementations, will you use them and how? How do you plan to improve or modify such implementations? You don’t have to have an exact answer at this point, but you should have a general sense of how you will approach the problem you are working on.

We plan to use the random forests and decision trees method.  We can use bootstrap aggregation to introduce randomness while sampling our data for each weak learner.

How will you evaluate your results? Qualitatively, what kind of results do you expect (e.g. plots or figures)? Quantitatively, what kind of analysis will you use to evaluate and/or compare your results (e.g. what performance metrics or statistical tests)?

We can use a bar graph to show how many of the tweets were classified correctly and how many were incorrectly classified. We can also use a scatter plot with the x and y axises being features to show where we split our dataset. We plan to use the sample submission data in the Kaggle competition to calculate the error for each of the weak learners.  We can compare our weak leaners using the mean and standard deviation of their errors to compare their accuracy.  We can also calculate the entropy and information gain of our splits.

