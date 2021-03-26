# RAKE
Python implementation of the Rapid Automatic Keyword Extraction (RAKE) algorithm. 

This implementation follows the steps detailed in the [paper](https://www.researchgate.net/publication/227988510_Automatic_Keyword_Extraction_from_Individual_Documents):
    
    Automatic Keyword Extraction from Individual Documents (2010)
    DOI : 10.1002/9780470689646.ch1
    Paper authors : Rose, Stuart & Engel, Dave & Cramer, Nick & Cowley, Wendy. 
    
RAKE came about from the authors' observation that keywords are often composites of words within a context window, and that these composite forms rarely include words of insignificant lexical meaning. For example stopwords such as and, the, in, etc. as well as punctuation, don't contribute to the sentence's semantics. Hence the RAKE algorithm's approach to keyword extraction by splitting candidate keywords by specified delimiters. 

It is worth noting that there are still cases where keywords may contain nested stopwords like the example given in the paper: "axis of evil". This (simple) implementation does not cover these cases at present but it would be an interesting extension. This can be achieved by identifying neighbouring keywords, adjoined by a stopword, repeatedly occuring in the same order. However, as the personal use cases for which this was built are examining short news article headlines, this extension was not implemented here. Similarily all keywords are returned in lower-case, as it was not necessary for me to be case sensitive. This implementation is best suited for keyword extraction on individual documents, rather than a collection of. 

## The RAKE algorithm:
* Generate candidate keywords by splitting word tokens by various delimiters (stopwords, punctuation, etc.)
* Measure co-occurence of all keywords (individual and composite).
* For each unique word in the keywords collection, calculate that word's frequency as well as its degree (the sum of the frequency of the word and the count of all words of co-occurence). 
* Divide a word's degree by its frequency to get individual word scores.
* Calculate keyword scores by summing the word scores of the words that make up the keyword.
