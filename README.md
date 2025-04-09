# Multi-Label-Classification-Approach-to-predict-Clinical-Outcome-Measures

## Project Background and Objectives

This project explores using a Multi Label Classification Model (MLC) to investigate whether clinical trials with certain characteristics are more likely to adopt digital tools (e-Questionnaire and e-Patient Diary) to collect clinical outcome. More than 10 years of industry-sponsored interventional paediatric clinical trial records were scrapped from ClinicalTrials.gov database and studied. A total of 27 Multi-Label Classification algorithms were implemented, and their performances were evaluated against example-based and label-based metrics.

## Source of the dataset

The primary data used in this research is the clinical trial protocol information collected from [ClinicalTrials.gov,](https://clinicaltrials.gov/), a publicly accessible global registry maintained by the U.S. National Library of Medicine. The registry contains more than 420 thousand clinical trial records documented since Year 2000 and  offers a RESTful Application Programming Interface (API) to protocol information from computer programs. 

A Java Script was written to interact with the RESTful API and search for the clinical trials that match the following criteria:
• Funder Type: Industry-sponsored
• Study Type: Interventional and Observational Studies
• Start Date: Running from 1st January 2012 to 17th May 2022
• Participants: Children
• Overall Status: Not yet recruiting, Recruiting, Enrolling by Invitation, Active and not Recruiting, Completed

The API returned 7979 matches and they were converted into a DataFrame for further processing in Python language.

