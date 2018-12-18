---
layout: page
title: "SIGMORPHON 2019 Shared Task: Crosslinguality and Context in Morphology"
breadcrumb: 2019
---

- [Task 1](task1): Crosslingual transfer for inflection generation
- [Task 2](task2): Morphological analysis and lemmatization in context
- [Task 3](task3): Open challenge
- [Data and Baselines](https://github.com/sigmorphon/2019) 
<!-- - [Registration](https://docs.google.com/forms/d/e/1FAIpQLSdMiv7vgA5EMGvVWQPY4LVG8mO-ZtRa9HvMeAMZIQWKMotZBg/viewform?usp=sf_link)-->
<!-- - [Google Group](https://groups.google.com/forum/#!forum/conll-sigmorphon-2018)-->
- [Organizers](organizers)
- [Dates](dates)


## Overview

In 2019, [SIGMORPHON](https://sigmorphon.github.io/) is hosting a shared task on **universal morphological inflection**.
The shared task features **nearly 100 distinct languages**, whose morphology participants are asked to model.

A word’s form reflects syntactic and semantic categories that are expressed by the word through a process termed morphology.
For example, each English count noun has both singular and plural forms (`robot`/`robots`, `process`/`processes`).
These are known as the inflected forms of the noun.
Some languages display little inflection, while others possess a proliferation of forms.
Polish verb can have [nearly 100 inflected forms](http://www.tastingpoland.com/language/verb/dodac_add_verb.html) and an [Archi](https://en.wikipedia.org/wiki/Archi_language) verb has thousands (Kibrik 1998). 

Natural language processing systems must be able to analyze and generate  these inflected forms.
Fortunately, inflected forms tend to be systematically related to one another.
This is why English speakers can usually predict the singular form from the plural and vice-versa, even for words they have never seen before: 
Given a novel noun `wug`, an English speaker knows that the plural is `wugs`. 

The shared task consists of two tasks.
**Task 1** requires participants to exploit **cross-lingual transfer for inflection in low-resource languages**.
The task is the following: given a lemma and a bundle of morphological features, generate a target inflected form. In English, an example of inflection is the  conversion of a lemma `run` to its present participle, `running`.
We will provide many data in a high-resource language and few data in the low-resource language. The goal, then, will be to perform morphological inflection in the low-resource language, having hopefully exploited some similarity to the high-resource language.


**Task 2** is contextual **morphological analysis and lemmatization**. You are given a sentence. You are required to annotate this sentence with the lemma and morphosyntactic description (MSD) of each word.

**Task 3** is an open challenge: We invite systems that wish to compete on any of the previous year’s shared tasks. We will publish strong system description papers with the rest of the SIGMORPHON proceedings.

To participate in the shared task, you will build a system that can learn to solve such morphology problems.
Training examples and development examples will be provided for each task.
For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io).
All submitted systems will be compared on a held-out test set.

You will be invited to describe your system in a system paper for the SIGMORPHON workshop proceedings.
The task organizers will write an overview paper that describes the task and summarizes the different approaches taken and their results.

## Interpretability Prize

Due to the growing importance of interpretability in machine learning, this year we will recognize the system paper demonstrating the most interpretable system for each task. We will award a most interpretability prize to the paper whose system performs above the standard baseline *and* best explains how the system works: how it makes generalizations, what kind of features or representations it used or identified, why it produced its results, and so on. The evaluations will be made by a panel of judges.

## Overview paper

In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

- which systems are significantly different in performance
- which examples were hard and which types of systems succeeded on them
- which systems would provide complementary benefit in an ensemble system
- which papers presented the best work on interpretability of their models

## Contact

Error reports (e.g. flaws in the data annotation or the evaluation script) are accepted at <sigmorphon+sharedtask2019@gmail.com>. This is also where your results on test sets should be sent.

## Previous Shared Tasks

- [2018](../2018)
- [2017](../2017)
- [2016](../2016)

## Venue

1 or 2 August; at the [16th SIGMORPHON Workshop](../../workshops/2019) in Florence, Italy (collocated with ACL 2019).

## References

1. Kibrik, Aleksandr E. (1998). "Archi". In Andrew Spencer; Arnold M. Zwicky. *The Handbook of Morphology*. Blackwell Publishers. pp. 455–476.
