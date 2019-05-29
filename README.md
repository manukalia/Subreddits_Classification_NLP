____

<b> <font size='5'>  
Sub-reddit Post Classification<br> </font>  

<font size='4'>Separating Science-Fact From Science-Fiction </font>

<font size='3'>  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Manu Kalia NLP Classification Project<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 08-Apr-2019<br><br>
</font>


___
    
### Problem Statement  

<font size='2'>  
***Natural Language Processing***  has a number of very high-utility application areas:  classification, machine translation, sentiment analysis, chat bots/ cust service, marketing message, targeting, etc.

***The question here is:***  can a classification model successfully classify subreddit posts into one of two categories, even if the subreddits are related in subject matter?  If so, which estimator performs best in terms of accuracy and compute resources?

</font>



### Executive Summary  
<font size='2'>  
Although we might imagine that SciFi/StarWars posts in Reddit might have a great deal of similarity to posts in Physics/Astronomy posts, NLP estimators do a good job in classifying these posts… 93% accuracy.

In the cases of Naive-Bayes (multinomial) and Logistic Regression estimators, we also have very computationally-efficient models, compared to ensemble techniques like Random Forests, or ExtraRandom Trees.  
<br/>
Logistic Regression also generates coefficients that are interpretable as odds (when coeff is exponentiated).  All in all, a very powerful tool for processing text.  

</font>  



### Data Dictionary  

<font size='2'>  
While there is a great deal of information in the json dictionaries obtained via the Reddit API, this analysis only employs the merged text info in the `Title` and `Selftext` fields.  Many posts on Reddit, particularly in Subreddits like `StarWars` and `Astronomy` contain very little (or no) text, but rather an image.  To avoid large numbers of null values, the too fields were concatenated together, since `Title` will contain some text at the very least.  
<br/>
The three initial columns in the DataFrame are `Title`, `Selftext` and `post`... all of which are strings.  A binary `fact` column was added as the target for the classifiers.  `Fact` was set to 1 for all posts from the `Physics` and `Astronomy` subreddits, and `Fact` = 0 for all other posts (from `SciFi` and `StarWars`).  
</font>  



### Conclusions   
<font size='2'>  

This notebook (along with the related Subreddit Data Gathering Subnotebook) represents a generalizable workflow for the *process* of NLP using Python, Pandas, and Scikit Learn.  We could re-run this notebook on a different pair of subreddit post downloads, run the ten models, do some hyper-parameter tuning on the best 2-3 models, and see how well computers do on subreddits whose words highly overlap or are highly-divergent.  We could select pairs of subreddits on criteria other than subject... like overlap in author/user names.  For classification of text posts into either of two classes, this appears to be an accurate and computationally efficient technique.  
<br/>
Even though we might imagine that SciFi/StarWars posts in Reddit might have a great deal of similarity to posts in Physics/Astronomy posts, NLP estimators do a good job in classifying these posts… 93% accuracy.  
<br/>
In the cases of Naive-Bayes (multinomial) and Logistic Regression estimators, we also have very computationally-efficient models, compared to ensemble techniques like Random Forests, or ExtraRandom Trees.  The two models consistently showed model-fit-times on the order of 0.1 seconds and 1.0 seconds, respectively.  Other algorithms required fit-times of 10, 20, 50, or even 60+ seconds.
<br/>
Logistic Regression also generates coefficients that are interpretable as odds (when coeff is exponentiated).  All in all, a very powerful tool for processing text.  
<br/>
For future enhancements, given more time, it would be good to compare the use of CountVectorizer vs. TFIDF.  This was not relevant for the subreddits selected here, but for a pair of subreddits with many more words in common, TFIDF might prove to be the ingredient that moves the performance from bad to good.

</font>