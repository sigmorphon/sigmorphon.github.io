# SIGMORPHON 2020 Shared Task 0: Low-Resource Morphological Inflection 

SIGMORPHON’s fifth installment of its inflection generation shared task focuses on the low-resource case. In this edition, we are specifically interested in inflection generation systems’ ability to generalize to new languages, including languages that are typologically distinct. For example, if you have a neural network architecture that works well for a sample of Indo-European languages, should you expect the same architecture to also work well for Tupi–Guarani languages (where nouns are “declined” for tense)? The organizers suspect not, but you could prove us wrong!

## Important Links
* Register for the shared task using our [Google form](https://docs.google.com/forms/d/e/1FAIpQLSfaHAklgEaFGpu6PvP1Br7V5ouVB17NFh6l0oLGVui01uSXlA/viewform).
* Please join our [Google group](https://groups.google.com/forum/#!groupsettings/sigmorphon2020-sharedtask0/basic) to stay up to date.
* [Download the Data](https://github.com/sigmorphon2020/data)! 
* [Download a Baseline System](https://github.com/sigmorphon2020/baselines)!
* [Baseline Numbers](https://docs.google.com/spreadsheets/d/1sYHAhhhf9rpmsm_g6dIwIDgfsaPxFdM72qOVMjK2EgQ/edit?usp=sharing).


## Outline
* [Shared Task Description](#shared-task-description)
* [Timeline](#timeline)
* [Data](#data)
* [Evaluation](#evaluation)
* [Baselines](#baselines)
* [Submission](#submission)
* [References](#references)
* [Task Organization](#task-organization)


## Shared Task Description 

In this shared task, participants will design a model that learns to generate morphological inflections from a lemma and a set of morphosyntactic features of the target form. Each language in the task has its own training, development, and test splits. Training and development splits contain triples, each consisting of a lemma, a target form, and a set of morphological features, provided in the UniMorph format (the “Data” section below provides an example of input format). Test splits only provide lemmas and morphological tags: your model will need to predict the missing target form. 

The model should be general enough to work for natural languages of any typological patterning.<sup>1</sup> For example, Tagalog verbs exhibit [circumfixation](https://en.wikipedia.org/wiki/Circumfix); thus, a model with a strong inductive bias towards suffixing will likely not work well for Tagalog. The task will proceed in three phases: a Development Phase, a Generalization Phase, and an Evaluation Phase. As the task progresses, more data and more languages will be released.

In the Development Phase, we will provide training and development splits from the Austronesian, Niger-Congo, Oto-Manguean, Uralic and Indo-European language families that should be used to *construct* your system. We will refer to them as the *development languages*.  See the [table below](#development_langs) for a complete list.

In the Generalization Phase, we will provide training and development splits for new languages where approximately half are genetically related (belong to the same family) and half are genetically *unrelated* (are isolates or belong to a different family) to the development languages. We will keep the languages in the Generalization Phase a surprise until April 2020 (see [timeline](#timeline)). We will also keep the genetically unrelated language *families* a surprise, though some languages will come from the same families as those in the Development Phase. 
 
In the Evaluation Phase, the participants’ models will be evaluated on held-out forms from all of the languages from the previous phases. The languages from the Development Phase and the Generalization Phase are evaluated simultaneously. The only difference is that there has been more time to construct a model for those languages released in the Development Phase. It follows that a model could easily overfit to or favor phenomena that are more frequent in languages presented in the Development Phase, especially if parameters are shared across languages. For instance, a model based on the morphological patterning of the Indo-European languages may end up with a bias towards suffixing and will struggle to learn prefixing or circumfixation, the degree to which only becomes apparent during experimentation on other languages whose inflectional morphology patterns differ. Of course, the model architecture itself could explicitly or implicitly favor certain word formation types (suffixing, prefixing, etc.).

<sup>1</sup> See [References](#references)


**Glossary**

The shared task features both held-out morphological inflection triples and held-out languages. The organizers created a short glossary of task-specific terminology for clarity. We use the language described in this glossary unambiguously throughout the task description.

* **Development language**: A language for which the participants will have an elongated period of time (about two months) to construct a machine learning model for morphological inflection generation.
* **Held-out language**: A language for which the participants will have a short period of time (about one week) to construct or adapt a machine learning model for morphological inflection generation. The idea is that the participants apply the knowledge accrued from the Development Phase to choose a good model and good hyperparameters. Most of the held-out languages will be *typologically distinct* from the development languages, i.e. the majority of the languages will be taken from language families other than the ones used during the Development Phase.
* **Training split**: A selection of lemma–form–tag triples for a language (either development or held-out) that the participants may train their machine learning model on.
* **Development split**: A selection of lemma–form–tag triples for a language (either development or held-out) that the participants may tune the hyperparameters of their machine learning model on.
* **Test split**: A selection of lemma–tag pairs for a language (either development or held-out) for which the participants will predict target forms. The organizers will evaluate the models based on these predictions.


## Timeline

**Stage 1: Development Phase**
* February 24th, 2020: Training and development splits for development languages released; we invite participants to report errors.
* February 24th, 2020: Neural and non-neural baselines for development languages released.
* March 1st, 2020: Held-out language data are frozen.  

**Stage 2: Generalization Phase**
* April 13th, 2020: Training and development splits for held-out languages released.   
(This is not a zero-shot learning task. Participants will be given training data for all languages.)  

**Stage 3: Evaluation Phase**
* April 20th, 2020: Test splits for all languages (both development and held-out) released.
* April 27th, 2020: Participants submit test predictions on all languages.  

**Stage 4: Write-up Phase**
* May 4th, 2020: Participants’ system description papers due.  
* May 18th, 2020: Participants’ system description papers camera ready due.  
 

## Data
The training and development data are provided in a simple utf-8 encoded text format for both the development and held-out languages. Each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set of features, separated by semicolons. We refer to the MSDs as (morphological) tags for simplicity. The fields on a line are TAB-separated.
The fields are: lemma, target form, tag. Here we present an example from the Akan training data (the Akan verb “bisa” means “to ask” in English):

```
bisa     mmbisa     V;PRS;HAB;NEG
```

In the training data, we give all three fields. In the test phase, we omit field 2.

We will provide varying amounts of labeled training data, depending on the language, to assess models’ ability to generalize to novel forms, in addition to information about each language’s family and sub-family, and WALS features which participants may optionally use. For each language, the possible inflections are taken from a finite set of morphological tags, presented in the UniMorph schema.

**Development Languages**
<a name="development_langs"> 
</a>

The task features 90 languages in total.<sup>2</sup> 45 of these 90 languages are *development languages*. The development languages will come from five language families: Austronesian, Niger–Congo, Uralic, Oto-Manguean, and Indo-European. We list each of the development languages with its family and genus (subfamily) below. 

| Language                 | ISO 639\-3 | Family         | Genus                      | \# Train | \# Dev |
|:-------------------------|:----------:|:---------------|:---------------------------|---------:|-------:|
| Malagasy                 | mlg        | Austronesian   | Barito                     | 450      | 65     |
| Cebuano                  | ceb        | Austronesian   | Greater Central Phillipine | 432      | 62     |
| Hiligaynon               | hil        | Austronesian   | Greater Central Phillipine | 879      | 125    |
| Tagalog                  | tgl        | Austronesian   | Greater Central Phillipine | 2038     | 291    |
| Maori                    | mao        | Austronesian   | Oceanic                    | 149      | 22     |
| Danish                   | dan        | Indo\-European | North Germanic             | 17852    | 2550   |
| Icelandic                | isl        | Indo\-European | North Germanic             | 53841    | 7690   |
| Norwegian Bokmål         | nob        | Indo\-European | North Germanic             | 13372    | 1954   |
| Swedish                  | swe        | Indo\-European | North Germanic             | 54888    | 7840   |
| Dutch                    | nld        | Indo\-European | West Germanic              | 38826    | 5547   |
| English                  | eng        | Indo\-European | West Germanic              | 80865    | 11553  |
| German                   | deu        | Indo\-European | West Germanic              | 125534   | 17933  |
| Middle High German       | gmh        | Indo\-European | West Germanic              | 496      | 71     |
| North Frisian            | frr        | Indo\-European | West Germanic              | 2240     | 321    |
| Old English              | ang        | Indo\-European | West Germanic              | 29665    | 4255   |
| Chewa                    | nya        | Niger\-Congo   | Bantu                      | 3059     | 437    |
| Kongo                    | kon        | Niger\-Congo   | Bantu                      | 579      | 83     |
| Lingala                  | lin        | Niger\-Congo   | Bantu                      | 159      | 23     |
| Luganda                  | lug        | Niger\-Congo   | Bantu                      | 3426     | 490    |
| Sotho                    | sot        | Niger\-Congo   | Bantu                      | 345      | 50     |
| Swahili                  | swa        | Niger\-Congo   | Bantu                      | 3464     | 495    |
| Zulu                     | zul        | Niger\-Congo   | Bantu                      | 350      | 50     |
| Akan                     | aka        | Niger\-Congo   | Kwa                        | 2927     | 418    |
| Gã                       | gaa        | Niger\-Congo   | Kwa                        | 636      | 91     |
| Tlatepuzco Chinantec     | cpa        | Oto\-Manguean  | Chinantecan                | 5525     | 789    |
| San Pedro Amuzgo Amuzgos | azg        | Oto\-Manguean  | Amuzgo\-Mixtecan           | 8542     | 1221   |
| Yoloxóchitl Mixtec       | xty        | Oto\-Manguean  | Amuzgo\-Mixtecan           | 2139     | 306    |
| Chichicapan Zapotec      | zpv        | Oto\-Manguean  | Popolocal\-Zapotecan       | 814      | 117    |
| Yaitepec Chatino         | ctp        | Oto\-Manguean  | Popolocal\-Zapotecan       | 2657     | 379    |
| Zenzontepec Chatino      | czn        | Oto\-Manguean  | Popolocal\-Zapotecan       | 1096     | 157    |
| Eastern Highland Chatino | cly        | Oto\-Manguean  | Popolocal\-Zapotecan       | 3301     | 471    |
| Eastern Highland Otomi   | otm        | Oto\-Manguean  | Oto\-Pamean                | 21966    | 3138   |
| Mezquital Otomi          | ote        | Oto\-Manguean  | Oto\-Pamean                | 23213    | 3316   |
| Chichimec                | pei        | Oto\-Manguean  | Oto\-Pamean                | 10584    | 3024   |
| Estonian                 | est        | Uralic         | Finnic                     | 27373    | 3911   |
| Finnish                  | fin        | Uralic         | Finnic                     | 1293305  | 184758 |
| Ingrian                  | izh        | Uralic         | Finnic                     | 805      | 115    |
| Karelian                 | krl        | Uralic         | Finnic                     | 81725    | 11675  |
| Livonian                 | liv        | Uralic         | Finnic                     | 2936     | 420    |
| Veps                     | vep        | Uralic         | Finnic                     | 356103   | 50872  |
| Votic                    | vot        | Uralic         | Finnic                     | 1040     | 149    |
| Meadow Mari              | mhr        | Uralic         | Mari                       | 76681    | 10955  |
| Erzya                    | myv        | Uralic         | Mordvinic                  | 82346    | 11764  |
| Moksha                   | mdf        | Uralic         | Mordvinic                  | 51726    | 7390   |
| Northern Sami            | sme        | Uralic         | Sami                       | 45350    | 6479   |

<sup>2</sup>The organizers may increase the number of total languages, if annotation efforts allow.


**Held-out Languages** 

The remaining 45 of these 90 languages will be *held-out languages*. The shared task organizers will provide the participants with enough time (about a week according to the current timeline) to train a model that they have previously selected on the development languages. However, there will not be enough time for choosing a new model or extensive hyperparameter tuning. 

Which languages? They’re a surprise!


**Multilingual Modeling [Recommendation]**

Many of the languages in the shared task have only a few morphological forms annotated. In most cases, this is not because we have a larger stash that we are withholding, but rather because there is no resource known to the organizers for such data. To model these low-resource languages well, the organizers *recommend* a multilingual approach that exploits the genetic similarity within the development and held-out languages provided. For instance, we only give the participants a handful of lemma–form–tag triples of, say, Kongo, generalization will be difficult without using data from related Niger-Congo languages. 


**Restrictions**

There are no restrictions about what sort of data you can use for this task. For example, if you would like to use a large, unlabeled corpus, such as Wikipedia, that is acceptable. You may also use a pre-trained language model, e.g. BERT ([Devlin et al. 2019](https://www.aclweb.org/anthology/N19-1423/)). However, we will evaluate models in two different categories: (1) those that use external resources (beyond what is provided by the task), and (2) those that do not. Participants are asked to clearly specify the submission category. 


## Evaluation

Our shared task also comes with a somewhat novel experimental design. We will simultaneously evaluate models for both the Development languages, whose training and development sets will be available for an elongated period of time, and the Held-out languages, whose training and development sets will only be available for a short time prior to submission, which precludes extensive tuning. To be officially ranked, you must submit results for **all** evaluation languages. Thus, to succeed, your class of models (e.g. neural sequence-to-sequence models or weighted finite-state transducers with hand-crafted features) must generalize well to the group of Held-out languages that are typologically distinct from the Development languages you performed model selection on. To repeat: This is not a zero-shot learning task, but rather our evaluation set-up is designed to test the inherent inductive bias in the participants’ chosen model class. We attribute the inspiration for this experimental design to [Emily Bender](https://faculty.washington.edu/ebender/), who often [advocates for such positions](https://thegradient.pub/the-benderrule-on-naming-the-languages-we-study-and-why-it-matters/).

We will simultaneously evaluate the accuracy on held-out forms for languages from the following three categories of languages separately: 1) held-out forms from the Development languages, 2) held-out forms from genetically related Held-out languages, and 3) held-out forms from genetically unrelated Held-out languages. This tripartite split should give the field insight into how reliable performance of certain classes of models are on typologically distinct languages. It should also help answer the following question: If my model class works well when trained on English and many others, will the same model class work well on languages which exhibit linguistic characteristics distinct from English?


**Evaluation Script**

We will distribute an evaluation script for your use on the development data. The script will report:
* Accuracy = fraction of correctly predicted forms
* Average Levenshtein distance between the prediction and the truth across all predictions

The official evaluation script that we will use for our internal evaluation *<u>will be provided here</u>*. We encourage ablation studies to measure the advantage gained from particular innovations. You should perform these studies **on the development data** and report the findings in your system description paper.


**Averaging**

We will evaluate each language separately. A per-family aggregate evaluation will weight all languages in a family (see above) equally, i.e., macro-averaging, including the languages released later during the Generalization phase.

**Overview paper**

In the overview paper for the shared task, we will compare the performance of submitted systems in detail. We will evaluate:
* which systems are significantly different in performance, especially in low-resource scenarios
* which examples were hard, and which types of systems succeeded on them
* which systems would provide complementary benefit in an ensemble system


## Baselines

The organizers will provide two pre-trained baselines for the participants’ consumption. Their use is optional and provided to help the participants develop their own models faster. 

**Non-Neural Baseline**

The first baseline is a non-neural system that has been used as a baseline in earlier shared tasks on morphological reinflection ([Cotterell et al., 2017](https://www.aclweb.org/anthology/K17-2001/); [Cotterell et al., 2018](https://www.aclweb.org/anthology/K18-3001/)). The system first heuristically extracts lemma-to-form transformations; it assumes that these transformations are suffix- or prefix-based. A simple majority classifier is used to apply the most frequent suitable transformation to an input lemma, given the morphological tag, yielding the output form. Please see [Cotterell et al. (2017)](https://www.aclweb.org/anthology/K17-2001/) for further details.

**Neural Baseline**

The second baseline is a multilingual transformer ([Vaswani et al., 2017](https://papers.nips.cc/paper/7181-attention-is-all-you-need.pdf)). The version of this model adopted for character-level tasks currently holds the state-of-the-art on the 2017 SIGMORPHON shared task data. The transformer takes the lemma and morphological tags as input and outputs the target inflection. Given the low-resource setup, a single model will be trained on all languages. Additionally, we consider the data augmentation technique used by [Anastasopoulos and Neubig (2019)](https://www.aclweb.org/anthology/D19-1091/) as another baseline.


## Submission

Participants will be asked to submit a tarball of their models’ predictions to [sigmorphon2020sharedtask@gmail.com](mailto:sigmorphon2020sharedtask@gmail.com) at the end of the task on April 27, 2020. The exact file format will be clarified one week in advance on the shared task’s mailing list. A team (group of participants) may submit predictions from as many models as they would like. Each submission will be scored separately. Submissions must specify whether they are (1) unconstrained (use external resources) or (2) constrained (use only the data from our released splits). For evaluation purposes, we will rank using an aggregate of all test languages, so participants are encouraged to submit for all languages. Results will be announced as a public Google sheet a few days after submission.

Participants’ system description papers will be handled through softconf. The link will be provided a week before submission.


## References

Introduction into morphology:  
&nbsp;&nbsp;&nbsp; Haspelmath, M. (2002). [*Understanding Morphology*](https://www.researchgate.net/publication/271018639_Understanding_Morphology). Oxford University Press, USA.  
&nbsp;&nbsp;&nbsp; Aronoff, M., & Fudeman, K. (2011). [*What is Morphology?*](http://www.ucd.ie/artspgs/introling/Aronoffmorphology.pdf) (Vol. 8). John Wiley & Sons.

More detailed studies on morphological typology:  
&nbsp;&nbsp;&nbsp; Baerman, M. (Ed.). (2015). *The Oxford Handbook of Inflection*. Oxford University Press, USA.  
&nbsp;&nbsp;&nbsp; Song, J. J. (2014). *Linguistic Typology: Morphology and Syntax*. Routledge.  
&nbsp;&nbsp;&nbsp; Song, J. J. (2010). *The Oxford handbook of Linguistic Typology*. USA.  
&nbsp;&nbsp;&nbsp; Malchukov, A. and Spencer, A. (2008). *The Handbook of Case*. Oxford University Press, USA.  

Language-specific descriptions:  
&nbsp;&nbsp;&nbsp; You may find more detailed information on some languages here: [https://langsci-press.org/series](https://langsci-press.org/series)


## Task Organization   

**Logistics**  

Adina Williams (Facebook AI Research NYC, USA)   
Christo Kirov (Google Research NYC, USA)   
Ekaterina Vylomova (University of Melbourne, Australia)   
Eleanor Chodroff (University of York, UK)   
Elizabeth Salesky (Johns Hopkins University, USA)   
Mans Hulden (University of Colorado Boulder, USA)   
Miikka Silfverberg (University of British Columbia, Canada)   
Ryan Cotterell (ETH Zürich, Switzerland)   
Sabrina Mielke (Johns Hopkins University, USA)   
Shijie Wu (Johns Hopkins University, USA)  

**Data Annotation**  

Andrej Krizhanovsky (Karelian Research Centre, Russia)   
Antonios Anastasopoulos (Carnegie Mellon University, USA)   
Edoardo Ponti (University of Cambridge, UK)   
Elena Klyachko (National Research University Higher School of Economics, Russia)   
Irene Nikkarinen (University of Cambridge, UK)   
Jennifer White (University of Cambridge, UK)   
Josef Valvoda (University of Cambridge, UK)   
Kyle Estment (University of Cambridge, UK)   
Lucas Torroba Hennigen (University of Cambridge, UK)   
Natalia Krizhanovsky (Karelian Research Centre, Russia)   
Paula Czarnowska (University of Cambridge, UK)   
Ran Zmigrod (University of Cambridge, UK)   
Rowan Hall Maudslay (University of Cambridge, UK)   
Svetlana Toldova (National Research University Higher School of Economics, Russia)   
Tiago Pimentel (University of Cambridge, UK)   
Tim Arkhangelskij (University of Hamburg, Germany)   
