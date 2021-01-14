# Somatus Data Analyst Challenge: Exploration of Inpatient Admissions for CKD and ESKD Members

## Purpose

The purpose of this challenge is for you to demonstrate your ability to conduct basic data summarization and analyses, and to frame and solve a problem using your skills as a Data Analyst.

**Your submission for this exercise will be evaluated on (1) responses to the data summary questions, and (2) your summary of the open-ended recommendation.** For the open-ended recommendation, we are interested in seeing how you think about the problem and communicate your results more than your ability to analyze the data.

## Task Details

### Summary

In this challenge, there are two parts:

1. **Data summarization:** basic data munging and analysis questions to test your skills in understanding and interpreting a new data set, work with and combine data sources, and summarize results

2. **Open-ended recommendation:** -- an open-ended question where you will develop recommendation about how to prioritize Chronic Kidney Disease (CKD) and End Stage Kidney Disease (ESKD) members for interventions to reduce inpatient admissions, and develop a 1-page executive summary to communicate your recommendation and any supporting data. 

### Data Summarization Questions

* How many total CKD and ESKD members are there in the data across all years?  How many members are there by kidney disease stage (e.g., CKD Stage 1, CKD Stage 2, CKD Stage 3, CKD Stage 4, CKD Stage 5, and ESKD)?
* How many admissions did CKD and ESKD members have in the data across all years, by kidney disease stage (e.g., CKD Stage 1, CKD Stage 2, CKD Stage 3, CKD Stage 4, CKD Stage 5, and ESKD)?
* What was the total paid amount for admissions for CKD and ESKD members across all years, by kidney disease stage (e.g., CKD Stage 1, CKD Stage 2, CKD Stage 3, CKD Stage 4, CKD Stage 5, and ESKD)
* What are the most common co-morbid chronic conditions for CKD and ESKD members? No need to break out by kidney disease stage.  Chronic conditions may be identified using the flags on the beneficiary summary file.

### Open-ended Recommendation Question

Imagine you are tasked with developing a strategy to reduce inpatient admissions among the CKD and ESKD population.  In developing an effective inpatient admission reduction strategy, one of the keys is determining how to prioritize patients for targeted interventions by care team members. A wide variety of factors may be used for determining prioritization, and your job will be to make a recommendation about what factors should be used to prioritize members.

Please create a 1-page (maximum) executive summary describing your approach to prioritizing CKD and ESKD members for interventions to reduce inpatient admissions and the "why" behind your recommendation. You may include supporting data and charts on up to 2 additional pages, however these are strictly optional.  The format of the 1-page executive summary may be whatever you choose -- PowerPoint, Markdown, Word, Excel, etc.

You are expected to use the included data to support your recommendation. You may also include additional subject area expertise or additional third-party research outside of the data to support your recommendation (e.g., literature, white papers, news articles, etc.) however you are not required to do so.

### Submission

Your submission for this challenge should include responses to the data summarization questions and the 1-page executive summary (and up to 2 additional, optional supporting pages) describing your recommendation for the open-ended question. You do not need to send back a modified copy of the underlying data set.

## Data

### Source

The datasets for this challenge are publicly available datasets from the Centers for Medicare and Medicaid Services and contain synthesized claims data for Medicare members.

*Source: https://www.cms.gov/Research-Statistics-Data-and-Systems/Downloadable-Public-Use-Files/SynPUFs/DE_Syn_PUF*

However, please use the datasets attached (no need to download the data from the source above).

### Data Model and Dictionaries

Attached you will find two files:

* **176541_DE1_0_2008_Beneficiary_Summary_File_Sample_1.csv**: contains data for Medicare insurance beneficiaries
* **176549_DE1_0_2008_to_2010_Inpatient_Claims_Sample_1.csv**: contains data for inpatient hospital claims submitted to Medicare for beneficiaries

These files can be joined together using the Beneficiary Code field ("DESYNPUF_ID").

For more detailed information on these files, including data dictionaries and other reference material, see pages 9 through 11 of Section 4 ("Summary of Variables of the CMS Linkable 2008–2010 Medicare DE-SynPUF") in the attached PDF document called "SynPUF_DUG."

You can also visit the link found in the "Source" section above for more reference material if needed.

### Identifying Chronic Kidney Disease (CKD) and End Stage Kidney Disease (ESKD) members

Each member may be categorized as a CKD or ESKD member based on the logic below. Members may be identified using a combination of ICD-9-CM diagnosis codes on inpatient claims (ICD9_DGNS_CD_1 – ICD9_DGNS_CD_10, or ADMTNG_ICD9_DGNS_CD) and the ESRD indicator on the beneficiary summary file (BENE_ESRD_IND).

The following ICD-9-CM diagnosis codes may be used to identify CKD and ESKD members (note you may need to remove the period in the diagnosis code when searching in the data):

End Stage Kidney Disease (ESKD):

* **585.6** End Stage Kidney Disease (ESKD)

Chronic Kidney Disease (CKD):

* **585.5** Chronic kidney disease, Stage 5
* **585.4** Chronic kidney disease, Stage 4
* **585.3** Chronic kidney disease, Stage 3
* **585.2** Chronic kidney disease, Stage 2
* **585.1** Chronic kidney disease, Stage 1
* **585.9** Chronic kidney disease, unspecified

Each member should only have a single disease categorization, which should be determined by the highest disease severity identified:
* ESKD > CKD Stage 5 > CKD Stage 4 > CKD Stage 3 > CKD Stage 2 > CKD Stage 1 > CKD Stage Unspecified

For purposes of this exercise, you do not need to take into account the date of the claim when identifying kidney disease stage.

*Source: http://www.icd9data.com/2014/Volume1/580-629/580-589/585/default.htm*
