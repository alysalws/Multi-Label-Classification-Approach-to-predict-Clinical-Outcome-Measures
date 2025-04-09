**Data Cleaning and Transformation**

The following steps were conducted to clean and transform the dataset to ensure it is realiable and meaningful for model training.

1. Remove clinical trials that are only eligible for participants aged 16 or above were removed.
2. Remove trials with missing Gender, Minimum Age eligibility and Maximum Age eligibility were disregarded. 
3. Remove duplicated columns.
4. Standardize the formats in Dates and Age eligibility fields.
5. Remove contiguous sequences of characters, excess white spaces, paragraph numbers, new line characters, apostrophes and special characters in entries.
6. Remove study records with a study duration of less than or equal to 0 days were removed from the dataset.

Then, new columns were added to the dataset in the form of binary or numerical columns by drawing information from other columns. This includes:

1. The start year of the clinical trial and total study duration.
2. The type of intervention (e.g. procedural, behavioural, drug)
3. The use of placebo
4. The number of countries where the clinical trial is conducted
5. The number of sites where the clinical trial is conducted
6. The number of study arms to the dataset

Lastly, Natural Language Processing (NLP) techniques and human judgement were applied to categorize and extract information from the Free Text columns.

1. Split the  sentences in Free Text columns (i.e. tokenized in NLP terminology) into individual words or words consisting hyphens or forward slashes (e.g. ‘10 gram/day’, ‘cancer’, ‘rating-scale’).
2. USe SpaCy’s pipeline package namely ‘en_core_sci_lg’ to disambiguate the abbreviations and acronyms of medical terms.
3. Replace synonyms and words that convey similar meanings in Free Text columns with one standard wording.
4. Assign clinical terms with the same parent category into the same group. 

A 3,823 records and 230 columns remained in the dataset for Exploratory Data Analysis after the data is cleaned and transformed. 

**Key Insights from Exploratory Data Analysis & Implication for Methodology**

There are three key takeaways from Exploratory Data Analysis. First, the number of clinical trials using Questionnaire is almost three times of that using Patient Diary, and the number of clinical trials using 1 measure significantly exceeds that using 2 measures. An imbalanced dataset is an issue for MLC, because it will affect the model’s ability to effectively learn the decision boundary, resulting in poor predictions for the minority class in the testing dataset. This suggests the need to adjust the weight parameters in MLC models to avoid biased predictions towards the majority class,

Second, the average number of participants in IPCT equals 451 but only 17% of which recruited more than this number. Similarly, the average study duration of IPCT equals 883 days but only 39% of which had a duration longer than this. This suggests that the dataset is highly left skewed and outlier examination and Box-cox transformation is required to fix the nonnormality of the dataset before fitting it to the models. 

Third, the adoption of outcome measures seems to be much lower in China than in other countries, suggesting an association between outcome measures and the type of country (developing or developed) in which clinical trials were conducted. Also, the adoption of outcome measures seems to be more common in clinical trials that have a minimum age eligibility of 12 years old or above, implying clinical trials recruiting teenagers as participants may be more likely to use these measures. These findings provide good implications for feature selection in the subsequent research methodology section.

