---
layout: page
title: "SIGMORPHON 2016 Shared Task: Morphological Reinflection"
breadcrumb: 2016
---


## Overview

**The shared task has concluded!** Thanks to all those who particpated. All data (including the test sets) will be hosted on this site. Please read [here](www.aclweb.org/anthology/W/W16/W16-2002.pdf) for a detailed analysis of submitted systems and the results.

In 2015–2016, [SIGMORPHON]({{ "/" | absolute_url }}) is hosting a shared task on morphological reinflection. An example of English reinflection is the conversion of `ran` to its present participle, `running`.

To participate in the shared task, you will build a system that can learn to solve reinflection problems. All submitted systems will be compared on a held-out test set.

You will be invited to describe your system in a short paper for the SIGMORPHON 2016 workshop. The task organizers will write an overview paper that describes the task and summarizes the different approaches taken and their results.

**If you plan to participate, please sign up for the shared task [Google group](https://groups.google.com/forum/#!overview)! Just send an email to sigmorphon-2016-shared-task@googlegroups.com and ask to join.**

### Citation

```bibtex
@InProceedings{cotterell2016sigmorphon,
  author    = {Cotterell, Ryan and Kirov, Christo and Sylak-Glassman, John and Yarowsky, David and Eisner, Jason and Hulden, Mans},
  title     = {The {SIGMORPHON} 2016 Shared Task---Morphological Reinflection},
  booktitle = {Proceedings of the 2016 Meeting of {SIGMORPHON}},
  month     = {August},
  year      = {2016},
  address   = {Berlin, Germany},
  publisher = {Association for Computational Linguistics}
}
```

### Results

Available in the shared task overview paper.

### Shared Task Paper

Please submit the shared-task description papers at https://www.softconf.com/acl2016/sigmorphon16/ by **May 15th**.


### Submission

We have released the test data! It is in the same format as the training and dev data with the exception that the last column has been omitted. Please run your system for each language and each task for which you wish to submit an entry into the competition. The output format should be a text file identical to the train and dev files for the given task. Essentially, you will be adding the missing last column of answers to the test files. Note that you may submit multiple predictions for a given row and we will measure mean reciprocal rank. If you do submit mutiple ordered guesses, please output multiple lines with differing last columns; the order in the file will be the order in which we rank them.

Email the resulting text files to sigmorphon.sharedtask.2016@gmail.com with the subject in the format: INSTITUTION--XX--Y, where you should replace institution with the name of your institution and XX with an integral index (in case of multiple systems from the same institution). In the case of multiple institutions, please place a hyphen between each name. If there are any additional details you would like us to know about your system or resources you used, please write a short description in the body of the email. The Y should specify either 1, 2, or 3, depending on which data you are using to solve the task. These three categories are:

* 1 = Standard: The solution to task 1 may only use task 1 training/development data. Anything else is considered "using a bonus resource". Likewise, the solution to task 2 may only use task 1 and task 2 training/developent data. Anything else is considered "using a bonus resource". The solution to task 3 may only use task 1, 2, and task 3 training/development data. Anything else is considered "using a bonus resource".
* 2 = Restricted: All tasks are solved using only task-number specific training data: task 1 uses only task 1 train/dev data; task 2 uses only task 2 train/dev data; task 3 uses only task 3 train/dev data.
* 3 = Bonus: tasks are solved using the Standard approach, drawing also possibly on higher task number related training data and/or extra unlabeled data given on the website.

Please name your solution files "LANG-task#-solution", for example "finnish-task1-solution", etc. We encourage participants to send one email per category, with a single attached archive file containing the solutions for all languages and tasks solved. So, if you are solving all tasks with approach "Standard" (1), all the solutions can be communicated with one email with all your "LANG-task#-solution" files as an archive.

**Submissions are due at 11.59pm (anywhere in the world) on April 28, 2016 (Extended).**

### Dates

* December 1, 2015 - [training data](https://github.com/ryancotterell/sigmorphon2016/tree/master/data/) and [evaluation script](https://github.com/ryancotterell/sigmorphon2016/tree/master/src/evalm.py) released
* December 1, 2015 - [baseline system](https://github.com/ryancotterell/sigmorphon2016/tree/master/src/baseline) released
* April 20, 2016 - Surprise language data released; test input data released; participants run systems
* April 28, 2016 - System outputs collected
* May 3, 2016 - System results to participants
* May 25, 2016 - Shared task system papers due
* June 5, 2016 - Notification of Acceptance
* June 22, 2016 - Camera-ready paper due
* August 11, 2016 - Workshop


### Venue

The results of the shared task will be presented at the SIGMORPHON workshop held at [ACL 2016](http://acl2016.org/) in Berlin.



## Downloads

*Note 2018-02-17: The bonus resources (Wikipedia dumps) from these dates are no longer maintained.*

* [Training, development and test data](https://github.com/ryancotterell/sigmorphon2016/tree/master/data/)
* [Evaluation Script](https://github.com/ryancotterell/sigmorphon2016/tree/master/src/evalm.py)
* [Baseline](https://github.com/ryancotterell/sigmorphon2016/tree/master/src/baseline)
* Monolingual Corpora (Bonus Resources): Spanish, German, Finnish, Russian, Turkish, Georgian, Navajo, Arabic, Hungarian, Maltese


## Inflectional Morphology

A word's form reflects syntactic and semantic features that are expressed by the word. For example, each English count noun has both singular and plural forms (`robot`/`robots`, `process`/`processes`), known as the **inflected forms** of the noun. A Polish verb may have nearly 100 inflected forms.

NLP systems must be able to analyze and generate all of these inflected forms. Fortunately, inflected forms tend to be systematically related to one another. This is why English speakers can usually predict the singular form from the plural and vice-versa, even for words they have never seen before.



## The Tasks

There are actually three similar tasks. Your system may compete on any or all of the three tasks. Training examples and development examples will be provided for each task. For each language, the possivble inflections are named by a given finite set of morphological **tags**.



### Task 1 - Inflection

Given a **lemma** (the dictionary form of a word) with its part-of-speech, generate a target inflected form.

**English example**

> Source lemma: `run`
> Target tag: `Present participle`
> Output: `running`

Recent high-performance systems include Hulden et al. (2014) and Nicolai, Cherry and Kondrak (2015).



### Task 2 - Reinflection

Given an inflected form and its current tag, generate a target inflected form.

**English example**

> Source tag: `Past`
> Source form: `ran`
> Target tag: `Present participle`
> Output: `running`

Task 2 is a harder case of Task 1, since the source tag is no longer guaranteed to be `Lemma`.


### Task 3 - Unlabeled Reinflection

Given an inflected form without its current inflection, generate a target inflected form.

**English example**

> Source tag: not given
> Source form: `ran`
> Target tag: `Present participle`
> Output: `running`

Task 3 is a harder case of Task 2, since the source tag is no longer provided.

When solving a task, participants may use training data for lower-numbered tasks without it being considered to be a bonus resource. That is, when solving task 2, using task 1 data is permitted. Likewise, when solving task 3, both task 2 and task 1 training data can be used. We encourage participants to, if possible, run various systems, and report which training data they have used for task 2 and 3. Knowing how well task 2 (or 3) can be solved using only task 2 (or 3) data as opposed to also using data from lower-numbered tasks is valuable extra information.



### Some possible strategies

All of these are sequence-to-sequence mapping problems. If you have a general supervised method for learning such mappings, you can simply throw it at all of these tasks.

Alternatively, you can solve the tasks in sequence. For instance, reduce Task 2 to Task 1 by recovering an inflected form's lemma given its tag, and then reduce Task 3 to Task 2 by recovering an inflected form's tag.

An **inflectional paradigm** is a table that lists all inflected forms for some lemma. Rather than treating the training examples as independent, you could assemble them into partial paradigms based on shared input or output forms. You could then jointly analyze the partial paradigms to better discover latent structure in the observed forms and to better extrapolate to unobserved forms (Dreyer and Eisner 2009, 2011; Durrett and DeNero 2013; Hulden et al. 2014; Nicolai et al. 2015).



## A Baseline System

We provide a baseline system that can be used as a starting point for experiments, or simply for comparison. The system implements a discriminative string transduction, similar in spirit to other recent approaches such as Durrett and DeNero (2013) and Nicolai et al. (2015). The implementation and a description is available [here](https://github.com/ryancotterell/sigmorphon2016/tree/master/src/baseline
).




## Bonus Resources

When evaluated on a given (task, language) pair, your system is permitted to consult the provided training data for that pair. Your system is also permitted to consult the following additional resources, but no other resources. Participants need to clearly indicate if they are using the unlabeled corpora in their approach. We want to separate participation into two categories - those that only use the example inflection data, and those that take advantage of unlabeled data as well.

* Resources that we will provide for this language:
    * A large untagged monolingual text corpus.
    * The list of possible tags.
    * A description of each tag as a set of `attribute=value` pairs, e.g., `[Person=3,Number=plural,Tense=Past]`. These features are useful for generalization in languages with large tagsets.
* The training data for the other tasks in the same language:
    * Task 1 could use Task 2's data for multi-task learning (e.g., learning the Past → Gerund mapping might help with learning the Lemma → Gerund mapping).
    * Task 2 could use Task 3's data as additional incomplete training data.
* The test inputs for all tasks in the same language (transductive learning). The Task 2 example shown above reveals that `ran` can be a `Past` form. This could help Task 3 predict the `Past` form of `runs`.

Note that, as described above, *using lower-numbered task training data is not considered a bonus resource*. Task 2 may use task 1 data, and task 3 may use task 1 and 2 training data.

It is not required to use these bonus resources. They are permitted in order to make the task more realistic, to allow more freedom to develop interesting approaches, and because it would be difficult to exclude their use.

We encourage participants to experiment with various approaches and to document clearly which training data and bonus resources were used.

## Evaluation


Your system should predict a single string for each test example. Optionally, you may also produce a ranked list of up to 20 predictions for each test example.

We will distribute an evaluation script for your use on the development data. The script will report:

* Accuracy = fraction of correctly predicted forms
* Average Levenshtein distance between the prediction and the truth
* Mean reciprocal rank of the truth (if your system produces ranked lists)

The script will also provide some analysis of errors, e.g., according to whether the correct output appears in the monolingual corpus.

You are encouraged to do ablation studies to measure the advantage that you gained from using bonus resources or from particular innovations. You should perform these studies on the development data and report the findings in your paper.

We will use the same script to evaluate your system's output on the test data. If multiple answers are correct, we will use the answer that gives you the higher score. For example, in Task 1, the two senses of English lemma `hang` have different `Past` forms, `hung` and `hanged`. In Task 3, the English verb `lay` could be a `Present` or `Past` form, of different verbs whose `Past participle` forms are respectively `laid` and `lain`.

We will evaluate on each language separately. An aggregate evaluation will weight all languages equally, including the 2 surprise languages.

In the overview paper, we will also compare the systems to one another. We will evaluate

* which systems are significantly different in performance
* which examples were hard and which types of systems succeeded on them
* which systems would provide complementary benefit in an ensemble system

## Languages

We have chosen a diverse set of 10 languages, mostly languages with rich inflection. All of the datasets have been scraped from Wiktionary and undergone additional processing at the [Center for Language and Speech Processing](http://www.clsp.jhu.edu/) at [Johns Hopkins University](https://www.jhu.edu/). The data are formatted according to the schema described in Sylak-Glassman et al. (2015).

For all languages, the data consist of orthographic strings (written spellings), not phonological strings (pronunciations).

* **Spanish:** Spanish is a language of the Romance branch of the larger Indo-European family, that originated in the Castile region of Spain. More than 400 million people speak Spanish as a native language, making it second only to Mandarin in terms of its number of native speakers worldwide.
* **German:** German is a West Germanic language that derives most of its vocabulary from the Germanic branch of the Indo-European language family. It is spoken by 90 million people in central Europe.
* **Finnish:** Finnish is the language spoken by the majority of the population in Finland. It has 5.4 million speakers.
* **Russian:** Russian is an East Slavic language and an official language in Russia, Belarus, Kazakhstan, and Kyrgyzstan. It is an unofficial but widely spoken language in Ukraine, Moldova, Latvia and Estonia. Russian belongs to the family of Indo-European languages and is one of the three living members of the East Slavic languages. It has 150 million native speakers and 260 speakers total.
* **Turkish:** Turkish is the most widely spoken of the Turkic languages, with around 63 million native speakers. Speakers are located predominantly in Turkey, with smaller groups in Germany, Bulgaria, Macedonia, Northern Cyprus, Greece, the Caucasus, and other parts of Europe and Central Asia.
* **Georgian:** Georgian is a Kartvelian language spoken by Georgians. It is the official language of Georgia and spoken by 4.3 million people.
* **Navajo:** Navajo is a language of the Athabaskan branch of the Na-Dené family, by which it is related to languages spoken across the western areas of North America. Navajo is spoken primarily in the Southwestern United States, especially in the Navajo Nation political area. It is one of the most widely spoken Native American languages with almost 170,000 Americans speaking Navajo at home as of 2011.
* **Arabic:** Modern Standard Arabic (MSA) is the literary standard across the Middle East, North Africa, Horn of Africa and one of the six official languages of the United Nations. It is spoken by over 200 million people.
* **Hungarian (Surprise Language 1):** Hungarian is a Finno-Ugric language spoken primarily in Hungary by 13 million people.
* **Maltese (Surprise Language 2):** Maltese is a Semitic language closely related to Arabic. It is spoken natively on the island of Malta by 520,000 people.



## Data Format

The training and development data is provided in a simple utf-8 encoded text format where each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set feature/value pairs. The fields on a line are TAB-separated.

### Task 1

For task 1, the fields are: lemma, MSD, target form. An example from the Spanish training data:

```
hablar  pos=V,mood=IND,polite=FORM,tense=FUT,per=3,num=SG       hablará
```

### Task 2

In task 2, the fields are: source MSD, source form, target MSD, target form. For example:

```
pos=V,mood=IND,tense=PRS,per=1,num=SG,aspect=IPFV/PFV   hablo   pos=V,tense=PST,gen=MASC,num=PL hablados
```

### Task 3

In task 3, the fields are: source form, target MSD, target form. For example:

```
hablo   pos=V,tense=PST,gen=MASC,num=PL hablados
```

When evaluating, the purpose in all tasks is to reconstruct the word form in the last field, given information in the previous fields.



## Future Shared Tasks

The 2016 shared task omits some interesting aspects of the problem. In future, it might be fruitful to consider some extensions:

* Providing multiple source forms (i.e., paradigm completion)
* Providing a word's source and target contexts, in lieu of source and target tags
* Derivational morphology (instead of just inflectional morphology)
* Cross-modal learning (both phonological and orthographic data provided)
* Cross-lingual learning (some of the languages are related to one another)


## Bibliography
* Malin Ahlberg, Markus Forsberg and Mans Hulden. [Paradigm Classification in Supervised Learning of Morphology](https://www.aclweb.org/anthology/N15-1107). In NAACL 2015.
* Ryan Cotterell, Nanyun Peng and Jason Eisner. [Modeling Word Forms Using Latent Underlying Morphs and Phonology](https://aclweb.org/anthology/Q/Q15/Q15-1031.pdf). TACL 2015.
* Markus Dreyer and Jason Eisner. [Discovering Morphological Paradigms from Plain Text Using a Dirichlet Process Mixture Model](https://www.aclweb.org/anthology/D11-1057). In EMNLP 2011.
* Markus Dreyer and Jason Eisner. [Graphical Models over Multiple Strings](https://www.aclweb.org/anthology/D09-1011). In EMNLP 2009.
* Markus Dreyer, Jason Smith and Jason Eisner. [Latent-Variable Modeling of String Transductions with Finite-State Methods](https://www.aclweb.org/anthology/D08-1113). In EMNLP 2008.
* Greg Durrett and John DeNero. [Supervised Learning of Complete Morphological Paradigms](https://www.aclweb.org/anthology/N13-1138). In NAACL 2013.
* Ramy Eskander, Nizar Habash and Owen Rambow. [Automatic Extraction of Morphological Lexicons from Morphologically Annotated Corpora](https://www.aclweb.org/anthology/D13-1105.pdf). In EMNLP 2013.
* Mans Hulden, Markus Forsberg and Malin Ahlberg. [Semi-supervised Learning of Morphological Paradigms and Lexicons](https://aclweb.org/anthology/E/E14/E14-1060.pdf). In EACL 2014.
* Garret Nicolai, Colin Cherry and Grzegorz Kondrak. [Inflection Generation as Discriminative String Transduction](https://www.aclweb.org/anthology/N15-1093). In NAACL 2015.
* John Sylak-Glassman, Christo Kirov, David Yarowsky and Roger Que. [A Language-Independent Feature Schema for Inflectional Morphology](https://www.aclweb.org/anthology/P15-2111). In ACL 2015.
* Manaal Faruqui, Yulia Tsvetkov, Graham Neubig and Chris Dyer. [Morphological Inflection Generation Using Character Sequence to Sequence Learning](https://arxiv.org/pdf/1512.06110.pdf). In NAACL 2016.


## Organizers
* Ryan Cotterell (Johns Hopkins University)
* Mans Hulden (University of Colorado)
* Christo Kirov (Johns Hopkins University)
* John Sylak-Glassman (Johns Hopkins University)
* Jason Eisner (Johns Hopkins University)

Please direct all correspondence regarding the shared task to sigmorphon-shared-task-2016-organizers@googlegroups.com.

