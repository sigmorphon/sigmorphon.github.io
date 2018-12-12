---
layout: page
title: "CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection"
breadcrumb: 2018
---

- [Task 1](task1): Type-level inflection
- [Task 2](task2): Inflection in context
- [Data and Baselines](https://github.com/sigmorphon/conll2018) 
- [Registration](https://docs.google.com/forms/d/e/1FAIpQLSdMiv7vgA5EMGvVWQPY4LVG8mO-ZtRa9HvMeAMZIQWKMotZBg/viewform?usp=sf_link)
- [Google Group](https://groups.google.com/forum/#!forum/conll-sigmorphon-2018)
- [Organizers](organizers)
- [Dates](dates)

## Overview

<span style='color: red;'>*The shared task has concluded! Thanks to all those who participated!*</span> All data (including the test sets) will be hosted on this site. Please read [here](https://aclweb.org/anthology/K18-3001) for a detailed analysis of submitted systems and the results.

In 2018, [SIGMORPHON](https://sigmorphon.github.io/) and [CoNLL](http://www.conll.org/) are hosting a shared task on **universal morphological inflection**.
The shared task features **over 100 distinct languages**, whose morphology participants are asked to model.

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
**Task 1** asks participants to inflect word forms based on labeled examples.
In English, an example of inflection is the  conversion of a lemma `run` to its present participle, `running`.
The system will be provided with the source form and the morphological features of the target form.
**Task 2** is a harder version of Task 1, where the systems must infer the morphological features from the sentential context.
This is essentially a cloze task, asking participants to provide the correct form of a lemma in context.

To participate in the shared task, you will build a system that can learn to solve such inflection problems.
Systems may compete in either or both of these tasks.
Training examples and development examples will be provided for each task.
For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io).
All submitted systems will be compared on a held-out test set.

You will be invited to describe your system in a system paper for the CoNLL 2018 shared task proceedings.
The task organizers will write an overview paper that describes the task and summarizes the different approaches taken and their results.

#### A note on typography

CoNLL and SIGMORPHON are distinct entities in a joint venture.
In your writeup, please ensure that CoNLL and SIGMORPHON are [separated by an en-dash](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#En_dashes) ("–"), not a hyphen ("-").
These can be produced in LaTeX by typing two hyphens together ("`--`").

  
## Previous Shared Tasks

- [2017](../2017)
- [2016](../2016)

## Venue

31 October; Day 1 of shared task slot at CoNLL, Brussels, Belgium (collocated with EMNLP).

## References

1. Kibrik, Aleksandr E. (1998). "Archi". In Andrew Spencer; Arnold M. Zwicky. *The Handbook of Morphology*. Blackwell Publishers. pp. 455–476.
