---
layout: page
title: "CoNLL–SIGMORPHON 2017 Shared Task: Universal Morphological Reinflection"
breadcrumb: 2017
---

- [Task](task)
- [Registration](https://docs.google.com/forms/d/1cJ9c0o8WfZCBU4QWGiWYnLoKIedjlZWlVGXob-MH4c4/closedform)
- [Important dates](dates)
- [Organizers](organizers)

## News

* 06/27/2017: Test data answers released for both tasks!
* 05/20/2017: Test data released for both tasks!
* 05/19/2017: System description paper details posted (due on June 3!)
* 05/10/2017: Surprise data are released for 12 additional languages! See [here](https://github.com/sigmorphon/conll2017/tree/master/all).
* 05/10/2017: Example evaluation on sample baseline output lives [here](https://github.com/sigmorphon/conll2017/tree/master/evaluation).
* 03/03/2017: [Baseline system released](https://github.com/sigmorphon/conll2017/tree/master/baseline).
* 03/01/2017: Training and development data released for 40 languages, available here! We reserve the right to make minor corrections to the data until April 15. Please report any clear errors before then.
* 02/24/2017: Pilot data released, available [here](https://github.com/sigmorphon/conll2017/tree/master/pilotdata).

## Overview
A word's form reflects syntactic and semantic features that are expressed by the word. For example, each English count noun has both singular and plural forms (robot/robots, process/processes), known as the **inflected forms** of the noun. A Polish verb can have [nearly 100 inflected forms](http://www.tastingpoland.com/language/verb/dodac_add_verb.html).

NLP systems must be able to analyze and generate all of these inflected forms. Fortunately, inflected forms tend to be systematically related to one another. This is why English speakers can usually predict the singular form from the plural and vice-versa, even for words they have never seen before.

We are hosting a shared task on **universal morphological reinflection**. That is, the shared task of morphological reinflection will be conducted in **40+ languages of the world**. An example of English reinflection is the conversion of `ran` to its present participle, `running`. To participate in the shared task, you will build a system that can learn to solve reinflection problems. All submitted systems will be compared on a held-out test set.

## Contact
conll-sigmorphon-2017@googlegroups.com
