---
layout: page
title: "SIGMORPHON 2019 Shared Task: Crosslinguality and Context in Morphology"
breadcrumb: 2019
---

- [Task 1](task1): Crosslingual transfer for inflection generation
- [Task 2](task2): Morphological analysis and lemmatization in context
- [Task 3](task3): Open challenge
- [Data and Baselines ↪](https://github.com/sigmorphon/2019) 
- [Registration ↪](https://goo.gl/forms/bZrftpa5l6RpAkAG2)
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

The shared task consists of three tasks.
**Task 1** requires participants to exploit **cross-lingual transfer for inflection in low-resource languages**.
The task is the following: given a lemma and a bundle of morphological features, generate a target inflected form. In English, an example of inflection is the  conversion of a lemma `run` to its present participle, `running`.
We will provide many data in a high-resource language and few data in the low-resource language. The goal, then, will be to perform morphological inflection in the low-resource language, having hopefully exploited some similarity to the high-resource language.


**Task 2** is contextual **morphological analysis and lemmatization**. You are given a sentence. You are required to annotate this sentence with the lemma and morphosyntactic description (MSD) of each word.

**Task 3** is an open challenge: We invite systems that wish to compete on any of the previous year’s shared tasks. We will publish strong system description papers in the SIGMORPHON proceedings. For the sake of reproducibility, we require that these systems be made open source to be considered.

To participate in the shared task, you will build a system that can learn to solve such morphology problems.
Training examples and development examples will be provided for each task.
For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io).
All submitted systems will be compared on a held-out test set.

You will be invited to describe your system in a system paper for the SIGMORPHON workshop proceedings.
The task organizers will write an overview paper that describes the task and summarizes the different approaches taken and their results.

## Interpretability Prize

Due to the growing importance of interpretability in machine learning, this year we will recognize the system paper demonstrating the most interpretable system for each task. We will award a most interpretable prize to the paper whose system performs above the provided baselines *and* best explains how and why the system behaves as it does.

This does not mean “it computes hidden representations in 3 layers using weights that are updated by
gradient descent.” It means digging into the model's decisions, e.g., “when inflecting for nominative case, neuron 23 learned to track whether the lemma ends in a vowel which determines whether it takes the consonant-initial nominative suffix of the vowel-initial nominative suffix, as seen from the following tests.” A system is interpretable if we can understand how it makes generalizations with what kind of data points, what kind of features or representations it uses or identifies, why it produced its results as opposed to others, and so on. The evaluations will be made by a panel of judges.

## Submission of Results

We will release the test data on [April 20](dates). It will be in the same format as the training and dev data. Please run your system for each language and each task for which you wish to submit an entry into the competition. In task 1, you must output only the requested inflected form on each line.
For task 2, the output format should be a text file identical to the train and dev files for the given task. You will be filling null fields in Task 2. To see an example of the submission format, see the links on each task page, where we have run the baseline system and dumped the output. You will have until April 30 to submit your answers.

Email the resulting text files (as an archive) to [sigmorpon+sharedtask2019@gmail.com](mailto:sigmorphon+sharedtask2019@gmail.com) with the subject in the format: INSTITUTION–XX-Y, where you should replace institution with the name of your institution and XX with an integral index (in case of multiple systems from the same institution). In the case of multiple institutions, please place a hyphen between each name. If there are any additional details you would like us to know about your system or resources you used, please write a short description in the body of the email. Finally, Y should specify which task the email pertains to. As example, we consider the submission title JOHNSHOPKINS-01-2, which would the submission to the contextual lemmatization+analysis task from Johns Hopkins University, team 01.

Your output file should append ".output" to the name of the test file—e.g. `west-frisian-test.output` for Task 1 and `da_ddt-um-test.conllu.output` for Task 2. Please archive the entire directory structure (either the task1 folder or task2 folder). Each group may submit as many systems as they like (just change the XX value), but please send one email per unique setting of the variables in INSTITUTION–XX–Y.

## Overview paper

In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

- which systems are significantly different in performance
- which examples were hard and which types of systems succeeded on them
- which systems would provide complementary benefit in an ensemble system
- which papers presented the best work on interpretability of their models

## Contact

Error reports (e.g. flaws in the data annotation or the evaluation script) are accepted at [sigmorphon+sharedtask2019@gmail.com](mailto: sigmorphon+sharedtask2019@gmail.com). This is also where your results on test sets should be sent.

## Previous Shared Tasks

- [2018](../2018)
- [2017](../2017)
- [2016](../2016)

## Venue

August 2; at the [16th SIGMORPHON Workshop](https://sigmorphon.github.io/workshops/2019/) in Florence, Italy (co-located with [ACL 2019](http://www.acl2019.org/EN/index.xhtml).

## References

1. Kibrik, Aleksandr E. (1998). "Archi". In Andrew Spencer; Arnold M. Zwicky. *The Handbook of Morphology*. Blackwell Publishers. pp. 455–476.
