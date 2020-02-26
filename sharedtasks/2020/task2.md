---
layout: page
longtitle: "Task 2 - SIGMORPHON 2020 Shared Task: Grapheme-to-Phoneme, Unsupervised Induction of Morphology, and Typologically Diverse Morphological Inflection"
title: "Task 2: Unsupervised Discovery of Morphological Paradigms"
---

Details to come!

In this task, participants will create a computational system that receives raw text and a set of (verbal) lemmas in the same languages, then produces complete morphological paradigms for these lemmas.

## Data and Format

The raw text and lemma files will be provided in a simple utf-8 encoded text format. Each will be a separate file. The raw text has been tokenized; if you wish, you may further preprocess it.

The output should contain (number of paradigm slots) * (number of lemmas) lines; each lemma, word form, and paradigm slot number should be separated by a TAB.

For example, for the English lemmas file:

    run
    cooperate
    sing
    
One corresponding output file (the order of lines is not important) could be:

    run	ran	1
    run	runs	2
    ...
    cooperate	cooperates	2
    cooperate	cooperated	1
    ...

(The ellipses should not appear in your output.)

We will provide development languages at the start of the shared task. However, the final evaluation will be on test languages, which we will only reveal at the beginning of the test phase.

###  External Data

In order to enable a fair comparison between systems, we don't allow the use of any external data. (Thus, the use of pretrained models like morphological analyzers or BERT (Devlin et al., 2018) isn't allowed, either.)

## Evaluation

Systems should produce a file as described above. There should be no column headers.

### Evaluation Measures

We will compare against ground-truth morphological paradigms from UniMorph 3.0 (CITE), a morphological database which provides paradigms for over 100 languages.

Systems for *supervised* paradigm completion are commonly being evaluated using word-level accuracy (Cotterell et al., 2017, *inter alia*).  However, this is not possible for our task because slots are not labeled with gold data paradigm slot descriptions.

We will use best-match accuracy, both macro-averaged (i.e., per-slot) and micro-averaged (i.e., per-form), with micro-average being the main metric. Evaluation scripts will be provided, with links [on this page].

## Baseline

We will provide and describe a baseline system [here]. It relies on a pipeline of edit tree construction and discovery of new lemmas (performed by bootstrapping), discovery of paradigms by grouping observed forms, and generalization from existing forms to fill unobserved slots.

## Overview Paper

In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

1. which systems are significantly different in performance
1. which examples were hard and which types of systems succeeded on them
1. which systems would provide complementary benefit in an ensemble system

Included in the paper will be a summary of scores. Participants who produce outputs for all languages will be ranked; others may still have their systems described in the overview paper.

Further, regardless of performance, you are invited (and expected) to submit a summary paper (4–8 pages) for the SIGMORPHON proceedings. In it, you should detail your system, any clever choices you made, details for those hoping to reproduce it, and avenues for extending or improving the system.

