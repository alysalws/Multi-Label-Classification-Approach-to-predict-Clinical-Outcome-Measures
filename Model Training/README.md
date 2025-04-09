**Feature Engineering**

Riding on the findings from Exploratory Data Analysis, the features in the dataset were further consolidated. First, the number of categories in <Age (min) years> are collapsed from fifteen groups to two groups. Studies with a minimum age eligibility of 11 years old or below are grouped into ‘infant studies’, and ‘teenager studies’ if otherwise. Second, instead of creating dummy variables for each country, the association between the country and the outcome measures is factored in by creating two binary variables to identify whether the clinical trial takes place in developed and developing countries. The list of developed and developing countries is retrieved from the report prepared by the United Nations Development Programme (2021), which has ranked each country based on its corresponding Human Development Index (HDI). Country with an HDI higher than 0.8 is classified as a Developed Country by the United Nations.

Next, the extreme outliers in the dataset were identified and analysed. The analysis found that skewed dataset was due to the presence of certain clinical trials that recruited an extremely high number of participants (10 to 70 thousand). These trials studied very different diseases, took place in different locations, and were sponsored by different pharmaceutical companies. Therefore, considering the lack of commonalities between the outliers and the sufficient entries in the dataset, the values beyond the 99th quantile of the number of participants were removed, leaving 3,784 entries for analysis.

Below table summarizes the key figures before and after the removal of outliers:
![image](https://github.com/user-attachments/assets/3e22dc8f-570e-49a9-a814-a8f924be8e0b)

Subsequently, the dataset was split into training data and testing data in the ratio of 7:3 using MultilabelStratifiedShuffleSplit with 10 cross-validation folds. The purpose of splitting the dataset is to avoid the model from overfitting the training data such that it can generalize well to unseen data in the testing data. 

MultilabelStratifiedShuffleSplit was considered to be a better method than scikit-learn’s Train-Test-Split because the former ensures every label has the same proportion of observations within the categorical variables across the splits on imbalanced datasets.

To prevent data leakage from the training data into the testing data during the model learning phase, the testing data was scaled, imputed, normalized and encoded according to the distribution of the training data.

After feature engineering, a total of 62 columns (Features: 60, output labels: 2) and 3,784 entries remained in the dataset (training set: 2,649, testing set: 1,135).
