# Multi-Label-Classification-Approach-to-predict-Clinical-Outcome-Measures

## 1. Project Background and Objectives

Clinical trials are studies intended to evaluate the efficacy and safety of new medical treatments or interventions (such as vaccines, dietary supplements, drugs, devices, and lifestyle modifications) on humans. Clinical trials used to be only conducted in-person at designated sites such as hospitals. However during the outbreak of Covid-19 pandemic in 2021, the US Food and Drug Administration (FDA) issued guidelines on how Sponsors could run clinical trials when participants could not physically attend protocol-specified visits, with suggestions including running trials remotely over the internet and collecting clinical outcomes using digital tools. These suggestions opened doors for Sponsors and Contract Research Organizations to reassess their conventional approach of running clinical trials.

This project uses a Multi Label Classification Model to investigate whether clinical trials with certain characteristics are more likely to adopt digital tools such as e-Questionnaire and e-Patient Diary to collect clinical outcome from paedaetrics. The research questions are defined as follows:  

### Research Question 1. 
What are the trends and commonalities within Industry-sponsored Interventional Paediatric Clinical Trials?
### Research Question 2. 
How can Machine Learning be applied to predict the type of outcome measures used in clinical trials based on the trial characteristics?

More than 10 years of industry-sponsored interventional paediatric clinical trial records were retrieved from ClinicalTrials.gov database and studied. A total of 27 MLC algorithms were implemented, and their performances were evaluated against example-based and label-based metrics.


## Introduction of Multi-Label Classification Task 

In classic supervised learning tasks, the model only predicts one output variable based on the given set of inputs. This is referred to a Single-Label Classification task. In situations where there are several variables of interest, or one instance is associated with several mutually unexclusive outputs, it is referred to a Multi-Label Classification (MLC) task. The classifier function of MLC can be framed as X → YL, where X is the k-dimensional feature vector and Y is the target output vector with L number of possible labels. 

The most popular applications of MLC are Text Classification and Image Classification. For example, a comment on YouTube may consist of words that are ‘toxic’, ‘threatening’, and ‘insulting’, whilst an image can simultaneously be annotated as ‘mountain’, ‘sea’, and ‘bird’. MLC are also widely used in medical studies to predict patients’ symptoms and disease complications. Although single-label classification model can also handle these predictions, several studies have found out that MLC algorithms enhance the model’s predictive performance by leveraging on the correlations among labels.

There are three methods to train an MLC model, namely, Problem Transformation, Algorithm Adaptation and Ensemble Methods.
![image](https://github.com/user-attachments/assets/9e36b65d-167c-4c7d-bd1c-f2c32563340d)

The first method, Problem Transformation, addresses the MLC Task by converting the multi-label dataset into multiple single-label datasets, and then use binary or multi-class Machine Learning models to predict the output.

The second method, Algorithm Adaptation, trains the model to handle the multi-label problem directly without any form of data conversion. Certain adjustments in models are required to achieve this during the training process, such as changing the heuristics in Decision Trees and employing additional threshold techniques in Support Vector Machines (SVMs).

The third method, Ensemble Methods, combines the outcomes from either LP or CC to make predictions using ensemble-like techniques such as clustering. 



