---
layout: page
longtitle: "Task - CoNLL–SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection"
title: "Task"
---

The shared task has concluded! Thanks to all those who participated. All data (including the test sets) will be hosted on this site. Please read [here](http://www.aclweb.org/anthology/K17-2001) for a detailed analysis of submitted systems and the results.

The shared task consists of two sub-tasks. Sub-task 1 asks participants to inflect word forms based on labeled examples. Sub-task 2 asks participants to fill partially filled out paradigms based on a limited number of full paradigms seen as training data.

Systems may compete in either or both of these sub-tasks. Training examples and development examples will be provided for each sub-task. For each language, the possible inflections are taken from a finite set of morphological **tags**.

#### Data Quantity
For each sub-task, varying amounts of labeled training data (**low/medium/high**) are given to assess systems' capability of generalizing in both low and high-resource scenarios. Performance is evaluated independently under each of the three data quantity conditions.

### Sub-Task 1 - Inflection
Given a **lemma** (the dictionary form of a word) with its part-of-speech, generate a target inflected form.

**Example**

```
Source form and features: release V;NFIN
Target tag: V;V.PTCP;PRS
Target form: releasing
```

### Sub-Task 2 - Paradigm Cell Filling
Given a lemma, a part-of-speech tag, and an incomplete partial paradigm, complete the remaining paradigm cells. Note that for languages with smaller paradigms, it is often the case that no additional forms (other than the lemma) are observed.

**Example**

```
Source lemma and part of speech: release V
Incomplete (covered) paradigm:
release         release         V;NFIN
release         --              V;3;SG;PRS
release         --              V;V.PTCP;PRS
release         released        V;PST
release         --              V;V.PTCP;PST

Target (uncovered) paradigm:
release         release         V;NFIN
release         releases        V;3;SG;PRS
release         releasing       V;V.PTCP;PRS
release         released        V;PST
release         released        V;V.PTCP;PST
```
## Data Format
The [training and development data](https://github.com/sigmorphon/conll2017/tree/master/all) is provided in a simple utf-8 encoded text format where each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set features, separated by semicolons. The fields on a line are **TAB**-separated.
For sub-task 1, the fields are: lemma, target form, MSD. An example from the English training data:

```
touch   touching   V;V.PTCP;PRS
```

In the training data, all three fields are given. During the test phase, field 2 is omitted.
In sub-task 2, entire inflection tables are given in the same format. For example:

```
touch   touch      V;NFIN
touch   touches    V;3;SG;PRS
touch   touching   V;V.PTCP;PRS
touch   touched    V;PST
touch   touched    V;V.PTCP;PST
```

In the training data, full tables are provided as in the above example; in the test phase, some entries in the second column are omitted and need to be filled in. Thus, we provide a "covered" and an "uncovered" file, as discussed above.

## Evaluation
In sub-task 1, systems should predict a single string for each test example. In sub-task 2, systems should predict a single string for each missing paradigm cell. 

We will distribute an evaluation script for your use on the development data. The script will report (for both sub-task 1 and sub-task 2):

* Accuracy = fraction of correctly predicted forms
* Average [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) between the prediction and the truth across all predictions

The official evaluation script that will be used for our internal evaluation is provided here. You are encouraged to do ablation studies to measure the advantage gained from particular innovations. You should perform these studies on the development data and report the findings in your system description paper.
We will use the same script to evaluate your system's output on the test data. If multiple correct answers are possible, we will accept any string from the correct set. For example, in Sub-Task 1, the two senses of English lemma `hang` have different `Past` forms, `hung` and `hanged`. 
We will evaluate on each language separately. An aggregate evaluation will weight all languages equally (by macro-averaging), including the surprise languages released later during the development period.
In an overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate

* which systems are significantly different in performance, especially in low-resource scenarios
* which examples were hard and which types of systems succeeded on them
* which systems would provide complementary benefit in an ensemble system

## Rules and External Resources
For the sake of fair competition, no external resources are permitted for the main competition track, e.g., training models on multiple languages at once or using external corpora. However, we do not wish to stymie creativity. Thus, any system that does use data from multiple languages at once, or other external resources, may be submitted to the shared task alongside a restricted submission. All those submission employing external resources will be evaluated in a second, separate track. Importantly, **we will not consider these additional submissions when selecting a winning system**. However, we will report on their performance and give credit for interesting innovations.

For systems that make use of external monolingual corpora, we have provided a list of **approved external corpora** (Wikipedia text dumps) for use in semi-supervised approaches. We ask that only these corpora be used for such techniques. The links to the Wikipedia dumps (please use those from March 1st, 2017) are provided in the next section. 

Also, we ask that participants **only train models on the provided training data** and withhold the development data for tuning hyperparameters to allow for apples-to-apples comparisons among all systems. 

## Submission of Shared Task Results
We will release the test data on May 20th. It will be in the same format as the training and dev data. Please run your system for each language and each task for which you wish to submit an entry into the competition. The output format should be a text file identical to the train and dev files for the given task. You will be adding the missing last column of answers to the test files. To see an example of the submission format, see [https://github.com/sigmorphon/conll2017/tree/master/evaluation](https://github.com/sigmorphon/conll2017/tree/master/evaluation), where we have run the baseline system and dumped the output. You will have until May 30th to submit your answers. However, please also work on your final write-ups during the testing extension, as it is harder for us to extend CoNLL-related deadlines. 

Email the resulting text files (as an archive) to [conll.sigmorphon.2017@gmail.com](conll.sigmorphon.2017@gmail.com) with the subject in the format: INSTITUTION--XX--Y, where you should replace institution with the name of your institution and XX with an integral index (in case of multiple systems from the same institution). In the case of multiple institutions, please place a hyphen between each name. If there are any additional details you would like us to know about your system or resources you used, please write a short description in the body of the email. Finally, Y should specify which data the system uses: choose Y = 0 for the basic setting (no external data, e.g., external corpora or cross-lingual data) and Y = 1 for extended setting.  As example, we consider the submission title JOHNSHOPKINS-01-0, which would the submission without external data from Johns Hopkins University, team 01. 

Please name your solution files "LANG-SIZE-out", for example "finnish-low-out", etc, and place the output files in task1 and task2, respectively, depending on the task. For example, task1/finnish-low-out should contain the output for the task 1 low-resource Finnish setting and task2/finnish-low-out should contain the output for the task 2 low-resource Finnish setting.  In other words, we are following the directory structure in this folder: [https://github.com/sigmorphon/conll2017/tree/master/evaluation/sample-output](https://github.com/sigmorphon/conll2017/tree/master/evaluation/sample-output), which you may use as a model. Please archive the entire directory structure (it will only contain two folders: task1 and task2) and email it to the address above. Each group may submit as many systems as they like (just change the XX value), but please send one email per unique setting of the variables in INSTITUTION--XX--Y. 

## System Description Paper
Each team that submits a system is invited to submit a system description paper. The paper should follow the CoNLL 2017 guidelines, which may be found at [http://www.conll.org/cfp-2017](www.conll.org/cfp-2017). The system description papers will constitute a separate volume of the CoNLL 2017 proceedings, entitled “Proceedings of the CoNLL–SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection.” Each paper should be no longer than 8 pages, not including references. Shorter papers are certainly welcome! The paper is due May 30 and the submission link may be found at [https://www.softconf.com/acl2017/conll-sigmorphon-st2017](https://www.softconf.com/acl2017/conll-sigmorphon-st2017/). 

In the paper, the participants are encouraged to provide the details necessary to replicate their system, and to discuss their results. Comparison to previous work is also encouraged, as is insightful error analysis and potential ways problems might be fixed in future work.

Two members of the organizing committee will review each paper. All papers that meet the basic requirements for a CoNLL submission and provide an adequate system description will be accepted. Each accepted paper will be presented as a poster at CoNLL. Furthermore, the organizers will write a summary paper that distills the key ideas from the individual system descriptions and highlight which systems worked best in which scenarios, along with any interesting innovations. 

```
@InProceedings{cotterell-conll-sigmorphon2017,                 
  author    = {Cotterell, Ryan and Kirov, Christo and Sylak-Glassman, John and Walther, G{\'e}raldine and Vylomova, Ekaterina and Xia, Patrick and Faruqui, Manaal and K{\"u}bler, Sandra and Yarowsky, David and Eisner, Jason and Hulden, Mans},                                      
  title     = {The {CoNLL-SIGMORPHON} 2017 Shared Task: Universal Morphological Reinflection in 52 Languages},
  booktitle = {Proceedings of the CoNLL-SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection},
  month     = {August},                                  
  year      = {2017},                         
  address   = {Vancouver, Canada},                    
  publisher = {Association for Computational Linguistics}   
}
```

## Meet The Languages!
*Note 2018-02-17: The Wikipedia dumps no longer exist, so the links have been removed.*

1. [Indo-European/Celtic/Scottish Gaelic](https://en.wikipedia.org/wiki/Scottish_Gaelic) (gd) [wiki dump]
1. [Indo-European/Celtic/Welsh](https://en.wikipedia.org/wiki/Welsh_language) (cy) [wiki dump]
1. [Indo-European/Germanic/Danish](https://en.wikipedia.org/wiki/Danish_language) (da) [wiki dump]
1. [Indo-European/Germanic/Dutch](https://en.wikipedia.org/wiki/Dutch_language) (nl) [wiki dump]
1. [Indo-European/Germanic/English](https://en.wikipedia.org/wiki/English_language) (en) [wiki dump]
1. [Indo-European/Germanic/Icelandic](https://en.wikipedia.org/wiki/Icelandic_language) (is) [wiki dump]
1. [Indo-European/Germanic/Faroese](https://en.wikipedia.org/wiki/Faroese_language) (fo) [wiki dump]
1. [Indo-European/Germanic/German](https://en.wikipedia.org/wiki/German_language) (de) [wiki dump]
1. [Indo-European/Germanic/Swedish](https://en.wikipedia.org/wiki/Swedish_language) (sv) [wiki dump]
1. [Indo-European/Germanic/Nynorsk](https://en.wikipedia.org/wiki/Nynorsk) (nn) [wiki dump]
1. [Indo-European/Indo-Aryan/Hindi](https://en.wikipedia.org/wiki/Hindi) (hi) [wiki dump]
1. [Indo-European/Indo-Aryan/Urdu](https://en.wikipedia.org/wiki/Urdu) (ur) [wiki dump]
1. [Indo-European/Albanian](https://en.wikipedia.org/wiki/Albanian_language) (sq) [wiki dump]
1. [Indo-Europea/Iranian/Persian](https://en.wikipedia.org/wiki/Persian_language) (fa) [wiki dump]
1. [Kartvelian/Georgian](https://en.wikipedia.org/wiki/Georgian_language) (ka) [wiki dump]
1. [Na-Dené/Athabaskan/Navajo](https://en.wikipedia.org/wiki/Navajo_language) (nv) [wiki dump]
1. [Quechuan/Quechua](https://en.wikipedia.org/wiki/Quechuan_languages) (qu) [wiki dump]
1. [Indo-European/Romance/Catalan](https://en.wikipedia.org/wiki/Catalan_language) (ca) [wiki dump]
1. [Indo-European/Romance/French](https://en.wikipedia.org/wiki/French_language) (fr) [wiki dump]
1. [Indo-European/Romance/Italian](https://en.wikipedia.org/wiki/Italian_language) (it) [wiki dump]
1. [Indo-European/Romance/Portuguese](https://en.wikipedia.org/wiki/Portuguese_language) (pt) [wiki dump]
1. [Indo-European/Romance/Spanish](https://en.wikipedia.org/wiki/Spanish_language) (es) [wiki dump]
1. [Afro-Asiastic/Semitic/Arabic](https://en.wikipedia.org/wiki/Arabic) (ar) [wiki dump]
1. [Afro-Asiastic/Semitic/Hebrew](https://en.wikipedia.org/wiki/Hebrew_language) (he) [wiki dump]
1. [Indo-European/Slavic/Bulgarian](https://en.wikipedia.org/wiki/Bulgarian_language) (bg) [wiki dump]
1. [Indo-European/Slavic/Czech](https://en.wikipedia.org/wiki/Czech_language) (cs) [wiki dump]
1. [Indo-European/Slavic/Lower Sorbian](https://en.wikipedia.org/wiki/Lower_Sorbian_language) (dsb) [wiki dump]
1. [Indo-European/Slavic/Macedonian](https://en.wikipedia.org/wiki/Macedonian_language) (mk) [wiki dump]
1. [Indo-European/Slavic/Polish](https://en.wikipedia.org/wiki/Polish_language) (pl) [wiki dump]
1. [Indo-European/Slavic/Russian](https://en.wikipedia.org/wiki/Russian_language) (ru) [wiki dump]
1. [Indo-European/Slavic/Serbo-Croatian](https://en.wikipedia.org/wiki/Serbo-Croatian) (sr) [wiki dump]
1. [Indo-European/Slavic/Slovak](https://en.wikipedia.org/wiki/Slovak_language) (sk) [wiki dump]
1. [Indo-European/Slavic/Slovene](https://en.wikipedia.org/wiki/Slovene_language) (sl) [wiki dump]
1. [Indo-European/Slavic/Ukrainian](https://en.wikipedia.org/wiki/Ukrainian_language) (uk) [wiki dump]
1. [Uralic/Finnic/Finnish](https://en.wikipedia.org/wiki/Finnish_language) (fi) [wiki dump]
1. [Uralic/Ugric/Hungarian](https://en.wikipedia.org/wiki/Hungarian_language) (hu) [wiki dump]
1. [Uralic/Sami/Northern Sami](https://en.wikipedia.org/wiki/Northern_Sami) (se) [wiki dump]
1. [Indo-European/Baltic/Latvian](https://en.wikipedia.org/wiki/Latvian_language) (lv) [wiki dump]
1. [Turkic/Turkish](https://en.wikipedia.org/wiki/Turkish_language) (tr) [wiki dump]
1. [Indo-European/Armenian](https://en.wikipedia.org/wiki/Armenian_language) (hy) [wiki dump]
1. [Sino-Tibetan/Kiranti/Khaling](https://en.wikipedia.org/wiki/Khaling_language) (kha) 
1. [Isolate/Haida](https://en.wikipedia.org/wiki/Haida_language) (hai)
1. [Isolate/Basque](https://en.wikipedia.org/wiki/Basque_language) (eu) [wiki dump]
1. [Indo-European/Italic/Latin](https://en.wikipedia.org/wiki/Latin) (la) [wiki dump]
1. [Indo-European/Indo-Aryan/Bengali](https://en.wikipedia.org/wiki/Bengali_language) (bn) [wiki dump]
1. [Indo-European/Celtic/Irish](https://en.wikipedia.org/wiki/Irish_language) (ga) [wiki dump]
1. [Indo-European/Romance/Romanian](https://en.wikipedia.org/wiki/Romanian_language) (ro) [wiki dump]
1. [Indo-European/Iranian/Sorani (Central Kurdish)](https://en.wikipedia.org/wiki/Central_Kurdish) (ckb) [wiki dump]
1. [Indo-European/Iranian/Kurmanji (Northern Kurdish)](https://en.wikipedia.org/wiki/Northern_Kurdish) (ku) [wiki dump]
1. [Indo-European/Baltic/Lithuanian](https://en.wikipedia.org/wiki/Lithuanian_language) (lt) [wiki dump]
1. [Indo-European/Germanic/Norwegian (Bokmål)](https://en.wikipedia.org/wiki/Bokmål) (no) [wiki dump]
1. [Uralic/Finnic/Estonian](https://en.wikipedia.org/wiki/Estonian_language) (et) [wiki dump]

## Bibliography
* Malin Ahlberg, Markus Forsberg and Mans Hulden. [Paradigm Classification in Supervised Learning of Morphology](https://www.aclweb.org/anthology/N15-1107). In NAACL 2015.
* Ryan Cotterell, Christo Kirov, John Sylak-Glassman, David Yarowsky, Jason Eisner and Mans Hulden. [The SIGMORPHON 2016 shared task—morphological reinflection](https://www.cs.jhu.edu/~jason/papers/cotterell+al.sigmorphon16.pdf). In Proceedings of SIGMORPHON 2016.
* Ryan Cotterell, Nanyun Peng and Jason Eisner. [Modeling Word Forms Using Latent Underlying Morphs and Phonology](https://aclweb.org/anthology/Q/Q15/Q15-1031.pdf). TACL 2015.
* Markus Dreyer and Jason Eisner. [Discovering Morphological Paradigms from Plain Text Using a Dirichlet Process Mixture Model](https://www.aclweb.org/anthology/D11-1057). In EMNLP 2011.
* Markus Dreyer and Jason Eisner. [Graphical Models over Multiple Strings](https://www.aclweb.org/anthology/D09-1011). In EMNLP 2009.
* Markus Dreyer, Jason Smith and Jason Eisner. [Latent-Variable Modeling of String Transductions with Finite-State Methods](https://www.aclweb.org/anthology/D08-1113). In EMNLP 2008.
* Greg Durrett and John DeNero. [Supervised Learning of Complete Morphological Paradigms](https://www.aclweb.org/anthology/N13-1138). In NAACL 2013.
* Ramy Eskander, Nizar Habash and Owen Rambow. [Automatic Extraction of Morphological Lexicons from Morphologically Annotated Corpora](https://www.aclweb.org/anthology/D13-1105.pdf). In EMNLP 2013.
* Mans Hulden, Markus Forsberg and Malin Ahlberg. [Semi-supervised Learning of Morphological Paradigms and Lexicons](https://aclweb.org/anthology/E/E14/E14-1060.pdf). In EACL 2014.
* Katharina Kann and Hinrich Schütze. [The LMU system for the SIGMORPHON 2016 shared task on morphological reinflection](https://www.aclweb.org/anthology/W/W16/W16-2010.pdf). In Proceedings of SIGMORPHON 2016.
* Garret Nicolai, Colin Cherry and Grzegorz Kondrak. [Inflection Generation as Discriminative String Transduction](https://www.aclweb.org/anthology/N15-1093). In NAACL 2015.
* John Sylak-Glassman, Christo Kirov, David Yarowsky and Roger Que. [A Language-Independent Feature Schema for Inflectional Morphology](https://www.aclweb.org/anthology/P15-2111). In ACL 2015.
* Manaal Faruqui, Yulia Tsvetkov, Graham Neubig and Chris Dyer. [Morphological Inflection Generation Using Character Sequence to Sequence Learning](https://arxiv.org/pdf/1512.06110.pdf). In NAACL 2016.
