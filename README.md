# Multi-Label-Classification-Approach-to-predict-Clinical-Outcome-Measures

## 1. Project Background and Objectives

Clinical trials are studies intended to evaluate the efficacy and safety of new medical treatments or interventions (such as vaccines, dietary supplements, drugs, devices, and lifestyle modifications) on humans. Clinical trials used to be only conducted in-person at designated sites such as hospitals. However during the outbreak of Covid-19 pandemic in 2021, the US Food and Drug Administration (FDA) issued guidelines on how Sponsors could run clinical trials when participants could not physically attend protocol-specified visits, with suggestions including running trials remotely over the internet and collecting clinical outcomes using digital tools. These suggestions opened doors for Sponsors and Contract Research Organizations to reassess their conventional approach of running clinical trials.

This project uses a Multi Label Classification Model to investigate whether clinical trials with certain characteristics are more likely to adopt digital tools such as e-Questionnaire and e-Patient Diary to collect clinical outcome from paedaetrics. More than 10 years of industry-sponsored interventional paediatric clinical trial records were retrieved from ClinicalTrials.gov database and studied. A total of 27 MLC algorithms were implemented, and their performances were evaluated against example-based and label-based metrics.

## 2. Source of the dataset

The primary data used in this research is the clinical trial protocol information collected from [ClinicalTrials.gov,](https://clinicaltrials.gov/), a publicly accessible global registry maintained by the U.S. National Library of Medicine. This registry contains more than 420 thousand clinical trial records documented since Year 2000. It is selected out of 17 other global registries primarily because it is the oldest and largest one. Also, this registry offers a RESTful Application Programming Interface (API) that provides convenient access to protocol information from computer programs. 

A total of 7979 records and 84 columns were retrieved from the API. The records were converted into a table format that is supported by Jupyter Notebook for further processing in Python language.

## 3. Data Cleaning

1. Remove clinical trials that are only eligible for participants aged 16 or above were removed.
2. Remove trials with missing Gender, Minimum Age eligibility and Maximum Age eligibility were disregarded. T
3. Remove duplicated columns
4. Standardize the formats in Dates and Age eligibility fields
5. Remove contiguous sequences of characters, excess white spaces, paragraph numbers, new line characters, apostrophes and special characters in entries.
6. Remove study records with a study duration of less than or equal to 0 days were removed from the dataset.

## 4. Data Enrichment

This section creates new columns to enrich the dataset based on the information drawn from the structured columns. This includes:
1. Flagging the start year of the clinical trial and its study duration, based on the difference between the start date and the completion date. In case the study completion date is not provided, it is assumed to equal the primary study completion date (i.e. the day when the collection of primary outcomes is completed).
2. Adding the type of intervention (e.g. procedural, behavioural, drug), the use of placebo, the number of countries, the number of clinical trial sites, and the number of study arms to the dataset in the form of binary or numerical columns.
3. Using NLP techniques and human judgement to clean, categorize and extract information from 11 Free Text columns.  To commence with, the sentences in Free Text columns were split (i.e. tokenized in NLP terminology) into individual words or words consisting hyphens or forward slashes (e.g. ‘10 gram/day’, ‘cancer’, ‘rating-scale’). Then, the spaCy’s pipeline package namely ‘en_core_sci_lg’ which is trained on a large corpus of biomedical vocabularies was used to disambiguate the abbreviations and acronyms of medical terms. Subsequently, Categorization and Keyword Extraction were carried out. For both parts, Python functionalities were first used to replace the synonyms and words that convey similar meanings in Free Text columns with one standard wording. Then, information was mined using exact keyword match, and clinical terms that share the same parent category were grouped for aggregate analysis. 

