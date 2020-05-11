---
layout: page
longtitle: "Task 2 - SIGMORPHON 2020 Shared Task: Grapheme-to-Phoneme, Unsupervised Induction of Morphology, and Typologically Diverse Morphological Inflection"
title: "Task 2: Unsupervised Morphological Paradigm Completion"
---

**Summary**: In this task, participants will create a computational system that receives raw Bible text together with a set of (verbal) lemmas in the same language and outputs complete morphological paradigms for these lemmas.

## Important Links

1. Register for the shared task using our [Google form](https://forms.gle/vrKKVepXqpb1rLuc9)
2. Join our [Google group](https://groups.google.com/forum/#!forum/sigmorphon-2020)
3. Have a look at [the data](https://github.com/sigmorphon/2020/tree/master/task2) we provide
4. Check out our [baseline system](https://github.com/cai-lw/morpho-baseline/tree/a4b5c4ef9fe7a542c134b0ad451033b9f19e4216)

## Unsupervised Paradigm Completion

Morphologically rich languages express certain properties—like tense or case—of words by changing their surface forms. This process is called (morphological) inflection, and the set of all inflected
forms of a lemma—the canonical form—is called its paradigm. While English does not have a rich inflectional morphology, a rather extreme example, Archi paradigms, can have over 1.5 million slots (Kibrik, 1977). This leads to data sparsity and has shown to be challenging for natural language processing (NLP) systems.

Children master the task of morphological inflection without access to explicit morphological information. Do they have an innate capacity that enables them to learn a language’s morphology? Or can morphological inflection be learned in an unsupervised fashion? Furthermore, wouldn't it be amazing to obtain an explanation of a long forgotten language's morphology from raw text and some remaining translated words alone? 

This year's SIGMORPHON Task 2 finally fills the gap between recent SIGMORPHON shared tasks on morphological inflection learned from limited training data and completely unsupervised morphological generation by proposing the task of **unsupervised morphological paradigm completion**. The goal is to construct and fill inflection tables exclusively from raw text and a lemma list for a known part of speech (POS). 

###  2 Tracks

In **Track 1**, submitted systems will need to figure out the number of paradigm slots from the provided data alone.

**Track 2** features a slightly easier version of the task, where the number of paradigm slots in the gold data will be provided. 

Participants are allowed to participate in either or both tracks, but we strongly encourage everyone to submit to both tracks.

## Data and Format

We will provide the following resources for each language:

1. The tokenized Bible in the language
2. A list of (verbal) lemmas in the language for development, together with gold paradigms for each lemma
3. A list of (verbal) lemmas in the language for testing

The raw text and lemma files will be provided in a simple utf-8 encoded text format. Each will be a separate file. The raw Bible text has been tokenized; if you wish, you may further preprocess it.

By establishing the Bible as a standard for unsupervised paradigm completion, we hope to leverage developments made within the framework of the shared task to soon construct large inflection tables for all of the >2000 languages the Bible is available in (semi-)automatically.

###  Output Format

The output of each system for each language should contain (number of paradigm slots) * (number of lemmas) lines; each lemma, word form, and paradigm slot number should be separated by a TAB.

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

###  Languages

We will provide *development languages* at the start of the shared task. Those languages should be used for model development, hyper-parameter tuning, etc. However, **performance on the development languages will not be taken into account for the final evaluation**. (Note, in particular, that this is different from the evaluation of this year's Task 0.)

The final evaluation of all submitted systems will be on *test languages*, which we will only reveal at the beginning of the test phase.

**Development languages**: Maltese, Persian, Portuguese, Russian, Swedish

**Test languages**: Stay tuned!

###  External Data

In order to enable a fair comparison between systems, we don't allow the use of any external resources, i.e., anything not provided in the task2 folder of the [data repository](https://github.com/sigmorphon/2020.git). Importantly, this excludes both unlabeled data and any trained models available online. (Thus, the use of pretrained models like morphological analyzers or BERT (Devlin et al., 2018) isn't allowed!)

Finally, we do **not** allow participation of multilingual systems; one language, one system!

## Evaluation

Systems should produce a file as described above. There should be no column headers.

### Evaluation Metrics

We will compare against ground-truth morphological paradigms from [UniMorph](https://unimorph.github.io), a morphological database which provides paradigms for over 100 languages.

Systems for *supervised* paradigm completion are commonly being evaluated using word-level accuracy (Cotterell et al., 2017, *inter alia*).  However, this is not possible for our *unsupervised* task because slots are not labeled with gold data paradigm slot descriptions. Thus, we will evaluate using a metric we specifically designed for this task: **best-match accuracy**. This metric first matches predicted paradigm slots with gold slots in the best possible way, i.e., the way which leads to the highest overall accuracy, and then evaluates correctness of each individual inflected form.
The official evaluation script can be found [here](https://github.com/cai-lw/morpho-baseline/tree/a4b5c4ef9fe7a542c134b0ad451033b9f19e4216), and performs the following steps:

1. Compute the average exact-match accuracy between each predicted slot and each gold slot, leading to a weighted bipartite graph.  
2. Compute a maximum weighted bipartite matching. 
3. To obtain the final score, divide the total weight of all edges in the matching by the total number of edges + unmatched vertices. (The denominator is equivalent to max(predicted slots, gold slots) regardless of the choice of matching, as long as the matching is maximal. Maximum-weight matching gives us the highest possible numerator.)

We will account for syncretism (i.e., two paradigm slots being identical for all lemmas in a language), since a system should not be penalized for making a different decision than the gold standard about counting those as one or two slots.  Thus, our evaluation script will begin by merging identical slots: one copy of each pair of identical slots will be dropped before computing the bipartite matching. This is done for both the system output and the gold data. The number of gold paradigm slots provided for Track 2 will be the number after merging.

The task's metric penalizes systems (heavily) for predicting a wrong number of paradigm slots. We expect that this will, on average, result in worse performance of all systems for Track 1 as compared to Track 2. 

### Evaluation Example

Imagine a language with two paradigm slots. The given verbal lemmas (e.g., in ExampleLanguage.V-dev) are AAA and BBB, and the task is to predict the entire paradigms of the verbs AAA and BBB.

The gold paradigms (e.g., in ExampleLanguage.V-dev.gold), are:

    AAA AAAs PLURAL
    AAA AAAd PAST
    BBB BBBs PLURAL
    BBB BBBn PAST

Our system predicts only one paradigm slot:

    AAA AAAd 1
    BBB BBBd 1

Then, the shared task metric first computes the best match for that paradigm slot with the gold paradigm slots: the slot denoted as “PAST”, which yields 50% accuracy as compared to “PLURAL”, which would result in an accuracy of 0%. We then compute per-slot accuracies:

    [50%, 0%]

(The second entry is 0%, since the second slot hasn’t been discovered by the system.)

Then, we compute the best-match accuracy by averaging: 

    50% * 0.5 + 0% * 0.5 = 25% 

## Baseline

We will provide a baseline system for the task as a starting point for participants [here](https://github.com/cai-lw/morpho-baseline/tree/a4b5c4ef9fe7a542c134b0ad451033b9f19e4216). 

In short, our baseline system consists of a pipeline of 4 different components, which perform edit tree construction and discovery of new lemmas (via bootstrapping), discovery of paradigms by grouping observed forms, and generalization from existing forms to fill unobserved slots. In particular, the last part is a sequence-to-sequence model known to perform well for morphological inflection in the low-resource setting (Makarov and Clematide, 2018). Thus, a suggested starting point for participants could be to substitute this last component by more recent sequence-to-sequence models for inflection (e.g., one based on the Transformer (Vaswani et al., 2017) architecture), in order to improve over the provided baseline.
In order to make this as easy as possible, the baseline system will generate the final output of the first three components, i.e., the training file for the inflection model, to be used by the participants.

We additionally provide two trivial baselines (which do not merge identical paradigm slots for evaluation):
- LB-GT: This baseline generates inflected forms identical to the lemma for each paradigm slot; the gold number of paradigm slots is given (*Track 2*).
- LB-Dev: This baseline generates inflected forms identical to the lemma for each paradigm slot; the number of paradigm slots is the average over the number of paradigm slots in all development languages (*Track 1*).

### Baseline Results

|       | Maltese | Persian | Portuguese | Russian | Swedish |
| ----------- | :----: | :----: | :----: | :----: | :----: |
| Official baseline  | 20.00 | 6.49 | 31.57 | 41.74 | 40.87 |
| LB-GT  | 7.19 | 2.07 | 6.55 | 6.25 | 15.73 |
| LB-Dev | 1.92 | 2.07 | 6.55 | 1.67 | 2.84 |

### Official Submission Results

Official results for all submissions can be found [here](https://docs.google.com/spreadsheets/d/1FN6nQEPff5m9IohGV02ZOY0ifinXe4xmkb46KLVBG80/edit?usp=sharing).

## Submission

Participants will submit to this task by sending their models' predictions to 
[katharina.kann@colorado.edu](mailto:katharina.kann@colorado.edu) by May 7th, 2020. 
Participants may submit predictions from as many models as they wish; each submission will be scored separately. 
Participants must submit predictions for all languages to be scored. 

## Overview Paper

In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:

1. which systems are significantly different in performance,
1. which examples were hard and which types of systems succeeded on them,
1. which systems would provide complementary benefit in an ensemble system.

Included in the paper will be a summary of all scores. Only participants who produce outputs for all languages will be ranked, but all others may still have their systems described in the overview paper.

Further, regardless of performance, you are invited (and expected) to submit a summary paper (4–8 pages) for the SIGMORPHON proceedings. In it, you should detail your system, any clever choices you made, details for those hoping to reproduce it, and avenues for extending or improving the system.

## Timeline

- February 24th, 2020: Data for development languages released [*done*]
- March 6th, 2020: Baseline and evaluation script released [*done*]
- April <del>13th</del> 20th, 2020: Data for test languages released
- <del>April 27th</del> May 7th , 2020: Participants submit their system output for all languages
- May <del>11th</del> 17th, 2020: Participants’ system description papers due
- May <del>18th</del> 24th, 2020: Camera-ready version of participants’ system description papers due

## Organization

### Logistics

Arya McCarthy (Johns Hopkins University, USA) <br>
Katharina Kann (University of Colorado Bouler, USA) <br>
Mans Hulden (University of Colorado Boulder, USA) <br>

### Baseline and Evaluation Script

Chen Xia (Carnegie Mellon University, USA) <br>
Huiming Jin (Carnegie Mellon University, USA) <br>
Liwei Cai (Carnegie Mellon University, USA) <br>
Yihui Peng (Carnegie Mellon University, USA) <br>

### Point of Contact

Katharina Kann: katharina.kann@colorado.edu

## References

1. Cotterell et al. 2017. CoNLL-SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection in 52 Languages. Proceedings of CoNLL-SIGMORPHON. 
2. Devlin et al.. 2019. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. Proceedings of NAACL.
3. Kibrik, Aleksandr E. 1998. Archi. In Andrew Spencer; Arnold M. Zwicky. The Handbook of Morphology. Blackwell Publishers.
4. Peter Makarov and Simon Clematide. 2018. Imitation learning for neural morphological string transduction. Proceedings of EMNLP.
5. Vaswani et al. 2017. Attention is All You Need. Proceedings of NeurIPS.
