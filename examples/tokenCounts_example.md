# Token Counts
![Token Counts](https://github.com/miielab/TokenCounts/workflows/Token%20Counts/badge.svg)


## Example (NER Only)
1. To run *just* NER, create an `input.yaml` file in the `src/` and copy the following. Make the necessary edits.
```
---
data_dir: ENTER_YOUR_DATA_DIR_PATH

ner:
  method_name: spacy #currently the only accepted NER method in our pipeline
  spacy_dataset: en_core_web_lg #the NER pipeline used to run NER (can be en_core_web_sm, en_core_web_lg or en_core_web_trf)
  filter_entities: [PERSON] #what types of spacy entities you would like to extract specifically (default 
  output_dir: ENTER_YOUR_OUTPUT_DIR_PATH #where you would like your results stored
...

```
2. Run the NER pipeline with your customizations:
    - `python src/main.py -i /path/to/input/yaml`

## Example (Specific Word Counts Only)
1. To run *just* specific word counts, create an `input.yaml` file in the `src/` and copy the following. Make the necessary edits.
```
---
data_dir: ENTER_YOUR_DATA_DIR_PATH

specific_words:
  categorize_file: supplemental_data/Categories #list of specific words you are interested in
  spacy_dataset: en_core_web_sm #change this if you need a more accurate NER method
  subcats: [female, male, ...] #change this depending on what categories you want incorporated
  type: LU #whether you want to count the lower AND uppercase versions of the text (LU), just the lowercase versions (L) or just the uppercase versions (U)
  output_dir: ENTER_YOUR_OUTPUT_DIR_PATH #where you would like your results stored
...
```
Note: the [Categories](https://github.com/miielab/Categories) GitHub repository contains all potential specific words we are interested in for our analysis in particular. You may create your own categories that are interesting to you, or go off of the categories we already created. 

2. Run the specific words pipeline with your customizations:
    - `python src/main.py -i /path/to/input/yaml`


## Example (Both NER + Specific Word Counts)
1. To run both specific words and NER in one go, simply combine the fields in the specific word count section with the fields in the NER section into one large input.yaml file and then run `python src/main.py -i /path/to/input/yaml`

```
---
data_dir: ENTER_YOUR_DATA_DIR_PATH

ner:
  method_name: spacy 
  spacy_dataset: en_core_web_lg 
  filter_entities: [PERSON] 
  output_dir: /path/to/output_dir/

specific_words:
  categorize_file: /path/to/Categories/ 
  spacy_dataset: en_core_web_lg 
  subcats: [female, female_pronouns_combined, female_pronouns_upper, gendered, male, male_pronouns_combined, male_pronouns_lower, male_pronouns_upper, nationalities, old_female, old_male, plural_female, plural_male, red, singular_female, singular_male, white, young_female, young_male] 
  type: LU 
  output_dir: /path/to/output_dir/
...
````
