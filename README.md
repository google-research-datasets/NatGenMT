---
# Gender Issues in Machine Translation
Evaluation benchmark for gender issues in MT
---


## Dataset Description
- **Paper:** [Automatically Identifying Gender Issues in Machine Translation using Perturbations](https://www.aclweb.org/anthology/2020.findings-emnlp.180.pdf)
- **Point of Contact:** [Hila Gonen](mailto:hilagnn@gmail.com), [Kellie Webster](websterk@google.com)

### Dataset and Task Summary
This dataset is intended as an evaluation benchmark for gender issues in Machine Translation.
We consider the challenges in modeling and handling gendered language in the context of machine translation and extend over previous work that identifies issues using synthetic examples. We focus on the class of issues which surface when a neutral reference to a person is translated to a gendered form. For this class of examples, the MT task requires a system to produce a single translation without source cues, thus exposing a model's preferred gender for the reference form.
We include English source sentences, and four target gendered languages across three language families (French, German, Spanish, and Russian).
The examples included in the dataset expose where MT encodings are gendered, finding new issues not covered in previous manual approaches.

### Overview of Dataset Creation

The dataset is automatically curated using the following pipeline:
1. We keep only gender-neutral sentences with a single human entity, the rest are filtered out.
2. We create perturbations on the human entity in the source sentence, to form pairs of original/perturbed sentences.
3. We translate all pairs to the target language and surface pairs in which the gender of the human entity differs between the original and the perturbed sentence.
4. Human annotators verify the surfaced pairs ("at risk" pairs).
5. Random ("not at risk") pairs are added to the dataset.

### Languages
Source language: English.

Target languages: French, German, Spanish, and Russian.

## Meta Information

### Dataset Curators
[Hila Gonen](mailto:hilagnn@gmail.com), [Kellie Webster](websterk@google.com)

### Licensing Information
We release this dataset under the Apache Version 2.0 license. Refer to LICENSE
for details.

### Citation Information
```
@inproceedings{gonen-webster-2020-automatically,
               title = "Automatically Identifying Gender Issues in Machine Translation using Perturbations",
               author = "Gonen, Hila and Webster, Kellie",
               booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2020",
               year = "2020",}
```

## Dataset Structure

### Data Instances
The dataset consists of pairs of English sentences that differ in a single word (the human entity), and their translation to a gendered language (either French, German, Spanish or Russian).

### Data Fields
Each example consists of two six-line entries. Each six-line entry is separated
by a single blank line; examples are separated by two blank lines. Where the
first line is `Original sentences:`, the sentence is unchanged from the
underlying data; `Substitution sentences:` indicates that a word has been
perturbed.

```
"Original sentences:" or "Substitution sentences:"
a sentence, in English (source).
the sentence, in the target language.
a word from the English sentence.
the word, in the target language.
the grammatical gender of the word in the target language, fem or masc.
```

### Data Statistics

Statistics of the dataset per target language:

French: 100 "at risk" pairs, 100 "not at risk" pairs

German: 100 "at risk" pairs, 100 "not at risk" pairs

Spanish: 100 "at risk" pairs, 100 "not at risk" pairs

Russian: 59 "at risk" pairs, 100 "not at risk" pairs


## Dataset Creation

### Curation Rationale
This dataset is automatically curated, with a human verification step that follows the automatic process. The class of issues we are interested in are those where translation to a gender-marking language exposes a model's gender preference for a personal reference.

### Communicative Goal
By publicly releasing our dataset, we hope to enable the community to work together towards solutions that are inclusive and equitable to all.

### Source Data

#### Initial Data Collection and Normalization
Sentences with no human entities or more than a single human entity are filtered out. Sentences that are not gender-neutral are also filtered out.

#### Who are the source language producers?
All sentences are taken from the subreddit "career". The perturbations to the entity are done using BERT.


### Annotations

#### Annotation process
There is no human annotation step, only a human verification step, where speakers of both source and target languages verify that "at risk" sentence pairs exhibit problematic behavior upon translation.

#### Who are the annotators?
For each target language, the verifier was a speaker of both English and the target language.


## Considerations for Using the Data

### Social Impact of the Dataset
The main goal of this dataset is to promote fairness in machine translation, by providing an evaluation benchmark to this end.
We focus specifically on gender bias.

### Other Known Limitations
1. The scale of the dataset is relatively small.
2. The chosen sentences depend on the underlying translation model used for translation. In our case - Google Translate.
