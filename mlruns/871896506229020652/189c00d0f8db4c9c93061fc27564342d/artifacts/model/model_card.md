
# m3_hierarchical_ner_ref_cmbert_iob2

## Introduction

This model is a fine-tuned verion from [Jean-Baptiste/camembert-ner](https://huggingface.co/Jean-Baptiste/camembert-ner) for **nested NER task** on a nested NER Paris trade directories dataset.

## Dataset

Abbreviation|Entity group (level)|Description
-|-|-
O |1 & 2|Outside of a named entity
PER |1|Person or company name
ACT |1 & 2|Person or company professional activity
TITREH |2|Military or civil distinction
DESC |1|Entry full description
TITREP |2|Professionnal reward
SPAT |1|Address
LOC |2|Street name
CARDINAL |2|Street number
FT |2|Geographical feature

## Experiment parameter

* Pretrained-model : [Jean-Baptiste/camembert-ner](https://huggingface.co/Jean-Baptiste/camembert-ner)
* Dataset : ground-truth
* Tagging format : IOB2
* Recognised entities : 'All'

## Load model from the Hugging Face

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification

tokenizer = AutoTokenizer.from_pretrained("nlpso/m3_hierarchical_ner_ref_cmbert_iob2")
model = AutoModelForTokenClassification.from_pretrained("nlpso/m3_hierarchical_ner_ref_cmbert_iob2")


