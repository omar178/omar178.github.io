---
layout: post
title: "Natural language processing"
date: 2019-06-28 22:50:00
image: '/assets/img/'
description:
tags:
categories:
twitter_text:
---
# Text normalization
converting text to more convenient, standarad form For example, most of what we are going to do with language relies on first separating out or tokenizing words from running text, the task of tokenization.  English words are often separated from each other tokenization by whitespace, but whitespace is not always sufficient.New York and rock ’n’ roll are sometimes treated as large words despite the fact that they contain spaces. A tokenizer can also be used to expand clitic contractions that are marked by clitic apostrophes,  for example,  converting what’re to the two tokens what are,  and we’re to we are. A clitic is a part of a word that can’t stand on its own, and can only occur when it is attached to another word. One commonly used tokenization standard is known as thePenn Treebank tokenization standard, used for the parsed corpora (treebanks) released by the Linguistic Data Consortium (LDC), the source of many useful datasets.  This standard separates out clitics (doesn’t becomes does plus n’t), keeps hyphenated words together, and separates out all punctuation, tokens can also be normalized i,e be in a standard form. Case folding is another kind of normalization. For tasks like speech recognition case folding and information retrieval, everything is mapped to lower case.
## Lemmatization
another part of text normalization and the task includes deterimining two or more words that have the same root like the words plays,played,playground these words will boil down to play.

## Stemming
just includes the task of stripping off the suffix of word (it may results in non-english words) for example  sitting -> sitt example of algortihms: cascade, porter
## Chinese language segmentation
Some languages, including written Chinese, Japanese, and Thai, do not use spaces tomark potential word-boundaries, and so require alternative segmentation methods.so in this case we use an algorithm called MaxMatch and it works as follows, run iteratively through the characters one by one and match each character with the longest sequence match in a dictionary as follows:
![](/assets/img/maxmatch.png)
, this algorithm does not work on english language for example if the input is:
wecanonlyseeashortdistanceahead
the output will be:
we canon l y see ash ort distance ahead, however this algorithm has a problem even with chinese lanuguage as you think what might happen if the character not in the dictionary, THIS ALGORITHM WILL FAIL!
# Minimum edit distance
It's the measure of how two strings are similar to each other for example the distance between two words like man and woman is 2 because all we have to do is to add w, o to the word man this is called the Levenshtein distance between two sequences.  More formally, the minimum edit distance between two strings is defined minimum edit distanceas the minimum number of editing operations (operations like insertion, deletion,substitution) needed to transform one string into another. the algorithm works as follows it uses dynamic programming to find the shortest path difference between two or more words.
# Language Models
Models that assign probabilities to sequences of words are called language models or LMs. we introduce the simplest model that assigns probabilities language model LM to sentences and sequences of words, then-gram.  An n-gram is a sequence of N n-gram words:  a 2-gram (or bigram) is a two-word sequence of words like “please turn”,“turn your”, or ”your homework”, and a 3-gram (or trigram) is a three-word sequence of words like “please turn your”, or “turn your homework”.  We’ll see how  to use n-gram models to estimate the probability of the last word of an n-gram giventhe previous words, and also to assign probabilities to entire sequences.  In a bit of terminological ambiguity, we usually drop the word “model”, and thus the term n-gram is used to mean either the word sequence itself or the predictive model that assigns it a probability.
## N-Grams
Let’s begin with the task of computing P(w|h), the probability of a word (w) given some history (h).  Suppose the history (h) is “its water is so transparent that” and we want to know the probability that the next word is the:
  P(the|its water is so transparent that)
One way to estimate this probability is from relative frequency counts:  take a very large corpus, count the number of times we see its water is so transparent that,and count the number of times this is followed by the. This would be answering the question “Out of the times we saw the history (h), how many times was it followed by the word w”, as follows:P(the|its water is so transparent that) =C(its water is so transparent that the)C(its water is so transparent that)
I will add the real equation for the n-gram model to give a better intuition about the guessing the probability of a word given the whole sequence of words in the history
![](/assets/img/n-grams.png)
The intuition of the n-gram model is that instead of computing the probability ofa word given its entire history, we can approximate the history by just the last few words.
## bigram
The bigram model, for example, approximates the probability of a word given bigram all the previous wordsP(wn|wn−11)by using only the conditional probability of the preceding word P(wn|wn−1). In other words, instead of computing the probability
  P(the|Walden Pond’s water is so transparent that)
we approximate it with the probability P(the|that),When we use a bigram model to predict the conditional probability of the next word, we are thus making the following approximation:
  P(wn|wn−11)≈P(wn|wn-1)
p.s bigram models follows Markov assumption which assume that a word at time t depends only on word at time t-1
p.s trigram follows the same rule they just look two words in the past  
so general equation for n-grams is:
![](/assets/img/general.png)
so the question that comes to my mind right now is how we actually compute these probabilities for these n-grams,
we compute the following equation with Maximum likelyhood
![](/assets/img/equation.png)
the numerator is the count of word at time n and word at time n-1 normalized by counts of word happen at time n-1 with all other words i,e frequency of the word n-1 at large.
sometimes when data is too big we do the following:
  p1×p2×p3×p4=exp(log p1+log p2+log p3+log p4)
  adding log to mitigate the problem of probabilities underflow as values get too small when number of words increase
## Evaluation metric (Perplexity)
In practice we don’t use raw probability as our metric for evaluating language models, but a variant called perplexity. The perplexity(sometimes called PP for short) perplexity of a language model on a test set is the inverse probability of the test set, normalized by the number of words. For a test set W=w1w2...wN,
![](/assets/img/equ1.png)
Note that because of the inverse in the higher the conditional probability of the word sequence, the lower the perplexity.  Thus, minimizing perplexity is equivalent to maximizing the test set probability according to the language model
A problem that might arise using n-grams models is that if we split or data into train/test splits and in test splits we have words that our model never seas during training in this case the probability of the word x will be equal to zero and that will be a problem but fortunately there are several ways to mitigate this problem and we will dive into several ways,
### Laplace smoothing
the simplest way out there is to just add one to all the words counts before normalization so words with 0 counts will be 1 and so on, so equation becomes as follows
![](/assets/img/equ2.png)
where c is the counts for each word and as you can we increment the values by 1 and then adding V to the denominator
# References
https://web.stanford.edu/~jurafsky 
