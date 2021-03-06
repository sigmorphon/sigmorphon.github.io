---
layout: page
longtitle: "Task  - SIGMORPHON 2020 Shared Task: Grapheme-to-Phoneme, Unsupervised Induction of Morphology, and Typologically Diverse Morphological Inflection"
title: "Task 0: Typologically Diverse Morphological Inflection"
---

SIGMORPHON’s fifth installment of its inflection generation shared task focuses on languages that are typologically diverse from languages in our previous tasks. Many of these languages are extremely low-resource. In this edition, we are specifically interested in inflection generation systems’ ability to generalize to new languages, including languages that are typologically distinct. For example, if you have a neural network architecture that works well for a sample of Indo-European languages, should you expect the same architecture to also work well for Tupi–Guarani languages (where nouns are “declined” for tense)? The organizers suspect not, but you could prove us wrong!

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
* [Contact](#contact)
* [Task Organization](#task-organization)


## Shared Task Description 

In this shared task, participants will design a model that learns to generate morphological inflections from a lemma and a set of morphosyntactic features of the target form. Each language in the task has its own training, development, and test splits. Training and development splits contain triples, each consisting of a lemma, a target form, and a set of morphological features, provided in the UniMorph format (the “Data” section below provides an example of input format). Test splits only provide lemmas and morphological tags: your model will need to predict the missing target form. 

The model should be general enough to work for natural languages of any typological patterning.<sup>1</sup> For example, Tagalog verbs exhibit [circumfixation](https://en.wikipedia.org/wiki/Circumfix); thus, a model with a strong inductive bias towards suffixing will likely not work well for Tagalog. The task will proceed in three phases: a Development Phase, a Generalization Phase, and an Evaluation Phase. As the task progresses, more data and more languages will be released.

In the Development Phase, we will provide training and development splits from the Austronesian, Niger-Congo, Oto-Manguean, Uralic and Indo-European language families that should be used to *develop* your system. We will refer to them as the *development languages*.  See the [table below](#development_langs) for a complete list.

In the Generalization Phase, we will provide training and development splits for new languages where approximately half are genetically related (belong to the same family) and half are genetically *unrelated* (are isolates or belong to a different family) to the development languages. We will keep the languages in the Generalization Phase a surprise until April 2020 (see [timeline](#timeline)). We will also keep the genetically unrelated language *families* a surprise, though some languages will come from the same families as those in the Development Phase. 
 
In the Evaluation Phase, the participants’ models will be evaluated on held-out forms from all of the languages from the previous phases. The languages from the Development Phase and the Generalization Phase are evaluated simultaneously. The only difference is that there has been more time to construct a model for those languages released in the Development Phase. It follows that a model could easily overfit to or favor phenomena that are more frequent in languages presented in the Development Phase, especially if parameters are shared across languages. For instance, a model based on the morphological patterning of the Indo-European languages may end up with a bias towards suffixing and will struggle to learn prefixing or circumfixation, the degree to which only becomes apparent during experimentation on other languages whose inflectional morphology patterns differ. Of course, the model architecture itself could explicitly or implicitly favor certain word formation types (suffixing, prefixing, etc.).

<sup>1</sup> See [References](#references)


**Glossary**

The shared task features both held-out morphological inflection triples and surprise languages. The organizers created a short glossary of task-specific terminology for clarity. We use the language described in this glossary unambiguously throughout the task description.

* **Development language**: A language for which the participants will have an elongated period of time (about two months) to construct a machine learning model for morphological inflection generation.
* **Surprise language**: A language for which the participants will have a short period of time (about one week) to construct or adapt a machine learning model for morphological inflection generation. The idea is that the participants apply the knowledge accrued from the Development Phase to choose a good model and good hyperparameters. Most of the surprise languages will be *typologically distinct* from the development languages, i.e. the majority of the languages will be taken from language families other than the ones used during the Development Phase.
* **Training split**: A selection of lemma–form–tag triples for a language (either development or surprise) that the participants may train their machine learning model on.
* **Development split**: A selection of lemma–form–tag triples for a language (either development or surprise) that the participants may tune the hyperparameters of their machine learning model on.
* **Test split**: A selection of lemma–tag pairs for a language (either development or surprise) for which the participants will predict target forms. The organizers will evaluate the models based on these predictions.


## Timeline

**Stage 1: Development Phase**
* February 24th, 2020: Training and development splits for development languages released; we invite participants to report errors.
* February 24th, 2020: Neural and non-neural baselines for development languages released.
* March 1st, 2020: Development language data are frozen.  

**Stage 2: Generalization Phase**
* <del>April 13th</del> April 20, 2020: Training and development splits for surprise languages released.   
(This is not a zero-shot learning task. Participants will be given training data for all languages.)  

**Stage 3: Evaluation Phase**
* <del>April 20th</del> April 27, 2020: Test splits for all languages (both development and surprise) released.
* <del>April 27th</del> May 4, 2020: Participants submit test predictions on all languages.  

**Stage 4: Write-up Phase**
* <del>May 11th</del> May 17, 2020: Participants’ system description papers due.  
* <del>May 18th</del> May 24, 2020: Participants’ system description papers camera ready due.  
 

## Data
The training and development data are provided in a simple utf-8 encoded text format for both the development and surprise languages. Each line in a file is an example that consists of word forms and corresponding morphosyntactic descriptions (MSDs) provided as a set of features, separated by semicolons. We refer to the MSDs as (morphological) tags for simplicity. The fields on a line are TAB-separated.
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


<table>
    <tr>
        <td><sub><b>Language</b></sub></td>
        <td><sub><b>ISO 639-3</b></sub></td>
        <td><sub><b>Family</b></sub></td>
        <td><sub><b>Genus</b></sub></td>
        <td><sub><b># Train</b></sub></td>
        <td><sub><b># Dev</b></sub></td>
    </tr>
    <tr>
        <td><sub>Malagasy</sub></td>
        <td><sub>mlg</sub></td>
        <td><sub>Austronesian</sub></td>
        <td><sub>Barito</sub></td>
        <td><sub>447</sub></td>
        <td><sub>62</sub></td>
    </tr>
    <tr>
        <td><sub>Cebuano</sub></td>
        <td><sub>ceb</sub></td>
        <td><sub>Austronesian</sub></td>
        <td><sub>Greater Central Phillipine</sub></td>
        <td><sub>420</sub></td>
        <td><sub>58</sub></td>
    </tr>
    <tr>
        <td><sub>Hiligaynon</sub></td>
        <td><sub>hil</sub></td>
        <td><sub>Austronesian</sub></td>
        <td><sub>Greater Central Phillipine</sub></td>
        <td><sub>859</sub></td>
        <td><sub>116</sub></td>
    </tr>
    <tr>
        <td><sub>Tagalog</sub></td>
        <td><sub>tgl</sub></td>
        <td><sub>Austronesian</sub></td>
        <td><sub>Greater Central Phillipine</sub></td>
        <td><sub>1870</sub></td>
        <td><sub>236</sub></td>
    </tr>
    <tr>
        <td><sub>Maori</sub></td>
        <td><sub>mao</sub></td>
        <td><sub>Austronesian</sub></td>
        <td><sub>Oceanic</sub></td>
        <td><sub>145</sub></td>
        <td><sub>21</sub></td>
    </tr>
    <tr>
        <td><sub>Danish</sub></td>
        <td><sub>dan</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>North Germanic</sub></td>
        <td><sub>17852</sub></td>
        <td><sub>2550</sub></td>
    </tr>
    <tr>
        <td><sub>Icelandic</sub></td>
        <td><sub>isl</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>North Germanic</sub></td>
        <td><sub>53841</sub></td>
        <td><sub>7690</sub></td>
    </tr>
    <tr>
        <td><sub>Norwegian Bokmål</sub></td>
        <td><sub>nob</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>North Germanic</sub></td>
        <td><sub>13263</sub></td>
        <td><sub>1929</sub></td>
    </tr>
    <tr>
        <td><sub>Swedish</sub></td>
        <td><sub>swe</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>North Germanic</sub></td>
        <td><sub>54888</sub></td>
        <td><sub>7840</sub></td>
    </tr>
    <tr>
        <td><sub>Dutch</sub></td>
        <td><sub>nld</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>38826</sub></td>
        <td><sub>5547</sub></td>
    </tr>
    <tr>
        <td><sub>English</sub></td>
        <td><sub>eng</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>80865</sub></td>
        <td><sub>11553</sub></td>
    </tr>
    <tr>
        <td><sub>German</sub></td>
        <td><sub>deu</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>99405</sub></td>
        <td><sub>14201</sub></td>
    </tr>
    <tr>
        <td><sub>Middle High German</sub></td>
        <td><sub>gmh</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>496</sub></td>
        <td><sub>71</sub></td>
    </tr>
    <tr>
        <td><sub>North Frisian</sub></td>
        <td><sub>frr</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>1902</sub></td>
        <td><sub>224</sub></td>
    </tr>
    <tr>
        <td><sub>Old English</sub></td>
        <td><sub>ang</sub></td>
        <td><sub>Indo-European</sub></td>
        <td><sub>West Germanic</sub></td>
        <td><sub>29270</sub></td>
        <td><sub>4122</sub></td>
    </tr>
    <tr>
        <td><sub>Chewa</sub></td>
        <td><sub>nya</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>3059</sub></td>
        <td><sub>429</sub></td>
    </tr>
    <tr>
        <td><sub>Kongo</sub></td>
        <td><sub>kon</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>568</sub></td>
        <td><sub>76</sub></td>
    </tr>
    <tr>
        <td><sub>Lingala</sub></td>
        <td><sub>lin</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>159</sub></td>
        <td><sub>23</sub></td>
    </tr>
    <tr>
        <td><sub>Luganda</sub></td>
        <td><sub>lug</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>3420</sub></td>
        <td><sub>489</sub></td>
    </tr>
    <tr>
        <td><sub>Sotho</sub></td>
        <td><sub>sot</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>345</sub></td>
        <td><sub>50</sub></td>
    </tr>
    <tr>
        <td><sub>Swahili</sub></td>
        <td><sub>swa</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>3374</sub></td>
        <td><sub>469</sub></td>
    </tr>
    <tr>
        <td><sub>Zulu</sub></td>
        <td><sub>zul</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Bantu</sub></td>
        <td><sub>322</sub></td>
        <td><sub>42</sub></td>
    </tr>
    <tr>
        <td><sub>Akan</sub></td>
        <td><sub>aka</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Kwa</sub></td>
        <td><sub>2793</sub></td>
        <td><sub>380</sub></td>
    </tr>
    <tr>
        <td><sub>Gã</sub></td>
        <td><sub>gaa</sub></td>
        <td><sub>Niger-Congo</sub></td>
        <td><sub>Kwa</sub></td>
        <td><sub>607</sub></td>
        <td><sub>79</sub></td>
    </tr>
    <tr>
        <td><sub>Tlatepuzco Chinantec</sub></td>
        <td><sub>cpa</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Chinantecan</sub></td>
        <td><sub>5298</sub></td>
        <td><sub>727</sub></td>
    </tr>
    <tr>
        <td><sub>San Pedro Amuzgo Amuzgos</sub></td>
        <td><sub>azg</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Amuzgo-Mixtecan</sub></td>
        <td><sub>8482</sub></td>
        <td><sub>1188</sub></td>
    </tr>
    <tr>
        <td><sub>Yoloxóchitl Mixtec</sub></td>
        <td><sub>xty</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Amuzgo-Mixtecan</sub></td>
        <td><sub>2110</sub></td>
        <td><sub>299</sub></td>
    </tr>
    <tr>
        <td><sub>Chichicapan Zapotec</sub></td>
        <td><sub>zpv</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Popolocal-Zapotecan</sub></td>
        <td><sub>805</sub></td>
        <td><sub>113</sub></td>
    </tr>
    <tr>
        <td><sub>Yaitepec Chatino</sub></td>
        <td><sub>ctp</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Popolocal-Zapotecan</sub></td>
        <td><sub>2397</sub></td>
        <td><sub>313</sub></td>
    </tr>
    <tr>
        <td><sub>Zenzontepec Chatino</sub></td>
        <td><sub>czn</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Popolocal-Zapotecan</sub></td>
        <td><sub>1088</sub></td>
        <td><sub>154</sub></td>
    </tr>
    <tr>
        <td><sub>Eastern Highland Chatino</sub></td>
        <td><sub>cly</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Popolocal-Zapotecan</sub></td>
        <td><sub>3301</sub></td>
        <td><sub>471</sub></td>
    </tr>
    <tr>
        <td><sub>Eastern Highland Otomi</sub></td>
        <td><sub>otm</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Oto-Pamean</sub></td>
        <td><sub>21533</sub></td>
        <td><sub>3020</sub></td>
    </tr>
    <tr>
        <td><sub>Mezquital Otomi</sub></td>
        <td><sub>ote</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Oto-Pamean</sub></td>
        <td><sub>22962</sub></td>
        <td><sub>3231</sub></td>
    </tr>
    <tr>
        <td><sub>Chichimec</sub></td>
        <td><sub>pei</sub></td>
        <td><sub>Oto-Manguean</sub></td>
        <td><sub>Oto-Pamean</sub></td>
        <td><sub>10017</sub></td>
        <td><sub>1349</sub></td>
    </tr>
    <tr>
        <td><sub>Estonian</sub></td>
        <td><sub>est</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>26728</sub></td>
        <td><sub>3820</sub></td>
    </tr>
    <tr>
        <td><sub>Finnish</sub></td>
        <td><sub>fin</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>99403</sub></td>
        <td><sub>14201</sub></td>
    </tr>
    <tr>
        <td><sub>Ingrian</sub></td>
        <td><sub>izh</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>763</sub></td>
        <td><sub>112</sub></td>
    </tr>
    <tr>
        <td><sub>Karelian</sub></td>
        <td><sub>krl</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>80216</sub></td>
        <td><sub>11225</sub></td>
    </tr>
    <tr>
        <td><sub>Livonian</sub></td>
        <td><sub>liv</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>2787</sub></td>
        <td><sub>398</sub></td>
    </tr>
    <tr>
        <td><sub>Veps</sub></td>
        <td><sub>vep</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>94395</sub></td>
        <td><sub>13320</sub></td>
    </tr>
    <tr>
        <td><sub>Votic</sub></td>
        <td><sub>vot</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Finnic</sub></td>
        <td><sub>1003</sub></td>
        <td><sub>146</sub></td>
    </tr>
    <tr>
        <td><sub>Meadow Mari</sub></td>
        <td><sub>mhr</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Mari</sub></td>
        <td><sub>71143</sub></td>
        <td><sub>10081</sub></td>
    </tr>
    <tr>
        <td><sub>Erzya</sub></td>
        <td><sub>myv</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Mordvinic</sub></td>
        <td><sub>74929</sub></td>
        <td><sub>10738</sub></td>
    </tr>
    <tr>
        <td><sub>Moksha</sub></td>
        <td><sub>mdf</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Mordvinic</sub></td>
        <td><sub>46362</sub></td>
        <td><sub>6633</sub></td>
    </tr>
    <tr>
        <td><sub>Northern Sami</sub></td>
        <td><sub>sme</sub></td>
        <td><sub>Uralic</sub></td>
        <td><sub>Sami</sub></td>
        <td><sub>43877</sub></td>
        <td><sub>6273</sub></td>
    </tr>
</table>

<sup>2</sup>The organizers may increase the number of total languages, if annotation efforts allow.


**Surprise Languages** 

The remaining 45 of these 90 languages will be *surprise languages*. The shared task organizers will provide the participants with enough time (about a week according to the current timeline) to train a model that they have previously selected on the development languages. However, there will not be enough time for choosing a new model or extensive hyperparameter tuning. 

Which languages? ~~They’re a surprise!~~ Surprise no longer! 


<table>
  <tr>
    <td><sub><b>Language</b></sub></td>
    <td><sub><b>ISO 639-3</b></sub></td>
    <td><sub><b>Family</b></sub></td>
    <td><sub><b># Train</b></sub></td>
    <td><sub><b># Dev</b></sub></td>
  </tr>
  <tr>
    <td><sub>Maltese</sub></td>
    <td><sub>mlt</sub></td>
    <td><sub>Afro-Asiatic</sub></td>
    <td><sub>1233</sub></td>
    <td><sub>176</sub></td>
  </tr>
  <tr>
    <td><sub>Oromo</sub></td>
    <td><sub>orm</sub></td>
    <td><sub>Afro-Asiatic</sub></td>
    <td><sub>1424</sub></td>
    <td><sub>203</sub></td>
  </tr>
  <tr>
    <td><sub>Classical Syriac</sub></td>
    <td><sub>syc</sub></td>
    <td><sub>Afro-Asiatic</sub></td>
    <td><sub>1917</sub></td>
    <td><sub>275</sub></td>
  </tr>
  <tr>
    <td><sub>Cree</sub></td>
    <td><sub>cre</sub></td>
    <td><sub>Algic</sub></td>
    <td><sub>4571</sub></td>
    <td><sub>584</sub></td>
  </tr>
  <tr>
    <td><sub>Murrinh-Patha</sub></td>
    <td><sub>mwf</sub></td>
    <td><sub>Australian</sub></td>
    <td><sub>777</sub></td>
    <td><sub>111</sub></td>
  </tr>
  <tr>
    <td><sub>Kannada</sub></td>
    <td><sub>kan</sub></td>
    <td><sub>Dravidian</sub></td>
    <td><sub>3670</sub></td>
    <td><sub>524</sub></td>
  </tr>
  <tr>
    <td><sub>Telugu</sub></td>
    <td><sub>tel</sub></td>
    <td><sub>Dravidian</sub></td>
    <td><sub>952</sub></td>
    <td><sub>136</sub></td>
  </tr>
  <tr>
    <td><sub>Middle Low German</sub></td>
    <td><sub>gml</sub></td>
    <td><sub>Germanic</sub></td>
    <td><sub>890</sub></td>
    <td><sub>127</sub></td>
  </tr>
  <tr>
    <td><sub>Swiss German</sub></td>
    <td><sub>gsw</sub></td>
    <td><sub>Germanic</sub></td>
    <td><sub>1345</sub></td>
    <td><sub>192</sub></td>
  </tr>
  <tr>
    <td><sub>Norwegian Nynorsk</sub></td>
    <td><sub>nno</sub></td>
    <td><sub>Germanic</sub></td>
    <td><sub>10101</sub></td>
    <td><sub>1443</sub></td>
  </tr>
  <tr>
    <td><sub>Bengali</sub></td>
    <td><sub>ben</sub></td>
    <td><sub>Indo-Aryan</sub></td>
    <td><sub>2816</sub></td>
    <td><sub>402</sub></td>
  </tr>
  <tr>
    <td><sub>Hindi</sub></td>
    <td><sub>hin</sub></td>
    <td><sub>Indo-Aryan</sub></td>
    <td><sub>36300</sub></td>
    <td><sub>5186</sub></td>
  </tr>
  <tr>
    <td><sub>Sanskrit</sub></td>
    <td><sub>san</sub></td>
    <td><sub>Indo-Aryan</sub></td>
    <td><sub>22968</sub></td>
    <td><sub>3188</sub></td>
  </tr>
  <tr>
    <td><sub>Urdu</sub></td>
    <td><sub>urd</sub></td>
    <td><sub>Indo-Aryan</sub></td>
    <td><sub>8486</sub></td>
    <td><sub>1213</sub></td>
  </tr>
  <tr>
    <td><sub>Persian</sub></td>
    <td><sub>fas</sub></td>
    <td><sub>Iranian</sub></td>
    <td><sub>25225</sub></td>
    <td><sub>3603</sub></td>
  </tr>
  <tr>
    <td><sub>Pushto; Pashto</sub></td>
    <td><sub>pus</sub></td>
    <td><sub>Iranian</sub></td>
    <td><sub>4861</sub></td>
    <td><sub>695</sub></td>
  </tr>
  <tr>
    <td><sub>Tajik</sub></td>
    <td><sub>tgk</sub></td>
    <td><sub>Iranian</sub></td>
    <td><sub>53</sub></td>
    <td><sub>8</sub></td>
  </tr>
  <tr>
    <td><sub>Shona</sub></td>
    <td><sub>sna</sub></td>
    <td><sub>Niger-Congo</sub></td>
    <td><sub>1897</sub></td>
    <td><sub>246</sub></td>
  </tr>
  <tr>
    <td><sub>Zarma</sub></td>
    <td><sub>dje</sub></td>
    <td><sub>Nilo-Sahan</sub></td>
    <td><sub>56</sub></td>
    <td><sub>9</sub></td>
  </tr>
  <tr>
    <td><sub>Asturian</sub></td>
    <td><sub>ast</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>5096</sub></td>
    <td><sub>728</sub></td>
  </tr>
  <tr>
    <td><sub>Catalan</sub></td>
    <td><sub>cat</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>51944</sub></td>
    <td><sub>7421</sub></td>
  </tr>
  <tr>
    <td><sub>Middle French</sub></td>
    <td><sub>frm</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>24612</sub></td>
    <td><sub>3516</sub></td>
  </tr>
  <tr>
    <td><sub>Friulian</sub></td>
    <td><sub>fur</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>5408</sub></td>
    <td><sub>772</sub></td>
  </tr>
  <tr>
    <td><sub>Galician</sub></td>
    <td><sub>glg</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>24087</sub></td>
    <td><sub>3441</sub></td>
  </tr>
  <tr>
    <td><sub>Ladin</sub></td>
    <td><sub>lld</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>5073</sub></td>
    <td><sub>725</sub></td>
  </tr>
  <tr>
    <td><sub>Venetian</sub></td>
    <td><sub>vec</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>12203</sub></td>
    <td><sub>1743</sub></td>
  </tr>
  <tr>
    <td><sub>Anglo-Norman</sub></td>
    <td><sub>xno</sub></td>
    <td><sub>Romance</sub></td>
    <td><sub>178</sub></td>
    <td><sub>26</sub></td>
  </tr>
  <tr>
    <td><sub>Tibetan</sub></td>
    <td><sub>bod</sub></td>
    <td><sub>Sino-Tibetan</sub></td>
    <td><sub>3428</sub></td>
    <td><sub>466</sub></td>
  </tr>
  <tr>
    <td><sub>Dakota</sub></td>
    <td><sub>dak</sub></td>
    <td><sub>Siouan</sub></td>
    <td><sub>2636</sub></td>
    <td><sub>376</sub></td>
  </tr>
  <tr>
    <td><sub>Evenki</sub></td>
    <td><sub>evn</sub></td>
    <td><sub>Tungusic</sub></td>
    <td><sub>5413</sub></td>
    <td><sub>774</sub></td>
  </tr>
  <tr>
    <td><sub>Azerbaijani</sub></td>
    <td><sub>aze</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>5602</sub></td>
    <td><sub>801</sub></td>
  </tr>
  <tr>
    <td><sub>Bashkir</sub></td>
    <td><sub>bak</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>8517</sub></td>
    <td><sub>1217</sub></td>
  </tr>
  <tr>
    <td><sub>Crimean Tatar; Crimean Turkish</sub></td>
    <td><sub>crh</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>5215</sub></td>
    <td><sub>745</sub></td>
  </tr>
  <tr>
    <td><sub>Kazakh</sub></td>
    <td><sub>kaz</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>7852</sub></td>
    <td><sub>1063</sub></td>
  </tr>
  <tr>
    <td><sub>Kyrgyz</sub></td>
    <td><sub>kir</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>3855</sub></td>
    <td><sub>547</sub></td>
  </tr>
  <tr>
    <td><sub>Khakas</sub></td>
    <td><sub>kjh</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>840</sub></td>
    <td><sub>120</sub></td>
  </tr>
  <tr>
    <td><sub>Turkmen</sub></td>
    <td><sub>tuk</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>20963</sub></td>
    <td><sub>2992</sub></td>
  </tr>
  <tr>
    <td><sub>Uighur; Uyghur</sub></td>
    <td><sub>uig</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>5372</sub></td>
    <td><sub>750</sub></td>
  </tr>
  <tr>
    <td><sub>Uzbek</sub></td>
    <td><sub>uzb</sub></td>
    <td><sub>Turkic</sub></td>
    <td><sub>25199</sub></td>
    <td><sub>3596</sub></td>
  </tr>
  <tr>
    <td><sub>Komi-Zyrian</sub></td>
    <td><sub>kpv</sub></td>
    <td><sub>Uralic</sub></td>
    <td><sub>57919</sub></td>
    <td><sub>8263</sub></td>
  </tr>
  <tr>
    <td><sub>Ludian</sub></td>
    <td><sub>lud</sub></td>
    <td><sub>Uralic</sub></td>
    <td><sub>294</sub></td>
    <td><sub>41</sub></td>
  </tr>
  <tr>
    <td><sub>Livvi</sub></td>
    <td><sub>olo</sub></td>
    <td><sub>Uralic</sub></td>
    <td><sub>43936</sub></td>
    <td><sub>6260</sub></td>
  </tr>
  <tr>
    <td><sub>Udmurt</sub></td>
    <td><sub>udm</sub></td>
    <td><sub>Uralic</sub></td>
    <td><sub>88774</sub></td>
    <td><sub>12665</sub></td>
  </tr>
  <tr>
    <td><sub>Võro</sub></td>
    <td><sub>vro</sub></td>
    <td><sub>Uralic</sub></td>
    <td><sub>357</sub></td>
    <td><sub>51</sub></td>
  </tr>
  <tr>
    <td><sub>Papago (O'odham)</sub></td>
    <td><sub>ood</sub></td>
    <td><sub>Uto-Aztecan</sub></td>
    <td><sub>1123</sub></td>
    <td><sub>160</sub></td>
  </tr>
</table>


**Multilingual Modeling [Recommendation]**

Many of the languages in the shared task have only a few morphological forms annotated. In most cases, this is not because we have a larger stash that we are withholding, but rather because there is no resource known to the organizers for such data. To model these low-resource languages well, the organizers *recommend* a multilingual approach that exploits the genetic similarity within the development and surprise languages provided. For instance, we only give the participants a handful of lemma–form–tag triples of, say, Kongo, generalization will be difficult without using data from related Niger-Congo languages. 


**Restrictions**

Additional UniMorph (and ICGI) data beyond what is provided is not allowed for model training. There are no other restrictions about what sort of data you can use for this task. For example, if you would like to use a large, unlabeled corpus, such as Wikipedia, that is acceptable. You may also use a pre-trained language model, e.g. BERT ([Devlin et al. 2019](https://www.aclweb.org/anthology/N19-1423/)). However, we will evaluate models in two different categories: (1) those that use external resources (beyond what is provided by the task), and (2) those that do not. The constrained data category (2) will be restricted to monolingual models, while category (1) may include multilingual models -- we encourage you to be creative! Participants are asked to clearly specify the submission category. 


## Evaluation

Our shared task also comes with a somewhat novel experimental design. We will simultaneously evaluate models for both the Development languages, whose training and development sets will be available for an elongated period of time, and the Surprise languages, whose training and development sets will only be available for a short time prior to submission, which precludes extensive tuning. To be officially ranked, you must submit results for **all** evaluation languages. Thus, to succeed, your class of models (e.g. neural sequence-to-sequence models or weighted finite-state transducers with hand-crafted features) must generalize well to the group of Surprise languages that are typologically distinct from the Development languages you performed model selection on. To repeat: This is not a zero-shot learning task, but rather our evaluation set-up is designed to test the inherent inductive bias in the participants’ chosen model class. We attribute the inspiration for this experimental design to [Emily Bender](https://faculty.washington.edu/ebender/), who often [advocates for such positions](https://thegradient.pub/the-benderrule-on-naming-the-languages-we-study-and-why-it-matters/).

We will simultaneously evaluate the accuracy on held-out forms for languages from the following three categories of languages separately: 1) held-out forms from the Development languages, 2) held-out forms from genetically related Surprise languages, and 3) held-out forms from genetically unrelated Surprise languages. This tripartite split should give the field insight into how reliable performance of certain classes of models are on typologically distinct languages. It should also help answer the following question: If my model class works well when trained on English and many others, will the same model class work well on languages which exhibit linguistic characteristics distinct from English?

As mentioned in Restrictions above, we will evaluate submissions in two categories: monolingual, constrained data models, and unconstrained -- the world is your oyster!


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

Participants’ system description papers will be handled through softconf. Papers can be submitted at <https://www.softconf.com/acl2020/SIGMORPHON/>


## References

Anastasopoulos and Neubig. [“Pushing the Limits of Low-Resource Morphological Inflection.”](https://www.aclweb.org/anthology/D19-1091/) Proceedings of EMNLP 2019.  

Cotterell et al. [“CoNLL-SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection in 52 Languages.”](https://www.aclweb.org/anthology/K17-2001/) Proceedings of the CoNLL-SIGMORPHON 2017 Shared Task.  

Cotterell et al. [“The CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection.”](https://www.aclweb.org/anthology/K18-3001/) Proceedings of the CoNLL–SIGMORPHON 2018 Shared Task: Universal Morphological Reinflection.  

Devlin et al. [“BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.”](https://www.aclweb.org/anthology/N19-1423/) Proceedings of NAACL 2019.  

Vaswani et al. [“Attention is All You Need.”](https://papers.nips.cc/paper/7181-attention-is-all-you-need.pdf) Proceedings of NeurIPS 2017.  

*Introduction into morphology:*   
&nbsp;&nbsp;&nbsp; Haspelmath, M. (2002). [*Understanding Morphology*](https://www.researchgate.net/publication/271018639_Understanding_Morphology). Oxford University Press,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; USA.  
&nbsp;&nbsp;&nbsp; Aronoff, M., & Fudeman, K. (2011). [*What is Morphology?*](http://www.ucd.ie/artspgs/introling/Aronoffmorphology.pdf) (Vol. 8). John Wiley & Sons.

*More detailed studies on morphological typology:*   
&nbsp;&nbsp;&nbsp; Baerman, M. (Ed.). (2015). *The Oxford Handbook of Inflection*. Oxford University Press,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; USA.  
&nbsp;&nbsp;&nbsp; Song, J. J. (2014). *Linguistic Typology: Morphology and Syntax*. Routledge.  
&nbsp;&nbsp;&nbsp; Song, J. J. (2010). *The Oxford handbook of Linguistic Typology*. USA.  
&nbsp;&nbsp;&nbsp; Malchukov, A. and Spencer, A. (2008). *The Handbook of Case*. Oxford University Press,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; USA.  

*Language-specific descriptions:*  
&nbsp;&nbsp;&nbsp; You may find more detailed information on some languages here: [https://langsci-press.org/series](https://langsci-press.org/series)


## Contact

Point of Contact: [Ekaterina Vylomova](mailto:evylomova@gmail.com)  
Discussion: [Task 0 Google Group](https://groups.google.com/forum/#!forum/sigmorphon2020-task0)  
Submission: [sigmorphon2020sharedtask@gmail.com](mailto:sigmorphon2020sharedtask@gmail.com)  


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
Ilya Yegorov (Lomonosov Moscow State University, Russia)   
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


