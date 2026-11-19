## SIGTYP Shared Task on Morph Segmentation and Root Identification Across Typologically Diverse Languages

In 2027, <font color="red">S</font>IG<font color="red">T</font>YP is hosting a **Shared Task on Morph Segmentation and Root Identification Across Typologically Diverse Languages.** Morphological segmentation, the process of decomposing words into minimal meaningful units, is a long-standing problem in computational linguistics.  


## Table of Contents

1. [Important Dates](#important-dates)
2. [Linguistic Background](#task-description)
3. [Data Download](#data-download)
4. [Evaluation Metrics](#evaluation-metrics)
5. [Baselines](#baselines)
6. [Registration](#registration)
7. [CodaBench Submission Instructions](#codabench-submission-instructions)
8. [Submission of System Description Papers](#submission-of-system-description-papers)
9. [Task Organisers](#task-organisers)
10. [Acknowledgments](#acknowledgments)


## 1. Important Dates

The shared task timeline is organized as follows:

* **Registration opens:** November 21, 2026
* **Development phase begins:** January 15, 2027
  + Training and development data released
  + Baselines released
  + Evaluation script released
  + CodaBench development phase opens
* **Evaluation phase begins:** February 15, 2027
  + (Unannotated) evaluation data released
  + CodaBench evaluation phase opens
* **Evaluation phase ends:** March 1, 2027
  + CodaBench evaluation phase closes
* **System description paper submission deadline:** March 15, 2027
* **Notification of paper acceptance:** March 22, 2027
* **Camera-ready:** March 29, 2027
* **SIGTYP Workshop:** May 13


**Important Links** <br>

[**Shared Task Page**](https://sigtyp.github.io/st2027-lingseg.html)<br>

## 2. Task Description

For each language, the participants will be given list of word forms to be segmented.
Then, given a word form in its sentential context, participating systems are expected to 

1. segment it into surface morphs, i.e., the overt realizations of minimal meaningful units, and 
2. identify the root morph(s) among the resulting segments.

A root is understood as the morph carrying the primary lexical meaning of a word. While most word forms contain one or more roots, certain mono-morphemic function words, particularly primary prepositions and conjunctions, are considered rootless. By contrast, pronouns and articles are assigned a root and may also be morphologically complex. Whenever a word form contains multiple roots, all of them must be identified.

The task follows two central principles. First, it adopts a surface-based approach: the identified morphs must concatenate to reconstruct the original word form, rather than being represented through abstract or canonical morphological forms. Second, it requires maximum (exhaustive) segmentation: systems are expected to identify all constituent morphs, rather than merely separating a stem from an inflectional ending or identifying only the most recently added derivational affix. The aim is thus to capture the complete morphological structure of each word form as it is realized on the surface.

Each word form is accompanied by its sentence context and, where available, morphological features encoded according to the Universal Dependencies (UD) feature schema. The contextual information is intended to help systems resolve ambiguities that cannot be reliably addressed when word forms are considered in isolation, including homonymous forms that may have different morphological analyses.

The expected output consists of a segmentation of each word form and the identification of its root morph(s). The annotation format uses the plus sign (+) to indicate boundaries between morphs and the hash sign (#) to mark the beginning of a root morph. A special boundary marker ($) is used when a morphological boundary falls within a single grapheme, as may occur in syllabic and abugida writing systems.

All word forms are represented in lowercase in the annotation, including proper nouns, abbreviations, and other forms conventionally written with an initial capital letter. No additional white spaces are inserted around morph boundaries. However, word forms in some languages may themselves contain white spaces; in such cases, the plus sign marking a morph boundary is placed immediately after the existing white space.

The following examples illustrate the expected annotation:


<pre>
Word form          Annotation                 Language 
------------------------------------------------------
talked             #talk+ed                   English 
including          in+#clud+ing               English 
to                 to                         English 
Jahresabschlüsse   #jahr+es+ab+#schlüss+e     German 
твоей              #т+вое$й                   Russian
देखो                #देखो$                       Hindi 
助け               #助け$                      Japanese 
đàn ông           #đàn +#ông                  Vietnamese
</pre>

For languages with non-concatenative morphology, the annotation is based on IPA transcriptions. Discontinuous parts of a morpheme are enclosed in brackets to indicate that they belong together. Different bracket types are assigned in order of their first occurrence in the word: () for the first discontinuous morph, [] for the second, {} for the third, and <> for the fourth; see the following example:

<pre>
Word form       IPA transcription      Annotation                Language 
...           ʔal(#dʒ)anaː(ħ)i         ʔal+(#dʒ)[a](n)[aː](ħ)+i   Arabic
</pre>

Further details on morph segmentation and root identification are provided in the annotation guidelines used to prepare the development and evaluation data: [MŠ: SHOULD WE DISPLAY THEM ON THE PROJECT’S WEBSITE?]






## 3. Data Download

## 4. Evaluation Metrics

Each system participating in the shared task will be evaluated using a primary metric and several secondary metrics.

The primary evaluation metric upon which the CodaBench leaderboard will be based will be F1-score of joint segmentation and classification of morphs. For a morph to be considered a true positive, its span within the segmented word must be retrieved correctly, and it must be classified correctly as a root or non-root. If a morph boundary is inside a grapheme, the $ delimiter must be used directly after the grapheme in question. If the morph is discontinuous and uses brackets to mark its separated parts, these must be correctly applied.

Secondary evaluations will also be available, probably including morph-level F1 without root vs. non-root classification, boundary-level F1 (based on the correct placement of token boundaries), edit-distance of the recovered morph sequence and the ground truth, and character-level cluster-based metrics such as Dice coefficient.

A Python script will be provided for the evaluation (to appear here in mid January 2027).


## 5. Baselines

In mid January 2027, we will release two baseline systems and their results. The first baseline will consist of a fine-tuned encoder-decoder sequence-to-sequence model as in Ginn et al. (2026). The second baseline will consist of zero/few-shot prompting using a decoder-only large language model as in John and Žabokrtský (2026). Both baselines will be implemented monolingually (one instance per language). A more detailed description will be released alongside the final models.

References:

* Michael Ginn, Lindia Tjuatja, Enora Rice, Ali Marashian, Maria Valentini, Jasmine Xu, Graham Neubig, and Alexis Palmer. 2026. Massively multi-lingual joint segmentation and glossing. In Proceed-ings of the 64th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 35806–35820, San Diego, California, United States. Association for Computational Linguistics
* Vojtěch John and Zdeněk Žabokrtský. 2026. LLMs as linguistic experts: The case of morphological segmentation. In International Conference on Text, Speech, and Dialogue, pages 93–104. Springer.


## 6. Registration

[**Registration**](https://docs.google.com/forms/d/e/1FAIpQLSdHc1G7ttdoITBjntyM13b2I7ASr9BRnavjIBvcLmdErFYSRw/viewform?usp=dialog)

## 7. CodaBench Submission Instructions

## 8. Submission of System Description Papers

<p align="justify"> Participants will be invited to describe their system in a paper for the WILDRE7 workshop proceedings. The task organisers will write an overview paper describing the task, summarising the approaches taken, and analyse their results.

Paper submission instructions will be the same as for the [workshop](https://sigtyp.github.io/workshop.html). Each team participating in the shared task is expected to submit a system description paper of 4 to 5 pages, plus additional pages for references, formatted according to the workshop guidelines. The paper should describe the system and the resources used along with the libraries. The methodology/strategy should be documented in such a way that the readers and other researchers are able to replicate the work from the system description in the paper. </p>

## 9. Task Organisers
* **Magda Ševčíková**, Charles University<br/>
* **Zdeněk Žabokrtský**, Charles University<br/>
* **Priya Rani**, Charles University<br/>
* **Andrew Dryer**, Charles University<br/>
* **Hana Hledíková**, Charles University<br/>
* **Vojtěch John**, Charles University<br/>
* **Anja Nedoluzhko**, Charles University<br/>
* **Aleš Papáček**, Charles University<br/>
* **Enora Rice**, University of Colorado<br/>

## 10. Acknowledgments

This shared task is supported by the CrossLing project, Cross-Linguistic Analysis of the Internal Structure of Words, LL2615, funded by the Ministry of Education, Youth and Sports of the Czech Republic.

<!-- TODO: ack here also the crossling as well as authors of datasets integrated in UniSegments -->

