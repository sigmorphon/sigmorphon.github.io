---
layout: page
longtitle: "Task 1 - SIGMORPHON 2019 Shared Task: Crosslinguality and Context in Morphology"
title: "Task 1: Crosslingual Transfer for Inflection Generation"
---

SIGMORPHON has over the past three years (and jointly with CoNLL over the past two) hosted a shared task on type-level morphological generation. The goal this year to examine **how best to do this in a cross-lingual setting**.

Why go cross-lingual? Annotated resources for the world’s languages are not distributed equally—some languages simply have more as they have more native speakers willing and able to annotate more data. We will explore how to transfer knowledge from high-resource languages that are genetically related to low-resource language.

The task is the following: given a [lemma](https://en.wikipedia.org/wiki/Lemma_(morphology)) and a bundle of morphological features, generate a target inflected form. We will provide many data in the high-resource language and few data in the low-resource language. The goal, then, will be to perform morphological inflection in the low-resource language, having hopefully exploited some similarity to the high-resource language.

## Example
The model will have access to type-level data in a low-resource target language, plus a high-resource source language. We give an example here of Asturian as the target language with Spanish as the source language.

Low-resource target training data (Asturian)

```
facer      fechu      V;V.PTCP;PST
aguar      aguà       V;PRS;2;PL;IND
...
```

High-resource source language training data (Spanish)

```
tocar   tocando    V;V.PTCP;PRS
bailar  bailaba    V;PST;IPFV;3;SG;IND
mentir  mintió     V;PST;PFV;3;SG;IND
...
```

Test input (Asturian)

```
baxar   V;V.PTCP;PRS
```

Test output (Asturian)

```
baxando
```


## Data Format
The training and development data will be provided in a simple utf-8–encoded text format. 

The training data will comprise two files: one in the language of interest (the “target language”), and one in the high-resource source language. Development and testing data are only in the target language, so each will be one file. (A source language may be a member of multiple language pairs. You **must not** use any out-of-source data except the associated target file for this pair.) Each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set of features, separated by semicolons. The fields on a line are TAB-separated, as shown above. For each language, the possible inflections are taken from a finite set of morphological tags, presented in the [UniMorph schema](https://unimorph.github.io/).


In the training data, we give all three fields. In the test phase, we omit field 2.


Data are available [here](https://github.com/sigmorphon/2019).

## Evaluation
Systems should predict a single character sequence for each test example.

**Evaluation script.** We will distribute an evaluation script for your use on the development data. The script will report:

- Accuracy = fraction of correctly predicted forms
- Average [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) between the prediction and the truth across all predictions

The official evaluation script that we will use for our internal evaluation is provided [here](https://github.com/sigmorphon/2019/tree/master/evaluation). We encourage ablation studies to measure the advantage gained from particular innovations. You should perform these studies on the development data and report the findings in your system description paper.

**Ambiguous lemmata.** We will use the same script to evaluate your system’s output on the test data. If multiple correct answers are possible, we will accept any string from the correct set. For example, the two senses of English lemma `hang` have different `Past` forms, `hung` and `hanged`.

**Averaging.** We will evaluate on each language pair separately. An aggregate evaluation will weight all languages equally (i.e. macro-averaging), including the surprise languages released later during the development period.

## Pretrained Systems

Coming soon! We will offer four pretrained systems for cross-lingual inflection generation. This models constitute very strong baselines. We believe them to be state of the art, but we will refrain from such hype. The systems are neural sequence-to-sequence models with different types of attention mechanisms: (i) soft attention, (ii) 0th-order hard non-monotonic attention, (iii) 0th-order hard monotonic attention and (iv) 1st-order hard monotonic attention. In general, the 1st-order hard monotonic attention system is the best, but performance does vary by language. The code is available [here](https://github.com/sigmorphon/crosslingual-inflection-baseline); pretrained models and scores are listed in the README.
