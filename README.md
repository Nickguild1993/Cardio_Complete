# Machine Learning Cardiovascular Disease Analysis 


## Link to Google Slide Presentation 
https://docs.google.com/presentation/d/1p-YO3uYsGWfLahYIwny5GupWe3HAkLToKMBD_AEcl48/edit?usp=sharing Here is the link to the accompying slideshow complete with visualizations and excerpts from the analysis. 

## Purpose of Analysis:

- This project was undertaken in order to test the efficacy of machine learning (ML) models when it comes to predicting the outcome of cardiovascular disease based upon various aspects of patient data.  The (long term) goal of the work is to advocate for a progressive and proactive health care system that relies on machine learning models to help predict serious medical conditions before they fully develop.  Currently, the U.S. has a predominantly reactive medical system in which individuals only seek medical attention when their symptoms are troubling enough to warrant doing so.  

- Such a system is much less effective in terms of patient prognoses while also being exponentially more expensive than a proactive one.  In a proactive system, built on a machine learning models, patient data would be analyzed for possible indicators of latent illness (e.g., high systolic blood pressure in conjunction with a family history of cardiovascular disease) and that information would be compiled and relayed to the patient and their health care provider.  The hope being that the recognition of possible disease prevents it from ever fully manifesting itself as a financially costly and life-threatening condition.  Training machine learning models on predicative features is the first step in creating a health care system that results in better outcomes for the patient, less arduous work for the health care provider and greatly reduced financial burdens on the individual level as well as the macro level. 

## Analysis Overview:

- After downloading the dataset from Kaggle.com, the first step I undertook was cleaning the data.  There were quite a few instances of outliers in the continuous features that were likely the result of values simply being entered incorrectly (e.g., diastolic blood pressure value of -120).  To find the outliers and amend the dataset accordingly, I uploaded the CSV file into Pandas so that I could transform the table into a DataFrame and examine each feature column for dirty data.

- After ridding the DataFrame of erroneous outliers I transformed a few of the features so that the values were in an easier to read format.  One example of this was changing the “Age” feature to be displayed in years, instead of days.  This was done with the following code: ``` df = df.rename(columns= {“age” : “age_years”}) df[“age_years”] = (df[“age_years”]/365).astype(int) ```

- Additionally, I created a new feature column “BMI” (body mass index) which was derived from the values in the “height” and “weight” columns with the following code: ```cardio_df[“BMI”] = cardio_df[“weight”] / [cardio_df[“height”]/100 )**2 ```  The BMI column would end up becoming one of the most predictive of the 12 features analyzed.

- The two ML models that were utilized in this analysis were Support Vector Machine (SVM) and Random Forest.  They were chosen for their ability to accurately classify a binary outcome, or target, which is the presence (or absence) of cardiovascular disease (CVD) in this case.

## Conclusions:

- The SVM model turned out to be both more accurate (score of .723 compared to .702) and more sensitive (.78 compared to .71) than the Random Forest model. While neither of the models have the level of accuracy that you’d hope for, 72% isn’t terrible by any means.  Given that some of the features (“Alcohol Intake”, “Physical Activity” and “Smoking”) the model trained on were encoded as being binary (0=Doesn’t drink/exercise/smoke, 1= Does drink/exercise/smoke).  The issue is, that one person who has four drinks every night is recorded as having the same response as someone who only has a glass of wine twice a week when those values are actually very different from each other, and likely have ramifications for the outlook of one’s health.  So while there are some short comings in the analysis that could be improved upon with more in-depth data, perhaps utilizing bins, overall I believe this is an excellent start in exploring the possibilities of ML models in improving the health care system for everyone who has to interact with it.

