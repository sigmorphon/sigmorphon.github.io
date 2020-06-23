---
layout: page
title: "Invited Speakers"
---

(Displayed in a random order every time)

- [**Robert Malouf (San Diego State University)**][malouf]  
  **Title:**  Inflectional data science and human/computer-aided linguistic analysis
  **Abstract:** 
  Recent work in paradigm learning, e.g., as part of the SIGMORPHON shared tasks, has yielded impressive results. Seq2seq models in particular have been shown to capture complex sequential patterns across a range of linguistic phenomena. However, despite these advances, finite-state methods still (arguably) remain the best way of producing high-quality morphological processors for individual languages. And, while there have been notable attempts to extract linguistic generalizations from black-box models, the results do not yet approach as  good a linguistic analysis as those produced using standard descriptive techniques. 
 
Machine learning techniques for inflectional morphology, unlike (again, arguably) other aspects of language, have not yet made older methods obsolete. But, there is no good reason to think of these two general approaches as mutually exclusive. Seq2seq models and human analysts have complementary strengths and weaknesses. In this talk, I will discuss prospects for a combined approach to, depending on the perspective, either human-aided or computer-aided morphological modeling. In particular, I will focus on the use of machine learning techniques for the analysis of Estonian (Finnic) and Nandi (Nilotic), two languages with very complex inflectional systems. Machine learning can play a crucial role in gathering and validating raw data, generating and testing hypotheses, and detecting outliers. These methods are most useful for finding and testing statistical tendencies, i.e. patterns which are not consistent enough to qualify as a rule in the linguistic sense, yet that are still important parts of the morphological system. Finally, I would like to propose a closer collaboration between computational modelers and working linguists that might lead to the development of more specific tools to improve linguistic analyses.

Robert Malouf is a professor of linguistics at San Diego State University.  His main area of research lies in the intersection between morphological theory and computational modeling. 

- [**Bruce Hayes (UCLA)**][hayes]
  **Title:**   
  **Abstract:**
In recent years computational linguists have effectively addressed the problem of “paradigm completion”:  one trains a model on morphological paradigms (often including phonological alternations) and tests it on the ability to generate held-out forms correctly. This problem has more than once been the basis of a Shared Task at ACL, and the successive Tasks have addressed increasing amounts of language data and yielded ever more sophisticated and accurate solutions.
 
Here, I describe a research question that arises in this sort of work, one that has probably attracted less attention thus far: human learners sometimes fail to apprehend the correct pattern of their language’s paradigms. This results, sometimes, in mere personal idiosyncrasy, but sometimes in wholesale community adoption and hence language change. I will give a series of empirical examples, and also suggest, following the phonological literature, mechanisms whereby models can succeed at explaining failure of morphological learning. Lastly I mention scientific and indeed practical reasons to study these learning failures.

Bruce Hayes is the Biggs Distinguished Professor of Linguistics at UCLA. He has worked extensively on the paradigm completion problem using three approaches: phonological and morphological theory, experiments, and computational modeling. 
  
- [**Clara Vania (University of New York)**][vania]  
  **Title:** On Understanding Character-level Models for Representing Morphology
  **Abstract:** Morphology allows humans to create, memorize, and understand words in their language. To process and understand human languages, we expect our computational models to also learn morphology. Recent advances in neural network models provide us with models that compose word representations from smaller units like word segments, character n-grams, or characters. These so-called subword unit models do not explicitly model morphology yet they achieve impressive performance across many multilingual NLP tasks, especially on languages with complex morphological processes. They raise a provocative question: Does NLP benefit from models of morphology, or can they be replaced entirely by models of characters? In this talk, I will discuss our work aimed to shed light on this question, with focus on the interaction between character-level neural models, morphology, and language typology. We systematically compare various subword unit models and study their performance across language typologies. We show that models based on characters are particularly effective because they learn orthographic regularities which are consistent with form-function mapping of morphology. To understand which aspects of morphology are not captured by these models, we compare them with an oracle with access to explicit morphological analysis. We show that in the case of dependency parsing, character-level models are still poor in representing words with ambiguous analyses, and demonstrate how explicit modeling of morphology is helpful in such cases. Finally, I will conclude by discussing the implications of our studies for future work in multilingual NLP.
  
  Clara Vania is a postdoctoral researcher at the Center of Data Science, New York University. She obtained her PhD in 2019 from the University of Edinburgh, where she worked with Adam Lopez. Her research interests lie in the area of natural language processing and machine learning. In particular, she is interested in applying machine learning techniques and exploring rich linguistic resources for multilingual NLP. She is also interested in topics related to syntax, representation learning, transfer learning, multilingual, and low-resource NLP.
  
- [**Jane Chandlee (Haverford College)**][chandlee]  
  **Title:** Recursive Schemes for Phonological Analysis  
  **Abstract:** A central goal of generative linguistics is to determine abstract universals that govern the shape and structure of language (Chomsky, 1957; Baker, 2009). An abstract computational universal of natural language phonology is that it is regular (Johnson, 1972; Kaplan and Kay, 1981, 1994). Recent work has pursued stronger computational universals for phonology by positing further constraints on the nature of this memory (Heinz, 2009; Heinz and Lai, 2013; Chandlee and Heinz, 2018, a.o.). However, a criticism of a perspective that focuses on computational universals is that it does not allow for a theory that intensionally represents phonological generalizations in the way phonologists recognize them.

In this talk, present a computational formalism that retains the important discoveries about the computational restrictiveness of phonology but in a way that better aligns with commonly-held assumptions about phonological representations and grammars. Specifically, we introduce Boolean Monadic Recursive Schemes (BMRSs) and demonstrate their utility for phonological analysis. This formalism has a well-understood complexity bound that corresponds to previous results in the study of computational phonology, but it also provides a way to implement phonological substance. BMRSs are based on the well-studied concept of recursive program schemes, which are an abstract way of studying the complexity of algorithms (Moschovakis, 2019). Implementing a simple ‘if...then...else’ structure over properties of elements in phonological representations, BMRSs maintain one of the main strengths of OT in implementing a ranking of constraint-like predicates that identify particular structures in either the input or output. In contrast to OT, however, the evaluation of a BMRS hierarchy is necessarily local in nature, and therefore avoids the computational over-generation that has been attributed to OT’s global evaluation strategy (Frank and Satta, 1998; Gerdemann and Hulden, 2012; Lamont, 2018). In the talk we illustrate these advantages of BMRSs through two notable phonological case studies: the typology of *NC and Elsewhere Condition effects.

Jane Chandlee is an Assistant Professor in the Department of Linguistics at Haverford College, outside Philadelphia. She completed her PhD at the University of Delaware in 2014. Her work investigates the computational properties of phonological processes, with an emphasis on subregularity and phonological learning.

<script type="text/javascript">
var ul = document.querySelector('ul');
for (var i = ul.children.length; i >= 0; i--) {
    ul.appendChild(ul.children[Math.random() * i | 0]);
}
</script>

[malouf]: http://malouf.sdsu.edu
[hayes]: https://linguistics.ucla.edu/people/hayes/
[vania]: https://claravania.github.io/
[chandlee]: https://chandlee.sites.haverford.edu/
