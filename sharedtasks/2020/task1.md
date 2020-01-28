---
layout: page
longtitle: "Task 1 - SIGMORPHON 2020 Shared Task: Grapheme-to-Phoneme and Unsupervised Induction of Morphology"
title: "Task 1: Multilingual Grapheme-to-Phoneme Conversion"
---

In this task, participants will create computational models that map a sequence
of "graphemes" (characters, specfically Unicode codepoints) representing a word
in a given language to that word's pronunciation (represented as a roughly
phonemic [IPA](https://en.wikipedia.org/wiki/International_Phonetic_Alphabet)
transcription). This task is an important part of speech technologies such as
recognition and synthesis.

Data and Format
---------------

The training and development data will be provided as UTF-8-encoded
[tab-separated values](https://en.wikipedia.org/wiki/Tab-separated_values)
files. Each example occupies a single line and consists of a grapheme sequence,
a tab character, and the corresponding phone sequence. The phone sequences have
been automatically tokenzed using the [`segments`
library](https://github.com/cldf/segments). These are followed by another tab
character, then a count derived from [Wortschatz](https://wortschatz.uni-leipzig.de),
which you may choose to use as an additional feature in your system.
The following shows three lines from
the Romanian data set:

    antonim	a n t o n i m	808
    ploaie	p lʷ a j e	8675309
    pornește	p o r n e ʃ t e	1337

The test file will consist of a single column, containing grapheme sequences.
Please provide your results in the two-column (grapheme sequence, phone
sequence) format. If your system only provides the predicted phone sequences,
you can use the UNIX command-line tool `paste` to combine the columns.

The data used in this task is primarily extracted from
[Wiktionary](https://en.wiktionary.org/wiki/Wiktionary:Main_Page).

### Data conditions

There will be two data quantities for each language, a high-resource and a
low-resource setting. The low-resource setting will be restricted to 1000
training examples.
Please report test outputs for systems trained on 
each setting.

### External data

Participants are permitted to use the following types of external data:

-   Open-source pronunciation data *not derived from Wiktionary* (e.g., for
    instance, for French one may use pronunciations from
    [Lexique](http://www.lexique.org/), though note that these pronunciations
    are not in IPA)
-   Open-source pronunciation data from languages *not targeted in this
    challenge*, including those derived from Wiktionary
-   Open-source morphological analyzers
-   Word frequency distributions

*Participants may not make use of any Wiktionary data or Wiktionary-derived data for the targeted
languages.*

Evaluation
----------

Systems should predict a single phone sequence for each test example. The
primary measure will be the word error rate (WER), which is the percentage of
words for which the hypothesized transcription sequence does not match the gold
transcription. We also report phone error rate (PER), the micro-averaged edit distance
between hypotheses and gold transcriptions, computed by summing the minimum edit
distance between the hypothsis and gold transcriptions and then dividing by the
summed length of the gold transcriptions. As is common practice, we multiply
both numbers by 100.

Both metrics can be automatically computed using a provided Python script.

### Ambiguous examples

There are many reasons a word in a given language might have multiple
pronunciations. For instance, there may be inherent, or
sociolinguistically-conditioned, variation, or the word may be a homograph. We
deliberately exclude from the test data any words for which the source data
gives multiple pronunciations.

### Averaging

We will evaluate on each language separately. An aggregate evaluation will
weight all languages equally (i.e. macro-averaging), including surprise
languages released later during the development period.

### Languages

We evaluate the task on 15 languages. The ten core languages are listed below:

1. Bulgarian
1. French
1. Georgian
1. Hindi
1. Hungarian
1. Icelandic
1. Japanese (Hiragana)
1. Korean
1. Lithuanian
1. Modern Greek

The remaining five languages are "surprise languages" to be announced and
released at a late date.

Baselines
---------

We provide implementations of two baseline systems for the task:

1.  a *pair n-gram* model (Novak et al. 2016) implemented using the OpenGrm
    toolkit (Roark et al. 2012, Gorman 2016), and
2.  *a bidirectional LSTM encoder-decoder sequence model* implemented using the
    Fairseq toolkit (Ott et al. 2019).

Participants are welcome to adapt these baselines for their purposes.

Overview Paper
--------------

In an overview paper for the shared task, we will compare the performance of
submitted systems in detail. We will assess:

-   which systems are significantly different in performance
-   which languages were challenging and which types of systems succeeded on
    them, and
-   which systems would provide complementary benefit in an ensemble system.

Included in the paper will be a summary of scores. Participants who produce
outputs for all languages will be ranked; others may still have their systems
described in the overview paper.

References
----------

Gorman, K. (2016). Pynini: a Python library for weighted finite-state grammar
compilation. In *Proceedings of the SIGFSM Workshop on Statistical NLP and
Weighted Automata*, pages 75–80, Berlin. Association for Computational
Linguistics.

Novak, J. R., Minematsu, N., and Hirose, K. (2016). Phonetisaurus: exploring
grapheme-to-phoneme conversion with joint n-gram models in the WFST framework.
*Natural Language Engineering*, 22(6):907–938.

Ott, M., Edunov, S., Baevski, A., Fan, A., Gross, S., Ng, N., Grangier, D., and
Auli, M. (2019). fairseq: a fast, extensible toolkit for sequence modeling. In
*Proceedings of the 2019 Conference of the North American Chapter of the
Association for Computational Linguistics (Demonstrations)*, pages 48–53,
Minneapolis. Association for Computational Linguistics.

Roark, B., Sproat, R., Allauzen, C., Riley, M., Sorensen, J., and Tai, T.
(2012). The OpenGrm open-source finite-state grammar software libraries. In
*Proceedings of the ACL 2012 System Demonstrations*, pages 61–66, Jeju Island,
Korea. Association for Computational Linguistics.
