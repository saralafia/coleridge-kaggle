# Coleridge-Kaggle
Code for a [Kaggle competition](https://www.kaggle.com/c/coleridgeinitiative-show-us-the-data/data) to detect data references in academic publications

## /data
### Files:
* **test** - full text of the test set's publications in JSON format, broken into sections with section titles
* **train** - full text of the training set's publications in JSON format, broken into sections with section titles
* **sample_submission.csv** - a sample submission file in the correct format
* **train.csv** - labels and metadata for the training set

### Columns:
* **id** - publication id - there are multiple rows for some documents, indicating multiple mentioned datasets
* **pub_title** - title of the publication - a small number of publications have the same title
* **dataset_title** - the canonical title of the dataset mentioned in the publication
* **dataset_label** - the span of text that indicates the dataset - it's sometime identical to dataset title
* **cleaned_label** - the dataset_label passed through the `clean_text` function defined by the competition

## /notebooks
* **baseline-classifiers** - Pipeline for predicting classes of dataset references
* **citation-embeddings** - Exploring BERT and sciBERT to predict data citations in classification and embedding tasks
* **data-exploration** - Understanding the structure of data and publications provided by competition (section titles, indicator terms)
* **feature-engineering** - Analyzing publication sections and sentences to learn which features can predict data citations
* **get-data** - Querying CKAN API to build a list of all dataset titles from Data.gov (n=267,726) to supplement dataset titles
* **icpsr-demo** - Apply NER model to predict `dataset` entities from ICPSR bibliography full text
* **prep-sentences** - Preparing training data by extracting features (indicator term frequency, section, acronyms, labels)
* **train-classifier** - Build and save a classifier to discriminate true citation sentences (target - binary) given a set of input features
* **v1-string-matching** - First attempt solution for matching and formatting strings from publication text with dataset labels (Score: 0.47)
* **v2-refined-matching** - Second attempt solution for smarter string matching with more labels (Score: 0.48)
* **v3-classifier-NER** - Third attempt solution with RF classifier and NER models (Score: unscored - notebook timeout on Kaggle)

## /results
* **submission.csv** - latest version of submission file generated for the competition - prior submissions versioned in [Kaggle](https://www.kaggle.com/c/coleridgeinitiative-show-us-the-data/code?competitionId=25925&sortBy=dateRun&tab=profile)

### Workflow:
* **prep-sentences**
* **train-classifier**
* **v3-classifier-NER** 
