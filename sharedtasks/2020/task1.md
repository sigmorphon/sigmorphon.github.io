---
layout: page
longtitle: "Task  - SIGMORPHON 2020 Shared Task: Grapheme-to-Phoneme, Unsupervised Induction of Morphology, and Typologically Diverse Morphological Inflection"
title: "Task 1: Multilingual Grapheme-to-Phoneme Conversion"
---

In this task, participants will create computational models that map a sequence
of "graphemes"---characters---representing a word to a transcription of that
word's pronunciation.

This task is an important part of speech technologies including recognition and
synthesis.

Data
----

### Source

The data is primarily extracted from [Wiktionary](https://www.wiktionary.org/)
using the [`wikipron`](https://github.com/kylebgorman/wikipron) library (Lee et
al. in press).

### Languages

We initially provide data for 10 languages:

1.  Armenian (`arm`)
2.  Bulgarian (`bul`)
3.  French (`fre`)
4.  Georgian (`geo`)
5.  Hindi (`hin`)
6.  Hungarian (`hun`)
7.  Icelandic (`ice`)
8.  Korean (`kor`)
9.  Lithuanian (`lit`)
10. Modern Greek (`gre`)


**Update (2020-04-20)**: the surprise langauges are now announced. They are:

1.  Adyghe (`ady`)
2.  Dutch (`dut`)
3.  Japanese hiragana (`jpn`)
4.  Romanian (`rum`)
5.  Vietnamese (`vie`)

Baseline results
================

Results for the three baselines will be made available
[here](https://docs.google.com/spreadsheets/d/1g0HyGeVzFrNt2pvNuu8L1voFFQY-0CwjTxGA3VXXNGI/edit?usp=sharing)
as they become available.

### Size

There are 3600 training data examples and 450 development and test data examples
for each language.

### Format

Training and development data are UTF-8-encoded tab-separated values files. Each
example occupies a single line and consists of a grapheme
sequence---[NFC](https://en.wikipedia.org/wiki/Unicode_equivalence#Normal_forms)
Unicode codepoints---a tab character, and the corresponding phone sequence, a
roughly-phonemic
[IPA](https://en.wikipedia.org/wiki/International_Phonetic_Alphabet), tokenized
using the [`segments`](https://github.com/cldf/segments) library (Moran & Cysouw
2018). The following show three lines of Romanian data:

    antonim a n t o n i m
    ploaie  p lʷ a j e
    pornește    p o r n e ʃ t e

Test files consist of a single column, containing grapheme sequences.

Please provide your results in the two-column (grapheme sequence, tab-character,
tokenized phone sequence) TSV format, the same one used for the training and
development data. If your system only provides the predicted phone sequences,
use the UNIX command-line tool `paste` to combine the columns.


Data can be obtained [here]( https://github.com/sigmorphon/2020/tree/master/task1/data).

### Exclusions

We exclude from the provided data any words which:

-   have multiple pronunciations in the source data
-   consist of less than 3 graphemes, or
-   consist of less than 3 phonemes.

### External data

Participants are **permitted** to use:

-   open-source databases of phoneme inventories and features such as
    [Phoible](https://phoible.org/) (Moran & McCloy 2019),
-   open-source pronunciation data for languages not targeted in this challenge,
    and
-   open-source morphological analyzers and lexicons such as
    [UDLexicons](https://www.aclweb.org/anthology/L18-1292/) (Sagot 2018).

Participants who use such data must disclose their use of it at time of
submission.

Participants are **not permitted** to use any form of pronunciation data derived
from Wiktionary, except for the provided training and test data; they are also
**not permitted** to use external pronunciation dictionaries for any of the
targeted languages.

Evaluation
----------

Systems should predict a single phone sequence for each test example.

### Metrics

The primary measure will be the word error rate (WER), which is the percentage
of words for which the hypothesized transcription sequence does not match the
gold transcription. We also report phone error rate (PER), the micro-averaged
edit distance between hypotheses and gold transcriptions, computed by summing
the minimum edit distance between the hypothesis and gold transcriptions and
then dividing by the summed length of the gold transcriptions. As is common
practice, we multiply both numbers by 100. Both metrics will be computed using
the provided Python script `evaluate.py`, available [here](https://github.com/sigmorphon/2020/blob/master/task1/evaluation/evaluate.py).


### System comparison

We will evaluate on each language separately. The final system ranking will be
produced by macro-averaging the per-language WERs. We will also employ
statistical analysis for system comparison.

Baselines
---------

We provide implementations of two baseline systems for the task:

-   a pair n-gram model (Novak et al. 2016) implemented using the [OpenGrm
    toolkit](http://opengrm.org/) (Roark et al. 2012, Gorman 2016), and
-   a bidirectional LSTM encoder-decoder sequence model implemented using the
    [Fairseq toolkit](https://github.com/pytorch/fairseq) (Ott et al. 2019).
    

The baselines are available [here](https://github.com/sigmorphon/2020/tree/master/task1/baselines).

Participants are welcome to adapt these baselines for their purposes.


## Submission

Participants will submit to this task by sending their models' predictions to 
[sigmorphon2020.task1@gmail.com](mailto:sigmorphon2020.task1@gmail.com) by April 27th, 2020. 
Participants may submit predictions from as many models as they wish; each submission will be scored separately. 
Participants must submit predictions for all languages to be scored. 
Participants must specify any external resources used at time of submission.

System description papers will be submitted using [softconf](https://www.softconf.com/) - links will be provided at a later date.

## Timeline

* February 24th, 2020: Training and development splits for development languages released; we invite participants to report errors.
* February 24th, 2020: Neural and non-neural baselines for development languages released.
* April <del>13th</del> 20th, 2020: Training and development splits for surprise languages released.   
* April <del>20th</del> 27th, 2020: Test splits for all languages (both development and surprise) released.
* <del>April 27th</del> May 5th, 2020: Participants submit test predictions on all languages.  
* May <del>4th</del> 11th, 2020: Participants’ system description papers due.  
* May <del>18th</del> 25th, 2020: Participants’ system description papers camera ready due.  


Overview paper
--------------

In an overview paper for the shared task, we will compare the performance of
submitted systems in detail. We will assess:

-   which systems are significantly different in performance
-   which languages were challenging and which types of systems succeeded on
    them, and
-   which systems would provide complementary benefit in an ensemble system.

Included in the paper will be a summary of scores for all participants who
produce outputs for all targeted languages.

Organizers
----------

This task is organized by Lucas Ashby and Kyle Gorman at the [Graduate Center,
City University of New
York](https://www.gc.cuny.edu/Page-Elements/Academics-Research-Centers-Initiatives/Doctoral-Programs/Linguistics/Linguistics?gclid=Cj0KCQiA4sjyBRC5ARIsAEHsELHv8TTKiWAj74vMEHsPdp8xF2zs3ploIj-n_2FiOjpO81kASYtduk8aAj17EALw_wcB),
with help from other members of the [WikiPron
team](https://github.com/kylebgorman/wikipron/graphs/contributors).

Contact: [Kyle Gorman](mailto:kgorman@gc.cuny.edu).

References
----------

Gorman, K. (2016). Pynini: a Python library for weighted finite-state grammar
compilation. In *Proceedings of the SIGFSM Workshop on Statistical NLP and
Weighted Automata*, pages 75--80, Berlin. Association for Computational
Linguistics.

Lee, J. L, Ashby, L. F.E., Garza, M. E., Lee-Sikka, Y., Miller, S., Wong, A.,
McCarthy, A. D., and Gorman, K. (in press). *Massively multilingual
pronunciation mining with WikiPron*. To appear in the proceedings of LREC 2020.

Moran, S. and Cysouw, M. (2018). *The Unicode cookbook for linguists: managing
writing systems using orthography profiles*. Berlin: Language Science Press.

Moran, S. and McCloy, D. (2019). *PHOIBLE 2.0*. Jena: Max Planck Institute for
the Science of Human History.

Novak, J. R., Minematsu, N., and Hirose, K. (2016). Phonetisaurus: exploring
grapheme-to-phoneme conversion with joint n-gram models in the WFST framework.
*Natural Language Engineering*, 22(6):907--938.

Ott, M., Edunov, S., Baevski, A., Fan, A., Gross, S., Ng, N., Grangier, D., and
Auli, M. (2019). fairseq: a fast, extensible toolkit for sequence modeling. In
*Proceedings of the 2019 Conference of the North American Chapter of the
Association for Computational Linguistics (Demonstrations)*, pages 48--53,
Minneapolis. Association for Computational Linguistics.

Roark, B., Sproat, R., Allauzen, C., Riley, M., Sorensen, J., and Tai, T.
(2012). The OpenGrm open-source finite-state grammar software libraries. In
*Proceedings of the ACL 2012 System Demonstrations*, pages 61--66, Jeju Island,
Korea. Association for Computational Linguistics.

Sagot, B. 2018. A multilingual collection of CoNLL-U-compatible morphological
lexicons. In *Proceedings of the Eleventh International Conference on Language
Resources and Evaluation (LREC)*, pages 1861-1867. Miyazaki, Japan. European
Language Resources Association.

