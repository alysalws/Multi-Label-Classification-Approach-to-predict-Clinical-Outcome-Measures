### Feature Engineering

Riding on the findings from Exploratory Data Analysis, the features in the dataset were further consolidated. First, the number of categories in <Age (min) years> are collapsed from fifteen groups to two groups. Studies with a minimum age eligibility of 11 years old or below are grouped into ‘infant studies’, and ‘teenager studies’ if otherwise. Second, instead of creating dummy variables for each country, the association between the country and the outcome measures is factored in by creating two binary variables to identify whether the clinical trial takes place in developed and developing countries. The list of developed and developing countries is retrieved from the report prepared by the United Nations Development Programme (2021), which has ranked each country based on its corresponding Human Development Index (HDI). Country with an HDI higher than 0.8 is classified as a Developed Country by the United Nations.

Next, the extreme outliers in the dataset were identified and analysed. The analysis found that skewed dataset was due to the presence of certain clinical trials that recruited an extremely high number of participants (10 to 70 thousand). These trials studied very different diseases, took place in different locations, and were sponsored by different pharmaceutical companies. Therefore, considering the lack of commonalities between the outliers and the sufficient entries in the dataset, the values beyond the 99th quantile of the number of participants were removed, leaving 3,784 entries for analysis.

Below table summarizes the key figures before and after the removal of outliers:
![image](https://github.com/user-attachments/assets/3e22dc8f-570e-49a9-a814-a8f924be8e0b)

Subsequently, the dataset was split into training data and testing data in the ratio of 7:3 using MultilabelStratifiedShuffleSplit with 10 cross-validation folds. The purpose of splitting the dataset is to avoid the model from overfitting the training data such that it can generalize well to unseen data in the testing data. 

MultilabelStratifiedShuffleSplit was considered to be a better method than scikit-learn’s Train-Test-Split because the former ensures every label has the same proportion of observations within the categorical variables across the splits on imbalanced datasets.

To prevent data leakage from the training data into the testing data during the model learning phase, the testing data was scaled, imputed, normalized and encoded according to the distribution of the training data.

After feature engineering, a total of 62 columns (Features: 60, output labels: 2) and 3,784 entries remained in the dataset (training set: 2,649, testing set: 1,135).

### Model Training

27 algorithms were trained with respect to the 3 Multi Label Classification methods namely problem transformation, algorithm adaptation and ensemble method. 

Problem transformation method: Binary Relevance (BR), Label Powerset (LP) and Classifier Chain (CC)
Algorithm adaptation method: Multi-label k-nearest neighbour (MLkNN), Binary Relevance k-Nearest Neighbour (BRkNN)
Ensemble method: Random k-label Sets method (RAkEL) and Classifier Chain Majority Voting Classifier (MVC). 

The models used consist of Logistic Regression (LR), Support Vector Machine (SVM), Decision Tree (DT), Random Forest (RF) and Extreme Gradient Boosting (XGBoost). 

All models are optimized in the form of hyperparameter tuning using Grid Search to find their best scores. Below table summarizes the scores of Multi-Label classification algorithms

![image](https://github.com/user-attachments/assets/3023ba00-ed1b-4de1-a72b-a11bc02614ab).

The performances of algorithms were compared and evaluated against an evaluation matrix that consists of 11 example based- and label-based measures.Hamming Loss is selected as the main measure to evaluate the model’s predictive performance given it gives a fairer representation of the proportion of misclassification of individual labels in the dataset. The lower the Hamming Loss, the higher the predictive performance of the model. 

On the other hand, Macro-recall Score is selected as the score to be optimized because  to correctly identify more clinical trials with outcome measures out of the corresponding total in the dataset. 

To provide a high-level summary of how the algorithms performed, the performance of each was ranked based on its scores in the corresponding metric, and then the average rank was computed by the following formula.

𝐴𝑣𝑒𝑟𝑎𝑔𝑒 𝑅𝑎𝑛𝑘 𝑜𝑓 𝐴𝑙𝑔𝑜𝑟𝑖𝑡ℎ𝑚: = [(𝐻𝑎𝑚𝑚𝑖𝑛𝑔 𝐿𝑜𝑠𝑠 𝑅𝑎𝑛𝑘) 𝑥 2 + 𝐴𝑐𝑐𝑢𝑟𝑎𝑐𝑦 𝑆𝑐𝑜𝑟𝑒 𝑅𝑎𝑛𝑘 + 𝑀𝑎𝑐𝑟𝑜 𝑃𝑟𝑒𝑐𝑖𝑠𝑖𝑜𝑛 𝑆𝑐𝑜𝑟𝑒 𝑅𝑎𝑛𝑘 + 𝑀𝑎𝑐𝑟𝑜 𝑅𝑒𝑐𝑎𝑙𝑙 𝑆𝑐𝑜𝑟𝑒 𝑅𝑎𝑛𝑘 + 𝑀𝑎𝑐𝑟𝑜 𝐹1 𝑆𝑐𝑜𝑟𝑒 𝑅𝑎𝑛𝑘] / 6

For tied sets, the algorithms were assigned the average of their ranks. For example, if the Hamming Loss of BR-RF and BR-SVM are the same, their rank (x) would equal (x+x)/2. More weight (2x times) was assigned to Hamming Loss Rank because it was the most important evaluation criteria. 

![image](https://github.com/user-attachments/assets/f6b48e50-3d1e-45de-b1eb-46903296b174)

### Performance Evaluation

Based on the average rankings , the best performing model is MVC-RF, followed by BR-XGB and BRkNN. The confusion matrix of MVC-RF shows that the model
has correctly predicted 211/ (211+119) = 63.9% of clinical trials using questionnaires (majority class) but only 36/ (36+74) = 32.7% of clinical trials using patient diary (minority class) out of the respective totals in the dataset. A more balanced dataset would potentially improve the recall scores for both labels. 

To understand how useful the features were in making predictions in the best algorithm, the Permutation Feature Importance was computed for each feature in both the training and testing data. It is found that the 5 most important features by order are number of participants, study phase, disease type, study duration, and masking type. 

