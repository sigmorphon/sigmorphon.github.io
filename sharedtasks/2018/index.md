---
layout: page
title: "CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection"
breadcrumb: 2018
---

- [Task 1](task1): Type-level inflection
- [Task 2](task2): Inflection in context
- [Registration](https://docs.google.com/forms/d/e/1FAIpQLSdMiv7vgA5EMGvVWQPY4LVG8mO-ZtRa9HvMeAMZIQWKMotZBg/viewform?usp=sf_link)
- [Organizers](organizers)
- [Dates](dates)

## Overview

In 2018, [SIGMORPHON](https://sigmorphon.github.io/) and [CoNLL](http://www.conll.org/) are hosting a 
shared task on __universal morphological reinflection__. That is, the shared task of morphological reinflection will be conducted in **100+ languages of the world**. An example 
\of English reinflection is the conversion of `ran` to its present 
participle, `running`.

A word's form reflects syntactic and semantic features that are expressed by the word. For example, each English count noun has both singular and plural forms (`robot`/`robots`, `process`/`processes`), known as the **inflected forms** of the noun. A Polish verb can have [nearly 100 inflected forms](http://www.tastingpoland.com/language/verb/dodac_add_verb.html).

NLP systems must be able to analyze and generate all of these inflected forms. Fortunately, inflected forms tend to be systematically related to one another. This is why English speakers can usually predict the singular form from the plural and vice-versa, even for words they have never seen before.

The shared task consists of two parts. Task 1 asks participants to inflect word forms based on labeled examples. Task 2 is a cloze task, asking participants to provide the correct form of a lemma in context.

To participate in the shared task, you will build a system that can
learn to solve reinflection problems. Systems may compete in either or both of these tasks. Training examples and development examples will be provided for each task. For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io). All submitted systems will be 
compared on a held-out test set.

You will be invited to describe your system in a system paper for
the CoNLL 2018 shared task proceedings.  The task organizers will write an
overview paper that describes the task and summarizes the different
approaches taken and their results.

  
## Previous Shared Tasks

- [2017](../2017)
- [2016](../2016)

## Venue

November 1; Day 2 of shared task slot at CoNLL, Brussels, Belgium (collocated with EMNLP).
