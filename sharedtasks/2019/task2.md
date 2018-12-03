---
layout: page
longtitle: "Task 2 - CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection"
title: "Task 2: Inflection in Context"
---

This is a classical cloze task. You are given a sentence with a number
of missing word forms and the lemma of each missing word form. You
are required to fill in the missing forms.

There are two tracks in task 2. In track 1, you will be provided with
lemmas and morphosyntactic descriptions (MSD) for all of the context
words. In track 2, you will only see the context word forms but not
their lemmas or MSDs.

The correct forms will always be found in Unimorph paradigms. We will
provide you with example paradigms for each language. This is an
example of a complete Unimorph verb paradigm for English:

```
advise     advised     V;PST
advise     advised     V;V.PTCP;PST
advise     advises     V;3;SG;PRS
advise     advise      V;NFIN
advise     advising    V;V.PTCP;PRS
```

**Example**

> Sentence context and lemma for track 1:
> 
> `The/the+DT ___(dog) are/be+AUX;IND;PRS;FIN barking/bark+V;V.PTCP`
>
> Sentence context and lemma for track 2:
>
> `The ___(dog) are barking`
>
> Target form:
>
> `dogs`


## Data Format

The training and development data *will be* provided in a simple utf-8
encoded text format. Each word form in a sentence occupies a line and
each line has three fields: word form, lemma and MSD. The fields are
TAB-separated. Sentences are separated by an empty line.

An example from the English training data for track 1:

```
CHERNOBYL  Chernobyl      PROPN;SG
ACCIDENT   accident       N;SG
:          :              PUNCT
TEN        ten            NUM
years      year           N;PL
ON         on             ADV
```

An example from the English training data for track 2:

```
CHERNOBYL  _              _
ACCIDENT   _              _
:          _              _
TEN        _              _
years      year           _
ON         _              _
```

## Evaluation

Systems should predict a single character sequence for each test example.

**Evaluation script.** We will distribute an evaluation script for your use on the development data. The script will report:

* Accuracy = fraction of correctly predicted forms
* Average [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) between the prediction and the truth across all predictions

The official evaluation script that we will use for our internal evaluation *will be provided here*. We encourage ablation studies to measure the advantage gained from particular innovations. You should perform these studies **on the development data** and report the findings in your system description paper.

**Ambiguous examples.** We will use the same script to evaluate your
  system's output on the test data. If multiple correct answers are
  possible, we will accept any string from the correct set. For
  example, in the sentence `The dog ___(sleep)` both `sleeps` and
  `slept` are possible. Ambiguous lemmas may also sometimes result in
  several correct answers. For example, the two senses of English
  lemma `hang` have different Past forms, `hung` and `hanged`, which
  results in two possible answers for `They will be ___(hang)`.

  In case there are multiple correct answers, exact-match accuracy  will
  award credit for any of the correct forms.
   We will return the Levenshtein distance to the answer which is closest to the prediction.


**Averaging.** We will evaluate on each language separately. An aggregate evaluation will weight all languages equally (i.e. macroaveraging), including the surprise languages released later during the development period.

**Overview paper.** In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

* which systems are significantly different in performance, especially in low-resource scenarios
* which examples were hard and which types of systems succeeded on them
* which systems would provide complementary benefit in an ensemble system

