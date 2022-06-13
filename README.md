# A MAchine Learning Approach to Prediction of Parkinson’s Disease Using Voice Analysis

# Parkinson’s Disease
Parkinson’s Disease (PD) is a degenerative neurological disorder marked by decreased dopamine levels in the brain. It manifests itself through a deterioration of movement, including the presence of tremors and stiffness. There is commonly a marked effect on speech, including dysarthria (difficulty articulating sounds), hypophonia (lowered volume), and monotone (reduced pitch range). Additionally, cognitive impairments and changes in mood can occur, and risk of dementia is increased.

Traditional diagnosis of Parkinson’s Disease involves a clinician taking a neurological history of the patient and observing motor skills in various situations. Since there is no definitive laboratory test to diagnose PD, diagnosis is often difficult, particularly in the early stages when motor effects are not yet severe. Monitoring progression of the disease over time requires repeated clinic visits by the patient. An effective screening process, particularly one that doesn’t require a clinic visit, would be beneficial. Since PD patients exhibit characteristic vocal features, voice recordings are a useful and non-invasive tool for diagnosis. 
* Source: 'Exploiting Nonlinear Recurrence and Fractal Scaling Properties for Voice Disorder Detection'),Little MA, McSharry PE, Roberts SJ, Costello DAE, Moroz IM.
BioMedical Engineering OnLine 2007, 6:23 (26 June 2007)
> 
# Project Objectives.
This project aims at utilizing machine learning algorithms to detect the presence of the early stage of Parkinson's disease using voice recordings of healthy people and people suffering from parkinson's disease.

# Dataset
The dataset was acquired from kaggle, though it originated from [here](https://archive.ics.uci.edu/ml/machine-learning-databases/parkinsons/), The dataset consists of 195 rows, and 24 columns.The rows represent 195 observations, and the columns represent 23 features and 1 target variable.

Feature	

|Features|Description|
|--------|-----------|
|MDVP:FO(HZ)|Average vocal fundamental frequency|
|MDVP:FHI(HZ)|Maximum vocal fundamental frequency|
|MDVP:FLO(HZ)|Minimum vocal fundamental frequency|
|MDVP:JITTER(%), MDVP:JITTER(ABS),MDVP:RAP,MDVP:PPQ, JITTER:DDP|Several variations in fundamental frequency|
|MDVP:SHIMMER, MDVP:SHIMMER(DB), SHIMMER:APQ3 , SHIMMER:APQ5, MDVP:APQ, SHIMMER:DDA|Several measures of variation in amplitude|
|NHR, HNR|Two measures of ratio of noise to tonal components in the voice|
|STATUS|Health status of the subject (one) - Parkinson's, (zero) - healthy|
|RPDE, D2|Two nonlinear dynamical complexity measures|
|DFA|Signal fractal scaling exponent|
|SPREAD1, SPREAD2, PPE| Three nonlinear measures of fundamental frequency variation|

# Distribution of features
The distribution of these features varies between individuals with the disease and those without the disease. The orange bars in the barcharts below represents individuals with the disease and the blue bars represents individuals without the disease. There is a clear differnce in the level of voice features in the two groups. This difference is what will be used in the classification of individuals into PD positive and PD negetive status.

![bar1](https://user-images.githubusercontent.com/95732821/173400202-d8b17865-07d5-4d14-9838-eda73296fa32.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**MDVP:fo(HZ):**|lower| higher|             
|**MDVP:fhi(HZ)**|lower| higher|
|**MDVP:Flo(HZ):**|lower|higher|             
|**MDVP:Jitter(%)**|higher|lower|

![bar2](https://user-images.githubusercontent.com/95732821/173400234-b068e169-bac9-4c77-876d-9830194d1fd5.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**MDVP:jitter(Abs)**|higher|lower|             
|**MDVP:RAP**|higher|lower|
|**MDVP:PPQ**|higher|lower|             
|**Jitter:DDP**|higher|lower|

![bar3](https://user-images.githubusercontent.com/95732821/173400270-64788360-bf61-4b72-b450-6b23d2f1c34f.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**MDVP:Shimmer**|higher|lower|             
|**MDVP:Shimmer(dB)**|higher|lower|
|**Shimmer:APQ3**|higher|lower|             
|**Shimmer:APQ5**|higher|lower|

![bar4](https://user-images.githubusercontent.com/95732821/173400306-e3f7d7cc-6a16-45e2-8b40-0f102f324bee.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**MDVP:APQ**|higher|lower|             
|**Shimmer:DDA**|higher|lower|
|**NHR:**|higher|lower|             
|**HNR:**|lower|higher|

![bar5](https://user-images.githubusercontent.com/95732821/173400332-90825d9f-358b-4a66-93c2-1a93fc137076.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**RPDE:**|higher |lower|
|**DFA:**|higher|lower|
|**Spread1:**|higher |lower|             
|**Spread2:**|higher|lower|

![bar6](https://user-images.githubusercontent.com/95732821/173400358-95c32ef6-0d0e-45ed-b812-6247c17fa4fe.png)
|Features|Level in PD POSITIVE| Level in PD NEGATIVE
|--------|-----------|------------|
|**D2:**|higher|lower|             
|**PPE:**|higher|lower|



# Model Evaluation

**Error Types**

In every binary classification problem, there is always a 'positive' class and a 'negative' class. The positive class should be the one you are most interested in finding , it is usually the group of interest. For this Parkinson's disease dataset, the positive class will be the presence of Parkinson's disease and the negative class will be the absence of parkinson's disease.

>-**Type 1 error:** If our model predicts the presence of Parkinson's disease, when there is' no disease present, it will have made a type 1 error. This is also known as a false positive.

>-**Type 2 error:** If our model predicts that there is an absence of Parkinson's disease, when the disease is present, it will have made a type 2 error. This is is also known as a false negative.


## Evaluation Metrics

### Accuracy
![image](https://user-images.githubusercontent.com/95732821/169638957-d64f1e1e-a398-422a-bfe5-afa358dab1af.png)

This is the metric to use when:

>The cost of False Positive and False Negative are roughly equal

>The benefit of a True Positive and a True Negative are roughly equal

### Recall
![image](https://user-images.githubusercontent.com/95732821/169638957-d64f1e1e-a398-422a-bfe5-afa358dab1af.png)

Using sensitivity and specificity aims to keep the number of False Negative and False Positive respectively as low as possible since we might want to increase the model sensitivity. Recall is the metric to use when:

>The cost of False Negative is much higher than a False Positive

>The cost of a True Negative is much higher than a True Positive

### Precision
![image](https://user-images.githubusercontent.com/95732821/169639653-692b2103-c435-49a9-92b6-d34099f28a9b.png)

This is the metric to use when:

>The cost of a False Positive is much higher than a False Negative

>The Benefit of a True Positive is much higher than a True Negative

## Chosen Evaluation Metric
When it comes to predicting diseases, the false negative error can be griveously costly, It is better to predict the presence of a disease falsely than to predict the absence of a disease falsely. It is always better to have a model that has zero amount of false positive error than the false negative error.
This project aims at training a model to identify if a patient has a parkinson's disease or not, a False Negative might might delay the treatment of the patient, which might even lead to death, because a quick identification of a disease could help for a better treatment. On the other hand, a False Positive may only lead to additional tests which might be financially costly but not as costly as the life of a human being. That being said, the chosen evaluation metric will be the **recall score.**, which focuses on the type 2 error. It emphasizes on the false negative error, which is the center of attention in evaluating the performance of our models.

# Models
A data classification was performed on the data set using KNN,LGBM and XGB classification models. All three models were tuned and evaluated and the performance are being displayed in the maps below.

# Confusion map displaying the prediction performance of the model 
![knnn_image](https://user-images.githubusercontent.com/95732821/173371838-cfb5ef9e-151b-4b03-8136-56c39042453e.png)

 The KNN model made no errors on the training set but it had a 0% false negative error and a 33% false positive error on the testing set.
![lgbm_image](https://user-images.githubusercontent.com/95732821/173372159-72e3d42b-584e-4aab-a70c-02a8b4eb441a.png)

The LGBM model made all predictions accurately on the training set, but it made about 3% false negative error on the testing set.
![xgb_image](https://user-images.githubusercontent.com/95732821/173372244-a44f95eb-fac2-406f-ae01-2d9a05100cef.png)

The XGB model made all predictions accurately on the training set. As for the testing set, the model also made about 3% false negative errors on the testing set.

# Results
![image](https://user-images.githubusercontent.com/95732821/173372728-07cb0b19-23ee-4477-bb2d-32cac76359d6.png)

All three models performed well on the training set. As for the testing set,the KNN model performed the best with a recall score of 1, it made no false negative error, which would have been very costly. The LGBM and XGB model had same recall score of 0.97

# Conclusion
Three models, KNN, LGBM,and XGB, were built and tunned for the detection of early stage parkinson's disease, out of these models, the KNN model is the most suitable model with a high recall score of 1.
# Recommendations
The primary rationales for early detection and initiation of treatment in patients with PD include slowing disease progression, delaying and diminishing symptoms (both motor and nonmotor), limiting deterioration of patient quality of life (QoL), and achieving long-term cost savings.The KNN model, with its tunned parameters can be used to accurately predict the early stage of Parkinson's disease in individuals, using the voice analysis. 

