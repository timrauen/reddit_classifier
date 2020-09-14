Problem Statement:

How can I build a model to differentiate between two different levels of complexity in a scientific explanation? Specifically, I would like to build a classification model to predict whether a given Reddit comment was posted in the subreddit "Explainlikeimfive" or "Explainlikeimphd"


Data Collection:

My goal was to use a thousand comments from each subreddit to train and test my model. To ensure I had enough data after cleaning I scraped 4200 columns from each using the Pushshift Reddit API. I did this work in elif_comments and elip_comments, then exported the data as a csv which I could read in from my eda notebook.



Cleaning:
I limited my posts to those containg at least 5 words and not containing various racial or homophobic slurs. I also rejected comments posted by the automoderator or any human moderators. 


EDA:

I compared status length by word, character, and sentence and PHD was significantly longer (p = .01) for all three. However, there was no difference in average word length or average sentence length. They shared many of their most common words. "like", "just", "people", and "time" topped both lists. ELIP contained "energy" while ELIF did not. ELIP had "light" at number 5 while it was 23rd on ELIF. These words indicate a higher incidence of physics vocabulary. ELIP also contained "http" meaning that tese comments were more likely to use links to back up their explanations or give additional information.


Modeling:

I ran each document through a Count Vectorizer and fitted a variety of classification models, each with a gridsearch to optimize their parameters. I fit a LASSO logistic regression, a ridge logistic regression, a decision tree classifier, a bagged decision tree classifier, a random forest classifier, an ada boost classifier, a gradient boost classifier, and a naive bayes classifier. All of my models ended up being significantly overfit. LASSO, ridge, and MNB were my best models at about 70%. Then I put all of my models into a voting classifier and got about 72% accuracy.


Ideas for continued analysis:

If I have more time I would like to run some extensive analysis on the misclassified posts to see if I can find any patterns or similarities.
