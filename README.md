# Patient Selection for Diabetes Drug Clinical Trials Applying EHR data 
<div align="center">
  <img src="https://github.com/Ting-DS/EHR-Patient-Selection-for-Clinical-Trials/blob/main/EHR.jpg" width="50%">
</div>

## Background
EHR data (Electronic Health Records) is becoming a key source of real-world evidence (RWE) for the pharmaceutical industry and regulators to make decisions on clinical trials. In this project, I'm a data scientist for an exciting unicorn healthcare startup that has created a groundbreaking diabetes drug that is ready for clinical trial testing. It is a very unique and sensitive drug that requires administering the drug over at least 5-7 days of time in the hospital with frequent monitoring/testing and patient medication adherence training with a mobile application. We have been provided a patient dataset from a client partner and are tasked with building a predictive model that can identify which type of patients the company should focus their efforts testing this drug on. Target patients are people that are likely to be in the hospital for this duration of time and will not incur significant additional costs for administering this drug to the patient and monitoring.

In order to achieve our goal, we build a Expected Hospitalization Time Regression Model: Utilizing a synthetic dataset(denormalized at the line level augmentation) built off of the UCI Diabetes readmission dataset, students will build a regression model that predicts the expected days of hospitalization time and then convert this to a binary prediction of whether to include or exclude that patient from the clinical trial. This project will demonstrate the importance of building the right data representation at the encounter level, with appropriate filtering and preprocessing/feature engineering of key medical code sets. This project will also analyze and interpret the model for biases across key demographic groups.

## Data Source

Due to healthcare PHI regulations (HIPAA, HITECH), there are limited number of publicly available datasets and some datasets require training and approval. So, we are using a dataset from UC Irvine that has been modified for this project. The dataset represents ten years (1999-2008) of clinical care at 130 US hospitals and integrated delivery networks. Please note that it is limited in its representation of some key features such as diagnosis codes which are usually an unordered list in 835s/837s (the HL7 standard interchange formats used for claims and remits).

 - Data source description can be found [here](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)

 - Data Schema can be found [here](https://github.com/udacity/nd320-c1-emr-data-starter/tree/master/project/data_schema_references). There are two CSVs that provide more details on the fields and some of the mapped values.

## Analysis & Methods
 - Use the Tensorflow Dataset API to scalably extract, transform, and load datasets and build datasets aggregated at the line, encounter, and patient data levels(longitudinal)
 - Analyze EHR datasets to check for common issues (data leakage, statistical properties, missing values, high cardinality) by performing exploratory data analysis.
 - Create categorical features from Key Industry Code Sets (ICD, CPT, NDC) and reduce dimensionality for high cardinality features by using embeddings
 - Create derived features(bucketing, cross-features, embeddings) utilizing Tensorflow feature columns on both continuous and categorical input features
 - Use the Tensorflow Probability library to train a build Deep Learning Regression Model with Sequential API and TF Probability Layers that provides uncertainty range predictions that allow for risk adjustment/prioritization and triaging of predictions
 - Analyze and determine biases for a model for key demographic groups by evaluating performance metrics across groups by using the Aequitas framework



