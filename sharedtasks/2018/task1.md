---
layout: page
longtitle: "Task 1 - CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection"
title: "Task 1: Type-Level Inflection"
---

Given a [lemma](https://en.wikipedia.org/wiki/Lemma_(morphology)) and a bundle of morphological features, generate a target inflected form.

**Example**

> Source form and target features:
> 
> `release V;V.PTCP;PRS`
> 
> Target form:
> 
> `releasing`

## Data Format


The training and development data *will be* provided in a simple utf-8 encoded text format. Each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set of features, separated by semicolons. The fields on a line are TAB-separated.

For task 1, the fields are: lemma, target form, MSD. An example from the English training data:

```
touch   touching   V;V.PTCP;PRS
```

In the training data, we give all three fields. In the test phase, we omit field 2.

**Data quantity.** We give varying amounts of labeled training data (low, medium, high) to assess systems' ability to generalize in both low- and high-resource scenarios. We evaluate performance independently under each of the three data quantity conditions. For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io).

## Evaluation

Systems should predict a single character sequence for each test example.

**Evaluation script.** We will distribute an evaluation script for your use on the development data. The script will report:

* Accuracy = fraction of correctly predicted forms
* Average [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) between the prediction and the truth across all predictions

The official evaluation script that we will use for our internal evaluation *will be provided here*. We encourage ablation studies to measure the advantage gained from particular innovations. You should perform these studies **on the development data** and report the findings in your system description paper.

**Ambiguous lemmas.** We will use the same script to evaluate your system's output on the test data. If multiple correct answers are possible, we will accept any string from the correct set. For example, the two senses of English lemma `hang` have different Past forms, `hung` and `hanged`. 

**Averaging.** We will evaluate on each language separately. An aggregate evaluation will weight all languages equally (i.e. macroaveraging), including the surprise languages released later during the development period.

**Overview paper.** In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

* which systems are significantly different in performance, especially in low-resource scenarios
* which examples were hard and which types of systems succeeded on them
* which systems would provide complementary benefit in an ensemble system

