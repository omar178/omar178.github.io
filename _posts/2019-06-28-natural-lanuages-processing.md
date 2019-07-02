---
layout: post
title: "Natural lanuages processing"
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
It's the measure of how two strings are similar to each other for example the distance between two words like man and woman is 2 because all we have to do is to add w, o to the word man this is called the Levenshtein distance between two sequences
