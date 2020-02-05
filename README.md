# NLP_Fake News Detector
This project aims at creating an advanced binary classifier to set fake news apart from real ones.
This repo contains the original dataset that is utilized to test the constructed pipeline.

The pipeline mainly consists of two parts: Word Embedding and Binary Classification.

I used GloVe as the word embedding method, and then I employed two classifiers to do the classification. First I'm gonna explain why I chose GloVe. Part of the reason is that I wanted to try something different than the common methods like word2vec.

Word2vec and glove are fundamentally similar. They both learn vectors of words from their co-occurrence information.They differ in that word2vec is a "predictive" model, whereas GloVe is a "count-based" model. 
The additional benefits of GloVe over word2vec is that it is easier to train in a large dataset. I downloaded this materials from
a Stanford research website. I used the 300 dimension embedding and the one I clipped in the pptx document uploaded is 50.

So what I basically did is: I first tokenized the data, removed the stopwords, and then I used the glove embedding to assign each sentence a specific vector. Once done with the embedding part, we can jump to classification and hypertuning.

The first classifier that I used is KNN, K nearest neighbor. There are three major hyperparameters that need to be adjusted. I found that the best K is three and the better weight value is 'uniform', so
 there is no need for us to further hypertune the value of p.
I used this AUC metric to better visualize the hypertuning process, we can see that when K equals 3, there comes the best performance. Although this performance is rather unsatisfactory. It gives us a 
high precision but a really low recall.

And then I chose a classifier that functions better, Xgboost. It has a lot of hyperparameters. I basically listed 10. And I found it impossible to conduct a grid search. So I break this hypertuning process into several parts. 

First I used grid search to determine the most suitable value for three different hyperparameters respectively, then fix them and hypertune other parameters.
First max depth, then learning rate and n estimators. I fixed them and we can see it has already given us a good performance.
Then I hypertuned the other 7 parameters, finally we get the result.

The final f1-score is 0.901, which is not as good as I originally expected, but can be can still be considered as acceptable.




