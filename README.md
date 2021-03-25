# RAKE
Python implementation of the Rapid Automatic Keyword Extraction (RAKE) algorithm. 

This simple implementation follows the steps detailed in the [paper](https://onlinelibrary.wiley.com/doi/abs/10.1002/9780470689646.ch1):
    
    Automatic Keyword Extraction from Individual Documents (2010)
    DOI : 10.1002/9780470689646.ch1
    Paper authors : Rose, Stuart & Engel, Dave & Cramer, Nick & Cowley, Wendy. 
    
RAKE came from the authors' observation that keywords are often composites of words within a context window, and that these composite forms rarely include words of insignificant lexical meaning. For example stopwords such as and, the, in, etc. don't contribute to the semantics. That being said there are cases where keywords may contain nested stopwords, the example given in the paper: "axis of evil".

This implementation does not cover these cases at present and it would be an interesting extension which can be achieved by identifying repeated neighbouring keywords, adjoined by a stopword, occuring in the same order. However, as the personal use cases for which this was built are examining short news article headlines, this extension was not implemented here. Similarily all keywords are returned in lower-case, as it was not necessary for me to be case sensitive. This implementation is best suited for keyword extraction on individual documents

## The RAKE algorithm:
* Generate candidate keywords by splitting word tokens by various delimiters (stopwords, punctuation, etc.)
* Measure co-occurence of all composite keywords.
* For each unique word in keywords, calculate frequency of that word as well as its degree (the sum of the frequency of the word and the co-occurence count). 
* Divide the degree by the frequency to get individual word scores.
* Calculate keyword scores by summing the word scores of the word tokens that make up the keyword.
