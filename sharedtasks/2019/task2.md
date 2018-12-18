---
layout: page
longtitle: "Task 2 - SIGMORPHON 2019 Shared Task: Crosslinguality and Context in Morphology"
title: "Task 2: Morphological Analysis and Lemmatization in Context"
---

The second task that we will offer this year is **contextual morphological analysis and lemmatization**. You are given a sentence. You are required to give the lemma and morphosyntactic description (MSD) of each word.

For instance, when given this entry:

```
# sent-id = 1
# text = They buy and sell books.
1	They   _	_	_	_	_	_	_	_
2	buy    _	_	_	_	_	_	_	_
3	and    _	_	_	_	_	_	_	_
4	sell   _	_	_	_	_	_	_	_
5	books  _	_	_	_	_	_	_	_
6	.      _	_	_	_	_	_	_	_
```

Your system must produce the following.

```
# sent-id = 1
# text = They buy and sell books.
1	They   they	_	_	N;NOM;PL    _	_	_	_
2	buy    buy	_	_	V;SG;1;PRS	_	_	_	_
3	and    and	_	_	CONJ        _	_	_	_
4	sell   sell	_	_	V;PL;3;PRS  _	_	_	_
5	books  book	_	_	N;PL        _	_	_	_
6	.      .	_	_	PUNCT       _	_	_	_
```

It is not required that your system reproduce comment lines (those that begin with a hash-mark (‘`#`’)). Conversely, you may produce as many comment lines as you would like! This will not affect the evaluation. Nevertheless, each sentence **must** be separated by **one or more blank lines**. Blank lines **must not** exist **within** sentences.

## Data
The data is owes its provenance to the 
[Universal Dependencies](http://universaldependencies.org/) project, and the MSDs have been converted to the [UniMorph schema](https://unimorph.github.io/).

Sentences are annotated in the ten-column [CoNLL-U format](http://universaldependencies.org/format.html). All columns except for the `ID`, `FORM`, `LEMMA`, and `FEATS` will be nulled out (i.e., replaced with the underscore '`_`'). At inference time, test data will also null out the `LEMMA` and `FEATS` columns. Your system must print the data in CoNLL-U format, filling these two columns.

- The `ID` column gives each word a unique ID within the sentence.
- The `FORM` column gives the word as it appears in the sentence.
- The `LEMMA` column contains the form’s lemma.
- The `FEATS` column contains morphosyntactic features in the UniMorph schema.

Data are available [here](https://github.com/sigmorphon/2019).

## Evaluation
We will score each system based on two measures for each of the two subtasks

- Contextual Morphological Analysis
    - 0/1 accuracy of MSD (the `FEATS` column)
    - Micro-averaged F1 score for MSDs (the `FEATS` column)
- Contextual Lemmatization 
    - 0/1 accuracy of lemmata (the `LEMMA` column)
    - Average Levenstein distance of lemmata (the `LEMMA` column)

We will distribute our evaluation script so you can test your systems. If you find errors in the script, contact us at [sigmorphon+sharedtask2019@gmail.com](mailto: sigmorphon+sharedtask2019@gmail.com). 

## Pretrained System
Coming soon! We will offer one pretrained system for morphological analysis and lemmatization in context. 
